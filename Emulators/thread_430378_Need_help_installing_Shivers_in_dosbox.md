---
title: "Need help installing Shivers in dosbox"
date: 2007-05-02
forum: Emulators
---

### Post by fakie_flip on 2007-05-02
Hello, I am trying to install Shivers in Dosbox. Yes, I have tried Wine and Cedega several times, but I'd prefer to use dosbox anyways. I was told by many that they prefer to use dosbox instead of dosemu. I don't know what the difference is, but I am taking their advice and using dosbox. So far what I have done is mount the the game in dosbox using this command.

```
Z:\>mount d /media/cdrom -t cdrom -usecd 0 -ioctl
```

That command came from an example I found by typing intro cdrom in dosbox. The example command I found did not work, but it did after I changed D:\ to /media/cdrom. This game is supposed to install in both windows95/3.1 and msdos, but the instructions for both are not the same. For Win95, the game is supposed to be installed by running the SETUP.EXE, but in dos, it is not, and I am not sure what the instructions are for dos. I have looked for the instructions, but did not find them. I found something about making a boot floppy for dos instead. After I did that above command in dosbox, I switched to the mounted cdrom drive by typing D: and then typed dir to see the game files. Running SETUP.EXE does not work because that file is for installing in Win95/3.1, so how do I install in dosbox? Running SETUP.EXE gives me the message "This program requires Microsoft Windows." in dosbox.

---

### Post by cogadh on 2007-05-03
First off, let me say... Shivers!? Holy cow, I thought I was the only person who bought that game! It was awesome!

Secondly, I just pulled out my old Shivers manual to check the install instructions and it lists Windows 3.1 as a minimum requirement. I don't think this game could actually be run in DOS directly. The only install instructions that were included are for Win 3.1 and 95 and they both use the setup.exe file to install the game. The setup.exe file is not a DOS executable, so I don't think you will be able to install or play it using DOSBOX, you will need to use Wine.

EDIT - Just installed it on my system through Wine. It will install, just don't run the system tests first (it will crash) and make sure Wine is configured for Win 3.1, 95 or 98 emulation first. It won't install if you use any flavor of NT emulation (NT, 2000 or XP).

---

### Post by go_beep_yourself on 2008-11-24
I was able to get Shivers working. It works fine even though I kept getting errors while installing it. The only thing that doesn't work is full screen. The game won't go into full screen. Does anybody else have this problem or found a way to get the game to go into full screen? BTW, Shivers works with the wine in the Ubuntu repos but when I tried it with the repo from winehq.com, it didn't work, so I reverted back to using the wine in the Ubuntu repos.

PS. Windows 3.1 is DOS and the exe file isnt for Windows 3.1

---

### Post by itchy8me on 2008-11-24
hey fakie,

how about telling us how you got legends workin on the 64bit?

thanks,
wernher

---

### Post by go_beep_yourself on 2008-11-25
Looks like fakie is banned. Why don't you try adding him to messenger?

---

### Post by itchy8me on 2008-11-27
probably because he wouldn't accept me :-p

---

### Post by go_beep_yourself on 2008-11-27
> **itchy8me said:**
> probably because he wouldn't accept me :-p

No, I mean pidgin messenger. He's got screen names for everything.

---

### Post by CodyContagious on 2012-03-06
Hey guys i seen my parents play shivers when i was a lad and they couldnt beat it and i remembered this game but couldnt think of the name of it neither could my parents and now i have it downloaded i got the iso image but i cant install it ive tried dosbox but still nothing i am on windows 7 64 bit can you guys please help

---

### Post by Arthur_D on 2012-03-06
Sorry, but this is not a Windows forum, and thus this thread will soon be closed. But to send you on the right track: visit the DosBox wiki page for info on how to mount ISO images directly in DosBox.

---

### Post by Perfect Storm on 2012-03-07
Old thread, thread closed.

---

