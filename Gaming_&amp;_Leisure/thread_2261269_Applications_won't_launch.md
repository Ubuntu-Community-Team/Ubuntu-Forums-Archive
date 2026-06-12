---
title: "Applications won't launch"
date: 2015-01-17
forum: Gaming &amp; Leisure
---

### Post by nep-nori on 2015-01-17
I'm not new to Ubuntu but I figured I'd ask here because it's most likely just me being silly and forgetting something very obvious. Um, I'm running Ubuntu 14.04.1 LTS with XFCE4 as its DE (not Xubuntu, it's Ubuntu with XFCE built up from the Netboot mini.iso).

When I try to run POWDER! (the neat little roguelike) by double-clicking on the linux executable (that has no extension) nothing happens, no error code, no terminal, no crash, no freeze, literally nothing. And yes, the "allow to run as program" thingie is checked on the properties.

This also happens with Dungeon Crawl Stone Soup (another roguelike), Prime (yup, roguelike), ePSXe (an emulator) and Minecraft (even when specifically told to run on OpenJDK-7).

Surprisingly, opening my "games" folder where all of these programs are via terminal and trying to run them manually by typing their name has the same result...

---

### Post by Holger_Gehrke on 2015-01-17
How did you install the games ? Through the package manager or did you get tarballs from the authors site ? 

I've just installed powder through synaptic (yep, another fool for roguelikes; thank you for bringing this one to my attention; and there's even a version for my DS :) ) and it installed without any problem, made an entry in the menu and runs well from the menu, the command line or by double clicking in  the file manager. Using Ubuntu 12.04 LTS with XFCE (started out on Unity, installed XFCE additionally)

---

### Post by nep-nori on 2015-01-17
> **Holger_Gehrke said:**
> How did you install the games ? Through the package manager or did you get tarballs from the authors site ? 

All of 'em were downloaded directly off of the authors' websites, although not all of 'em are tarballs (minecraft being the prime example.)

> **Holger_Gehrke said:**
> I've just installed powder through synaptic (yep, another fool for roguelikes; thank you for bringing this one to my attention; and there's even a version for my DS :) ) and it installed without any problem, made an entry in the menu and runs well from the menu, the command line or by double clicking in  the file manager. Using Ubuntu 12.04 LTS with XFCE (started out on Unity, installed XFCE additionally)

Prime and Return to the Dungeons of Doom might be up your alley too, no religion systems though. Also everyone and their mom loves DoomRL, but not that many people give AliensRL a shot.

---

### Post by Bucky Ball on 2015-01-17
*Thread moved to **Gaming & Leisure**.*

You have the best chance of support by posting in the correct section. Good luck. ;)

---

### Post by efflandt on 2015-01-18
For minecraft you should be able to open a terminal, cd to the directory with the Minecraft.jar launcher that you downloaded from minecraft.net (not anything in ~/.minecraft), then do: **java -jar Minecraft.jar**
Or you can simply include the path to it (mine is still in Downloads): java -jar ~/Downloads/Minecraft.jar

If you eventually make a **desktop launcher**, it may have trouble with shell shortcuts or extra parameters unless you wrap it in a shell like: [B]sh -c 'java -jar ~/Downloads/Minecraft.jar'
[/B]
For other programs or scripts that you install yourself, it could be that they do not launch from a terminal because they are not in your $PATH. The current directory is not in your path by default. So even if they have execute permission and you are in that directory, they may not run unless you either precede them with "sh " or "./" prefix like: **sh scriptname** or **./scriptname** or full path to it.

I have not used XFCE, so not sure how it determines what to do if you double click on something with whatever it uses as file manager. But if you double click on an executable script in Unity's file manager, it usually asks if you want to open it with a text editor or run it, so it does not accidentally run if it does not work properly and/or you want to modify it.

---

### Post by Holger_Gehrke on 2015-01-18
> **nep-nori said:**
> 
Surprisingly, opening my "games" folder where all of these programs are via terminal and trying to run them manually by typing their name has the same result...

Actually you should have gotten an error message: "powder: command not found"

Only directories that are part of the list in the environment variable $PATH are searched for executables and the current working directory is not in the $PATH (for security reasons - imagine someone putting a malicious script named 'ls' someplace ...). When starting a program from someplace that's not in the $PATH you have to tell the computer where the executable is, for example './powder' to start powder from the file in the current working directory. 

I've tried powder from the authors site ([www.zincland.com/powder](www.zincland.com/powder)) and it works on Ubuntu 12.04.

---

### Post by nep-nori on 2015-01-18
> **efflandt said:**
> For minecraft you should be able to open a terminal, cd to the directory with the Minecraft.jar launcher that you downloaded from minecraft.net (not anything in ~/.minecraft), then do: **java -jar Minecraft.jar**

that worked! although it just confuses me more as to why double-clicking won't do anything. I thought I was missing a package or something... though maybe I am...

> **Holger_Gehrke said:**
> Actually you should have gotten an error message: "powder: command not found"

nope, originally I got no error message, no nothing.

To both efflandt and Holger_Gehrke: wanna hear something weird? I just tried double-clicking on the Powder executable again right after testing Minecraft and right before typing this, and it worked. And I have NO idea what I did or didn't do to make it work. I just double-clicked on the exact same icon in the exact same folder...

Let me try Prime or DCSS and I'll get back to you both.

EDIT: oh and Minecraft still doesn't work via double-clicking, I tried.

EDIT 2: "./prime" in my Games folder gives the following output: "./prime: error while loading shared libraries: libsigsegv.so.2: cannot open shared object file: No such file or directory"

"sh prime" says: "prime: 1: prime: Syntax error: "(" unexpected"

---

### Post by Aaron66 on 2015-01-22
Try going to properties then permissions and checking the box that says is executable, you'd be surprised at how many times this will mess you up it may not be the case for you but it could be :)

---

