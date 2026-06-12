---
title: "Newbie to linux"
date: 2006-03-13
forum: Desktop Environments
---

### Post by crakkajakka15 on 2006-03-13
OK heres what im running, hp p3 1.0 gzh 384 mb of ram. I recently went out and bought a seagate 80 gig hard drive and installed it. So i throw in my ubuntu intel disc and ran through the installation. now it comes to this screen where it say the first part of the installation is finished and now the system will reboot. It reboots and comes to the ubuntu loading screen and gets about half way though the loading bar and then the screen just goes blank and it comes to this black screen with just this little underscore/cursor looking thing and just sits there. It also dose that when i try to run the live cd version also whats going on???? please help any would be great

---

### Post by adamkane on 2006-03-13
I'm not an expert, but sounds like a video card problem. If you have another video card available, you might want to try an install with a different video card.

---

### Post by aysiu on 2006-03-13
Sounds like a screen resolution issue.

What happens when you press Control-Alt-F1?

If all is going well, that should get you to a black screen with only these words in white: ```
Ubuntu 5.10 "Breezy Badger" ubuntu tty1

ubuntu login:
```

---

### Post by crakkajakka15 on 2006-03-13
yea i dont see the ubuntu user login all it is the the black screen with the white cursor in the top left, i havent tried hitting alt control and f1, what exactly dose that do.......i mean it looks as if everything is loading correctly then it just jumps to that screen. the video card in the computer is a nvida geforce 2, but when i try to use the screen with the onboard video, the screen dosent even come on. also the olny thing that FAILS when loading is the random number generator??? any more help would be great thanks guys

---

### Post by aysiu on 2006-03-13
Control-Alt-F1 lets you log in at a different "run level" (I don't know what this means exactly, but I know what the effect is--a new login), which is console-based, so screen resolution should not be an issue.

If you do Control-Alt-F7 (the default "run level"), it tries to load a graphical environment. If it's trying for too high a screen resolution, you get issues.

Control-Alt-F1 will let you login at a sort of DOS-like screen and fix the screen resolution.

---

### Post by crakkajakka15 on 2006-03-15
when in the boot process should i hit these keys to try and change the screen res. keep the help coming thanks again

also  what kind of performance should i expect with linux on this system to something like windows in running general apps (i.e. Firefox) and such

---

### Post by aysiu on 2006-03-15
Press Control-Alt-F1 when you get to the blank screen.

As for performance...

I have two computers, one has 128 MB of RAM, the other 512 MB of RAM.

Firefox runs just as fast as it normally would on both (a little bit slower in rendering pages on the 128 one, but that's to be expected).

For 384 MB of RAM, you should be good. Things won't be lightning fast with KDE or Gnome without some major tweaks. You can also substitute something lighter (like XFCE).

Let's try to get a workable screen first, though, eh?

---

