---
title: "KDE problems"
date: 2005-11-16
forum: Desktop Environments
---

### Post by PenguinZdravko on 2005-11-16
Hi! I have installed kubuntu-desktop on my Ubuntu machine. Here are my 2 questions:
1. When I log in in my account, the sound is OK. But when I created an account for my sister, I don't have any sound. When I start a session with her user it tells me:
Sound server informational message:
Error while initializing the sound driver:
device /dev/dsp can't be opened (Permission denied)
The sound server will continue, using the null output device.
2. My sister want to use GAIM. I change the font size from System Settings to 14, and she is happy that can read the messages. But when I start Firefox the font is too big. How can I set different font size for each GTK app?
Edit: Problem 1 fixed, problem 2 lefts.

---

### Post by mlomker on 2005-11-17
[QUOTE=PenguinZdravko]device /dev/dsp can't be opened (Permission denied)
The sound server will continue, using the null output device.[/quote]

You need to add her to the **audio** group.  Your default user gets put in these groups:

```

mlomker@mlomkernote:/$ cat /etc/group | grep mlomker
adm:x:4:mlomker
dialout:x:20:mlomker,cupsys
cdrom:x:24:mlomker,hal
floppy:x:25:mlomker,hal
audio:x:29:mlomker
dip:x:30:mlomker
video:x:44:mlomker
plugdev:x:46:mlomker,hal
mlomker:x:1000:
lpadmin:x:104:mlomker
scanner:x:105:mlomker
admin:x:106:mlomker

```

> Edit: Problem 1 fixed, problem 2 lefts.

Figures!  That's the one that I didn't know.  I use gaim 2.0 and there isn't even a font adjustment in this particular build.  You're adjusting the Firefox font in Edit, Preferences?

---

### Post by incubus on 2005-11-17
Which font is too big in firefox: the text you browse or the menu's? Have you tried to tweak the "display resolution" there (preferences)?

---

### Post by PenguinZdravko on 2005-11-19
[QUOTE=incubus]Which font is too big in firefox: the text you browse or the menu's? Have you tried to tweak the "display resolution" there (preferences)?[/QUOTE]
The menus.

---

### Post by not_cool on 2005-11-19
Try changing the KDE theme. Some of the themes have smaller menus. Or try to change the font size in kcontrol. (Under Appearance and Themes -> Fonts)

---

### Post by kmashraf on 2006-04-29
Well I too ran into the same problem. Checked the permissions of /dev/dsp and found it belonged to the 'audio' group ....... and essentially figured the suggested fix. 
But hey why isn't this automated. When a new user is created how come he/she ain't automatically added to the 'audio' group so their sound server instance starts up on log on. Other distro's don't seem to have this problem ? Seems kinda dumb to me, having to add the user to the 'audio' group manually.

---

