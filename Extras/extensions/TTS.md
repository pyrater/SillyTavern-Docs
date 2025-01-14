# TTS

SillyTavern has a wide range of TTS options. This page explains the setup and use.

### What is it?

TTS is used to have a voice narrate parts of your chat.

### Configuring TTS

#### TTS Provider Selectbox

Used to select which TTS service you want to use.

- **ElevenLabs** - paid subscription required, highest quality voices available at present.
- **Silero** - free, runs on your PC, quality can vary widely
- **System** - uses your OS TTS engine, if one exists. Quality can vary widely depending on the OS.
- **Edge** - free, runs via Azure, generally quite fast, and voices feel natural but dry and emotionless. Like listening to the evening news or a radio announcer.
- **Coqui-TTS** - free, No API Implemation at this time. High-performance Text2Speech models (Tacotron, Tacotron2, Glow-TTS, SpeedySpeech) as well as Bark.
- **Novel** - requires a paid NovelAI subscription, generated by NovelAI's TTS engine

#### Checkboxes

- **Enabled** - turns TTS playback on/off
- **Auto Generation** - lets TTS start playing automatically when a new message enters chat
- **Only narrate "quotes"** - Limits TTS playback to only include text within `"quotation marks"`. This will `*include "quotes" within asterisk lines*` (internal variable name = `narrate_quoted_only`)
- **Ignore \*text, even "quotes", inside asterisks\*** - TTS will not play any text within `*asterisks*`, even "quotes" (internal variable name = `narrate_dialogues_only`)
- *having both "only narrate quotes" and "ignore asterisks" checkboxes both checked will result in the TTS only reading "quotes" which are not in asterisks, and ignoring everything else.*
- **Narrate only the translated text** - this will make the TTS only narrate the translated text.

![Logic Chart for Narration Filters](https://files.catbox.moe/2y48qr.png)

#### Voice Map

You must provide a voicemap for the TTS to use, otherwise it won't know what voices should be used for each character.

These must be in this exact format stated below:

`CharacterName:TTSVoice,CharacterName2:TTSVoice2`

For Coqui-TTS the format needs to include speaker and langage from the webgui:

`CharacterName:TTSVoice[speakerid][langid]`
 or
`Aqua:tts_models--multilingual--multi-dataset--your_tts\model_file.pth[2][1]`

#### Bark ZeroShot Voice Cloning Speakers

If using Bark you must create a voice folder with a voice file to clone. Ensure you add voices to homedir\tts\bark_v0\speakers\. On windows it is probably C:\Users\USERACCOUNT\AppData\Local\tts\bark_v0\speakers\ type %appdata% in windows explorer then go UP a directory to local and you should see tts.

The directory should look like this:
+ homedir
  + tts
    + bark_v0
      + speakers
        + customvoice1
          - speaker.wav 
          - speaker.npz        
        + robinwilliams
          - speaker.mp3
        + me
          - speaker.mp3

One first load of this model and voice bark will clone the voice and create a .npz file, this is needed for faster TTS.

#### Sliders

These will change depending on the API you select.

(explanation coming soon)

#### Buttons

- **Apply** - this must be clicked after setting an TSS API and after editing the voicemap.
- **Available voices** - loads a popup with all voices available for your selected API, and lets you preview them with sample dialogues.

### Using TTS

1. click the "enable" checkbox, or nothing will ever happen.
2. click the "auto generation" checkbox if you want the TTS to start automatically eveytime a new message arrive in chat.
3. optionally, click the megaphone icon inside the top-right of any message to playback on demand.
4. click the lower right "Stop" button (found unsde the wand menu) to stop any playback.
