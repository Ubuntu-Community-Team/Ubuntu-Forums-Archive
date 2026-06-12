---
title: "No Sound"
date: 2006-04-02
forum: Desktop Environments
---

### Post by Motumbo on 2006-04-02
I just installed Ubuntu for the first time, and I do not get any sound ... I installed mplayer, but I still get no sound.

I have never had sound.

What do I do?

---

### Post by halitech on 2006-04-02
not sure if this will help any but you could check the info here and see

[http://ubuntuforums.org/showthread.php?t=154340&highlight=sound]("http://ubuntuforums.org/showthread.php?t=154340&highlight=sound")

---

### Post by Motumbo on 2006-04-02
this does me no good.

I have not had sound from the start.

---

### Post by kelean on 2006-04-02
Have you looked in your /etc/modules file to see if your soundcard is listed or the module.  When i install ubuntu i have to do this on my p-III 450 dell GX-1 computer.

---

### Post by Motumbo on 2006-04-02
the things listed are 

lp
mousedev
psmouse

nothing there about sound.

I have a soundblaster card in my computer.

Can anything be done?

---

### Post by kelean on 2006-04-09
sorry about the long time to answer but yes there is.  You need to put the module into that file, I put it at the end.   Im not sure what the module name is for soundblaster may be someone could help with that.

---

### Post by louis_nichols on 2006-04-09
well... I would start with the GUI stuff, to keep things simple and in line with the trends (see windoze and stuff :p)

go to system/preferences/sound and see if you have anything listed under "default sound card". Then go to system/preferences/ multimedia systems selector and choose alsa both for source and for sink. Next see that all your apps are configured to use alsa for output (I've had a sound issue issue for a long time with mplayer, and was so sick of it that I don't use it to this day).

Another thing to check is under system/administration/users and groups. Select your user, click properties and go to "user privileges". there you have to see that "use audio devices" is checked.

I have nothing written in /etc/modules, but sound works just fine...

---

### Post by kelean on 2006-04-09
well until i added the sound mod to my /etc/modules file my system would always put up an error messang that the device not found.  I had tried severan things like tring to reinstall alsa drivers and alsa its self.  I tried a few of the howto's with nothing working at all.  I only ran across  across adding the snd-cs4236b line to the /etc/moudles file by accident.  It seems that when i installed ubuntu, debian, mepis, and a few others my sound card is not detected.  So i have to add the mod by hand when ever i do a fresh install.

Besides it is a very simple thind to look for in older computers.

---

