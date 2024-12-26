from moviepy.editor import *
from PIL import Image, ImageDraw, ImageFont

# Create a function to generate love message slides
def create_love_slide(text, duration=3, bg_color=(255, 182, 193)):
    # Create a blank image (using Pillow)
    img = Image.new('RGB', (1920, 1080), color=bg_color)
    draw = ImageDraw.Draw(img)
    
    # Load a font (you can use any TTF font available on your system)
    font = ImageFont.truetype("arial.ttf", 100)
    
    # Get the size of the text to center it
    text_width, text_height = draw.textsize(text, font)
    
    # Position the text in the center
    position = ((1920 - text_width) // 2, (1080 - text_height) // 2)
    
    # Add the text to the image
    draw.text(position, text, fill=(255, 0, 0), font=font)
    
    # Convert the image to a format MoviePy can use
    img.save("temp_image.png")
    
    # Create a video clip from the image (using MoviePy)
    clip = ImageClip("temp_image.png", duration=duration)
    
    return clip

# Create a love message video with multiple slides
love_messages = [
    "You are my sunshine.",
    "I love you to the moon and back.",
    "Every moment with you is magical.",
    "Forever and always, my love."
]

# Create a list of clips from each love message
clips = [create_love_slide(message) for message in love_messages]

# Combine all clips into one video
final_video = concatenate_videoclips(clips, method="compose")

# Add background music (optional)
audio = AudioFileClip("love_song.mp3").subclip(0, final_video.duration)
final_video = final_video.set_audio(audio)

# Write the final video to a file
final_video.write_videofile("love_message_video.mp4", fps=24)

      







<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Love Letter</title>
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #ffe4e1;
            color: #ff1493;
            text-align: center;
            padding: 50px;
        }
        h1 {
            font-size: 48px;
        }
        p {
            font-size: 24px;
        }
        .love-heart {
            font-size: 72px;
            color: red;
        }
    </style>
</head>
<body>
    <h1>To My Dearest Love</h1>
    <p>Every moment with you is a treasure.</p>
    <p>You are my one and only. <span class="love-heart">❤️</span></p>
    <p>I will always love you.</p>
</body>
</html>
