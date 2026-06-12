---
title: "Ubuntu (Jaunty) sound configuration"
date: 2009-06-15
forum: General Help
---

### Post by schizomasochizt on 2009-06-15
How to configure sound in Ubuntu (Jaunty Jackalope)

It depends on how you will use it. If you have updated your system then 
I believe this would pretty much do it.

If you want to play music or video from your own personal files

1.) Check your audio device i.e. Realtek Audio, Alsa, etc.
2.) Go to "System > Preferences" and then click "Sound". 
    a dialog box will appear named "Sound Preferences".
3.) On the "Devices" tab, there are four categories namely
    "Sound Events", "Music and Movies", "Audio Conferencing"
    and "Default Mixer Tracks".
4.) Choose between which audio device are you using, look for 
    the name of your audio device which has a "(OSS)" name
    attached to it. (for sound capture choose the one with
    "ALSA" attached along with your audio device name.
5.) After that click "Close"

Try playing your favorite music file.
hope this helps. :P

If you want to use your headset to call someone using sip phones or 
simply thru yahoo messenger or skype.

1.) Right click on the speaker icon beside the date and click
    "Open Volume Control". A dialog box named "Volume Control: (audio device name)"
2.) Select the audio device that you are using. Choose the one with "(Alsa mixer)"
    attached to your audio device name. Configure your desired settings.
3.) Click "Close"
4.) Right click again on the speaker icon, this time select "Preferences"
5.) Select the same audio device name and click "Close".

...Now if you still can't hear anything when you are inside your application i.e. 
    Yahoo Messenger, or Skpe, simply select the name of your audio device name
    on the "Configurations" > "Audio" or "Sound", the name may vary thru different
    applications but the idea is still the same.

---

