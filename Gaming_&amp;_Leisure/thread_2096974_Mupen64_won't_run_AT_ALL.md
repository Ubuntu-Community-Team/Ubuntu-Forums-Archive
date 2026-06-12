---
title: "Mupen64 won't run AT ALL"
date: 2012-12-21
forum: Gaming &amp; Leisure
---

### Post by Hollowed Skulls Inc on 2012-12-21
Whenever I attempt to open it, nothing happens. Same with Commodore 64. I honestly don't remember when or how I installed Mupen64, so I can't reinstall.  I'm getting really pissed and am going to kill someone! :evil: 

... Please help me, Imma cry. :cry:

---

### Post by LillyDragon on 2012-12-21
So you're going to cry *and* dangle a poor little kitty over a tank of hungry sharks? That's a serious case of frustation man, you might to focus on getting other apps to run while you're troubleshooting this one. XD There's no need to feed a poor soul to the sharks!

You do know Mupen64 is a terminal-based application, right? It won't run on its own, you have to give it some parameters and a directory to a game before it will execute. (The former is optional, though.) This is what my launcher icon for Majora's Mask looks like :

```
mupen64plus --fullscreen --resolution(640x480) '/host/Users/Jonathan/My Games/Nintendo 64/Legend of Zelda - Majoras Mask'
```

Some of those parameters are easily tweaked, like the resolution, and don't forget to read the list of commands you can use to control Mupen with.

[http://code.google.com/p/mupen64plus/wiki/UIConsoleUsage](http://code.google.com/p/mupen64plus/wiki/UIConsoleUsage)

There are also a few working GUI clients you can try out as well, if you really need a graphical interface. Unfortunately, CuteMupen isn't packaged with Mupen64Plus anymore, whereas I do recall it being included on the 10.04 LTS's Software Center. You'll have to install that separately.

---

### Post by Hollowed Skulls Inc on 2012-12-21
> **johnluke728 said:**
> So you're going to cry *and* dangle a poor little kitty over a tank of hungry sharks? That's a serious case of frustation man, you might to focus on getting other apps to run while you're troubleshooting this one. XD There's no need to feed a poor soul to the sharks!

You do know Mupen64 is a terminal-based application, right? It won't run on its own, you have to give it some parameters and a directory to a game before it will execute. (The former is optional, though.) This is what my launcher icon for Majora's Mask looks like :

```
mupen64plus --fullscreen --resolution(640x480) '/host/Users/Jonathan/My Games/Nintendo 64/Legend of Zelda - Majoras Mask'
```Some of those parameters are easily tweaked, like the resolution, and don't forget to read the list of commands you can use to control Mupen with.


[http://code.google.com/p/mupen64plus/wiki/UIConsoleUsage](http://code.google.com/p/mupen64plus/wiki/UIConsoleUsage)

There are also a few working GUI clients you can try out as well, if you really need a graphical interface. Unfortunately, CuteMupen isn't packaged with Mupen64Plus anymore, whereas I do recall it being included on the 10.04 LTS's Software Center. You'll have to install that separately.

Using --fullscreen --resolution(640x480) won't work for me. I had to  remove it for it to be able to work. How do I edit settings? And I had  Mupen64 as an application, I could just click on it. I also saw many videos in which it was a program just like project64.

---

### Post by LillyDragon on 2012-12-21
That's strange, and I'm actually getting better performance from it on 64-bit than I ever did with the 32-bit edition.

You're probably seeing videos of the Windows version, which has its own GUI, whereas the port to Linux doesn't include a user interface. Although as I said before, I remember earlier versions for Ubuntu being packed with CuteMupen for user-friendliness. I'm having trouble getting Mupen64plus to run right now myself, so I'll see what I can do to make it behave again.

To edit the settings, go to /home/username/.config/mupen64plus/mupen64plus.cfg . Most of the basic settings are here, but if you want to edit controller mappings as well as more advanced settings, check out your /usr/share/mupen64plus/ directory with super user priviledges to change them.

```
sudo gedit /usr/share/mupen64plus/InputAutoCfg.ini
```

Even more settings here :

```
sudo gedit /usr/share/mupen64plus/mupen64plus.ini
```

**EDIT** : If you're not sure what buttons to map to your controller, use jstest-gtk from the Software Center to tell which buttons are 0 through 24.

**SON OF EDIT :** For whatever reason, anytime the directory I provide is complicated with spaces or special characters, Mupen doesn't like it. So long as I give the disk images simple names in my home directory, everything's fine, such as this : 

```
/home/jonathan/N64/LoZMM.z64
```

**GRANDSON OF EDIT :** Okay, turns out I was forgetting the file extension to the disk image the whole time on my end, oops. :#

So the big question I have to ask is whether or the directory you're providing the emulator is accurate? Linux in general is case-sensitive, so if one letter is lowercase as opposed to upper, it returns nothing. Mupen would not start on me twice a while ago simply because I missed a capitol M in file name. It couldn't hurt to double-check your launcher's syntax.

---

