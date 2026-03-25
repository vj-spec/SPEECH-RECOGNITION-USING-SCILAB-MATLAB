# EXP 5 : SPEECH RECOGNITION USING SCILAB

## AIM: 

To perform and verify speech recognition using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM : 

# ================================
# INSTALL REQUIREMENTS
# ================================
!pip -q install SpeechRecognition pydub
!apt-get -qq install ffmpeg

# ================================
# IMPORT LIBRARIES
# ================================
import speech_recognition as sr
from google.colab import files
from pydub import AudioSegment

# ================================
# UPLOAD AUDIO FILE
# ================================
print("📁 Upload audio file (MP3 or WAV)")
uploaded = files.upload()

audio_file = list(uploaded.keys())[0]

# ================================
# CONVERT TO WAV (IF MP3)
# ================================
if audio_file.endswith(".mp3"):
    print("🔄 Converting MP3 to WAV...")
    sound = AudioSegment.from_mp3(audio_file)
    audio_file = "converted.wav"
    sound.export(audio_file, format="wav")

# ================================
# SPEECH TO TEXT
# ================================
recognizer = sr.Recognizer()

with sr.AudioFile(audio_file) as source:
    audio_data = recognizer.record(source)

# ================================
# CONVERT AUDIO TO TEXT
# ================================
try:
    text = recognizer.recognize_google(audio_data)
    print("\n🎯 Converted Text:\n", text)

except sr.UnknownValueError:
    print("\n❌ Could not understand audio")

except sr.RequestError:
    print("\n❌ API error (Check internet)")

## OUTPUT:

<img width="1599" height="690" alt="image" src="https://github.com/user-attachments/assets/ceaf3ba1-5301-44cc-ad0c-0ae2279fae8a" />

## RESULT: 
Thus the speech recognition using SCILAB was performed and verified.
