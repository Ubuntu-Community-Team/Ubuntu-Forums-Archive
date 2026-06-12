---
title: "External mic? Please help!"
date: 2009-06-04
forum: General Help
---

### Post by s.mulleady1122 on 2009-06-04
Hey everyone,
I'm a musician and quite often find myself in need of recording quick demos of songs for projects of mine.
Since I switched to Ubuntu, I have been having a lot of trouble! The programs are great - Ardour in particular, but much to my dismay I can't get my external mic to work for the LIFE of me!

Originally I had it in the front mic jack of my PC - I was getting playback but couldn't set it to record. My friend advised me to try the line-in jack in the back and still, I could hear playback but could not record. Even in Audacity, a very simple program, I can't set the recording input as line-in!

Any suggestions would be greatly appreciated! :D

---

### Post by s.mulleady1122 on 2009-06-04
Bump, I'd love some help, this is driving me nuts lol

---

### Post by Megrimn on 2009-06-04
In System> Preferences> Sounds, make sure all the devices are set to ALSA.  That's everything that has a drop-down menu.  At this point, if you had to change anything, you will have to restart the computer.

Then check in the sound preferences of your preferred program that the recording device or driver is set to ALSA.  I had to do this for audacity, since for some reason it wasn't set automatically.  you may have to restart the program for any changes to take effect.

Hope this helps.

P.S. You are only allowed to bump after 24 hours, just letting you know. :)

---

### Post by Villiam on 2009-06-04
I think you are using the sound card jacks which are builtin your motherboard. Right. Does your mic (or line-in) works well with other software or is it just Audacity. I am assuming that its not your sound card input/settings that are the issue here. With Audacity you may try not running any other software, as sometimes Audacity behaves very weird :) 
I have found this description on another thread. May be it will help you:
Open the alsa mixer (double click on the speaker icon in the taskbar). Go to the File->Change Device menu.
Make sure that your soundcard (working under Alsa) is selected. Use the Edit->Preferences menu to make
sure that all the mic recording and mic boost controls are present etc.
Open Audacity, go to the Edit->Preferences-AudioIO menu and make sure that Alsa is selected.
Don't run Firefox while you are recording since it tends to grab exclusive access to the audio.

[ubuntu]("http://www.linux-archive.org/ubuntu-user/")

---

### Post by s.mulleady1122 on 2009-06-04
Thanks for the help, I'll try these!

---

### Post by s.mulleady1122 on 2009-06-04
Okay, so I'm not sure what the problem is. In the drop-down menu in Audacity, ALSA isn't even an option. Ardour - Well, I don't even KNOW what's going on with Ardour.

---

### Post by Megrimn on 2009-06-05
In Edit>Preferences>Audio I/O in Audacity, under "recording", is there a device that says (hw:0,0) somewhere in the title?  cause that should be the one selected...

---

