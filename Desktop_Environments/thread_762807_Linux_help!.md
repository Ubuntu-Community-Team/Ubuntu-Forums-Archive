---
title: "Linux help!"
date: 2008-04-22
forum: Desktop Environments
---

### Post by Danial Weston on 2008-04-22
Hello,

I'm a new user of Ubuntu, and I need help.

1) can I download iTunes for Linux?

2) How do I add more email address in mail envirement?

3) How do I get sound working?

4) This is the old verion of Ubuntu, not the ubuntu 8

What do I do?

---

### Post by eriqjaffe on 2008-04-22
> **Danial Weston said:**
> 1) can I download iTunes for LinuxThere is no native version, but you might be able to run in through Wine.  Searching the forums for "Wine iTunes" will probably turn up a bunch of threads about that.

There are also plenty of Linux-native applications with similar functionality to iTunes.  If you have Ubuntu installed, you'll already have Rhythmbox, and a lot of people swear by Amarok (although that requires a bunch of KDE libraries, which is a turn-off for some people).

---

### Post by Danial Weston on 2008-04-22
> **eriqjaffe said:**
> There is no native version, but you might be able to run in through Wine.  Searching the forums for "Wine iTunes" will probably turn up a bunch of threads about that.

There are also plenty of Linux-native applications with similar functionality to iTunes.  If you have Ubuntu installed, you'll already have Rhythmbox, and a lot of people swear by Amarok (although that requires a bunch of KDE libraries, which is a turn-off for some people).
i've just got no idea how to use ubuntu.. so ok i'll search for wine itunes 

thanks.

---

### Post by Danial Weston on 2008-04-22
Hard? It says I don't have wine?
bash command not found? Do I need to install it?

---

### Post by Danial Weston on 2008-04-22
Also, how do I get flash player working?

---

### Post by mlentink on 2008-04-22
You might want to take a look at the [Ubuntu website ]("https://help.ubuntu.com")first. There's quite a bit of info in there.
You could also look [here]("http://www.ubuntuguide.org/") and [here]("https://help.ubuntu.com/community/")

Of course there's the [monkeyblog]("http://monkeyblog.org/ubuntu/installing/"), which should help you install stuff, and the undervalued [Psychocats]("http://www.psychocats.net/ubuntu/index"), where you will get most of what you would want to know

---

### Post by markjensen on 2008-04-22
You can install wine from your package manager.

You said you wanted "iTunes".  Do you really just want an online music store, or do you have an account with Apple already that you need to keep using?   Amazon offers a native Linux app for their (non-DRM!) music store, if purchasing music from other sources is acceptable.

---

### Post by Danial Weston on 2008-04-22
> **markjensen said:**
> You can install wine from your package manager.

You said you wanted "iTunes".  Do you really just want an online music store, or do you have an account with Apple already that you need to keep using?   Amazon offers a native Linux app for their (non-DRM!) music store, if purchasing music from other sources is acceptable.
I just want my iPod working, thats why I wanted itunes

XML Parsing Error: not well-formed
Location: chrome://browser/content/sanitize.xul
Line Number 1, Column 2:e();
-^

Why do I get this in FireFox?

---

### Post by Danial Weston on 2008-04-22
> **Danial Weston said:**
> I just want my iPod working, thats why I wanted itunes

XML Parsing Error: not well-formed
Location: chrome://browser/content/sanitize.xul
Line Number 1, Column 2:e();
-^

Why do I get this in FireFox?
also how do I find package manger :P

---

