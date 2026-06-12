---
title: "No Audio on websites?"
date: 2008-02-13
forum: Desktop Environments
---

### Post by KIeranG on 2008-02-13
Hello,

I'm having problems with audio from within FireFox. No sound will play through any Flash files... For example, no sound on YouTube videos...

This is weird because MP3 files and other files outside of the browser (aka non flash) work absolutely fine. I've google'd and found people with similar problems but the posts are all from 1-2 years ago - I've done what they did to fix it to no avail. 

Has anyone got any suggestions on how I can make sound work with Flash? I'm on the latest Ubuntu version...

PS. I'm very new to Ubuntu so explain as fully as you can! :)

Thanks,
Kieran.

Edit: Ok, second problem... Occasionally when I'm typing and I use caps lock, the letter after I press caps lock to turn it off (so it should be lower case) turns upper case... very strange, it doesn't do this in Windows... it's doing it as I type this now, I have to keep going back and changing it to lowercase >_<

---

### Post by mister_p_1998 on 2008-02-13
I keep getting this error, try re-installing the flash-plugin, and also disable your system sounds.
Steve

---

### Post by KIeranG on 2008-02-13
I have tried reinstalling and disabling system sounds, to no avail... I'm more than likely going to switch back to Windows tomorrow...

---

### Post by KIeranG on 2008-02-14
Bump, can anyone help me?

I really want to use Ubuntu but I can't with no sound :(

---

### Post by KIeranG on 2008-02-14
I just found out I have no sound in Amarok either....

It may have something to do with me having to change my sound devices in sound options to 'USB' because 'auto detect' wasn't working...

Is there some kind of USB driver I can download?

I have a cheap usb soundcard (needed it so I could use optical out...)

---

### Post by Chibi on 2008-02-14
Sounds like you have a low end soundcard. Here's what is happening, and what you can do as a temporary solution.

Sound compatibility in windows is a given, the mechanisms for handling most things are included in the software drivers which route extra audio tasks and mixing to your processor. On linux, the software mixing is handled seperate from the drivers, in a program like JACK, ESD, PulseAudio, or the like running in the background, which is generally a fine thing, however, on the other hand, linux has two backends for audio that conflict with eachother ALSA and OSS. Modern systems and programs perfer ALSA, and ALSA plays friendly with the sound server (ESD if you are using gnome) However, in this case, OSS will generally get blocked out if your sound card only has 1 channel. There is no easy way to completely solve this issue, because Flash uses OSS.

What you need to do before you start your browser is make sure no audio is playing and then hit Alt+F2, run the command "killall esd" in the prompt, and start your browser and a flash application before you do anything that will restart esd. (play a music file, sound file, popup noise etc). If your soundcard has enough channels, it might be feasible to entirely disabled esd in your sound configuration. If you decide to do this, try playing two things with sound at once, for example, a flash application and a music file, if one doesn't play, or it starts to sound crackley, you will end up needing to run a sound server in the end.

Hope this helps. :3

---

### Post by KIeranG on 2008-02-14
Thank you for the lengthy reply Chibi :)

I'm affraid killall esd did absolutely nothing, sound still wont work in flash even with going directly to a flash file after doing it...

I just went into sound options, clicked OSS and clicked test and I get an error

> 
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.


Any ideas?

---

### Post by KIeranG on 2008-02-14
I managed to get Amarok working by disabling my onboard sound, but still no luck with FireFox. I really want to get this working... any help? could the error above be the cause of this?

---

### Post by KIeranG on 2008-02-15
I'm bumping this... come on... give me some help... really want to use ubuntu

---

