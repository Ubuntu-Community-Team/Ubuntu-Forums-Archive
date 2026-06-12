---
title: "m64py front end to Mupen64plus path problems."
date: 2014-06-28
forum: Emulators
---

### Post by ethankschantz on 2014-06-28
So I can get mupen64plus to run fine on my computer, without lag or many issues of any sort really. But the total lack of a GUI makes a lot of things more difficult than I think they should be, like increasing the size of the window or changing the terrible controls on my gamepad. So I downloaded and installed m64py to give it a nice front end, but it didn't work right away like I thought it would. First it tells me it can't find the library file for mupen64plus, and then it sends me to the "paths" tab on this little settings Window. I tried browsing for the path to the mupen64plus library file, but it wouldn't let me select the file, so I eventually just typed in "usr/lib/i386-linux-gnu/mupen64plus/", but after that It still asks for three more directories, and I have no idea where to find them. What should I fill those out with? Am I doing something wrong already? Once I fill out those paths, is that all I need to do, or is there still more to get the emulator working with a GUI? All and any help would be appreciated.

---

### Post by BigSilly on 2014-06-29
I seem to remember having a similar issue with the new version myself, but I forget how I fixed it!

A quick look in my paths settings reveals these:

```
Library File - /usr/lib/x86_64-linux-gnu/libmupen64plus.so.2.0.0

Plugins Directory - /usr/lib/x86_64-linux-gnu/mupen64plus

Data Directory - /usr/share/games/mupen64plus
```

Hope this is useful to you. :)  Note: I am using a 64 bit system.

---

### Post by ethankschantz on 2014-06-29
I probably should've mentioned that I'm using a 32 bit system in my original post. Unfortunately this doesn't work for me.

---