### Post by markjensen on 2008-04-22
If you are just after iPod management, maybe something like Banshee would be what you need?
[http://www.simplehelp.net/2007/07/08/how-to-use-banshee-to-manage-your-ipod-in-ubuntu/](http://www.simplehelp.net/2007/07/08/how-to-use-banshee-to-manage-your-ipod-in-ubuntu/)


EDIT:  This thread is just all over the place, isn't it?   Not really about "Desktop Environments" at all.  Maybe a mod can move this to the "Beginner" section, since there are basic questions about package managers and such.

---

### Post by RainCT on 2008-04-22
Welcome.

You can use your iPod with many native programs, like Rhythmbox and Amarok which eriqjaffe mentioned above.

---

### Post by Danial Weston on 2008-04-22
> **markjensen said:**
> If you are just after iPod management, maybe something like Banshee would be what you need?
[http://www.simplehelp.net/2007/07/08/how-to-use-banshee-to-manage-your-ipod-in-ubuntu/](http://www.simplehelp.net/2007/07/08/how-to-use-banshee-to-manage-your-ipod-in-ubuntu/)
got no idea what it is, dose it put music on the ipod, etc?

---

### Post by Danial Weston on 2008-04-22
> **markjensen said:**
> If you are just after iPod management, maybe something like Banshee would be what you need?
[http://www.simplehelp.net/2007/07/08/how-to-use-banshee-to-manage-your-ipod-in-ubuntu/](http://www.simplehelp.net/2007/07/08/how-to-use-banshee-to-manage-your-ipod-in-ubuntu/)


EDIT:  This thread is just all over the place, isn't it?   Not really about "Desktop Environments" at all.  Maybe a mod can move this to the "Beginner" section, since there are basic questions about package managers and such.
got no idea what it is, dose it put music on the ipod, etc?

---

### Post by markjensen on 2008-04-22
> **Danial Weston said:**
> got no idea what it is, dose it put music on the ipod, etc?

Might I respectfully ask you to _read_ what I linked to?  It is very thorough and walks you through step-by-step.  Honestly.  It explains how banshee synchronizes music to your iPod.   It is all there.

---

### Post by RainCT on 2008-04-22
[Deleted - Double post]

---

### Post by Danial Weston on 2008-04-22
OK,

and how do I torrent?

---

### Post by Danial Weston on 2008-04-22
> **Danial Weston said:**
> OK,

and how do I torrent?
and what about itunes?

it says to me wine installitunes.exe? is that right?

i'm guessing wine is something to make .exe files to work

---

### Post by markjensen on 2008-04-22
I use transmission for my torrents.  If it isn't installed by default, you can find it in your package manager.   Or just try the default torrent app included in your menus (if one exists).

And .exe apps can be run through wine by association when you download them, it will prompt you to "open with wine".  Or when you use your file browser, and you double-click an .exe, it ought to know to use wine.

You can manually initiate this from a terminal by doing a **wine minesweeper.exe** or some such, based on what Windows executable you wish to run.

---

### Post by Danial Weston on 2008-04-22
> **markjensen said:**
> I use transmission for my torrents.  If it isn't installed by default, you can find it in your package manager.   Or just try the default torrent app included in your menus (if one exists).

And .exe apps can be run through wine by association when you download them, it will prompt you to "open with wine".  Or when you use your file browser, and you double-click an .exe, it ought to know to use wine.

You can manually initiate this from a terminal by doing a **wine minesweeper.exe** or some such, based on what Windows executable you wish to run.
i don't get this

i just downloaded itunes

and did 

wine itunessetup.exe

it brings me back with this

wine: could not load L"C:\\windows\\system32\\itunessetup.exe": Module not found

---

### Post by markjensen on 2008-04-22
I can try it when I get home.

When you try to run any other .exe (from the web, or downloaded) via firefox or your file browser by double-clicking, does it try to run it through wine?  If not, is "wine" listed as an available app to run the .exe file?

---

### Post by Danial Weston on 2008-04-22
> **markjensen said:**
> I can try it when I get home.

When you try to run any other .exe (from the web, or downloaded) via firefox or your file browser by double-clicking, does it try to run it through wine?  If not, is "wine" listed as an available app to run the .exe file?
Got it, I was running it through termanal

---

### Post by Danial Weston on 2008-04-22
nothigns working for me

can't install itunes no ipod for me :(

---

### Post by gitpik on 2008-04-22
> **Danial Weston said:**
> Also, how do I get flash player working?

This really helped me out when I first started, It was posted already but (at least for me) links are invisible right now so here it is again. :D
[http://www.psychocats.net/ubuntu/index.php]("http://www.psychocats.net/ubuntu/index.php")

---

### Post by markjensen on 2008-04-22
> **Danial Weston said:**
> nothigns working for me

can't install itunes no ipod for me :(

Ummm... Did you even _try_ any of the other apps mentioned that work with iPods?

---

### Post by scottuss on 2008-04-22
To be fair, I have used both Banshee and Rhythmbox for my iPod (80GB classic) and both work fantastically. You just have to try!

---

### Post by hulio40 on 2008-04-22
yeah i use rythmbox for my ipod and its perfect 


what do u mean by:  How do I add more email address in mail envirement? 

for the sound Double click on the speaker icon in the System Tray to bring up the mixer, make sure everything is enabled and if ur using a laptop try this:

2) Go into preferences and make sure that "External Amplifier" is selected to show on the mixer.

3) When you go back to the mixer, you will have a new tab "Switches." Select that tab.

4) Uncheck the only box on that tab. It's the box marked external amplifier.

5) Close mixer. Your sound will now work


to get flash working  go to add/remove and type flash check the first app and press apply then restart ur browsers if needed
and try it it should work

---

### Post by russo.mic on 2008-04-23
So, I'm pretty sure you cannot install iTunes with wine.  If you must use i tunes, may I recommend you think about a virtual machine?

Still, there is Rythembox, songbird, and Amarok which all support ipod databases.  

Good luck!

---

