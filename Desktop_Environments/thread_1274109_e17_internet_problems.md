---
title: "e17 internet problems"
date: 2009-09-24
forum: Desktop Environments
---

### Post by logicalform on 2009-09-24
Hey all. I've been in the mood to try something new so I installed e17 (enlightenment). I knew it might take some setting up/getting used to, but for some reason my wireless connection won't work. Do I need to install some sort of network managing application to go along with e17? Why won't the default one work (I'm using linux mint, same as ubuntu). If I do need to install something, what should it be? The weird thing about it is that I tried a live usb with elive compiz on it and, even though it clearly has a network manager, my internet doesn't work there either. 

Help? Please?

Thanks.

---

### Post by squaregoldfish on 2009-09-24
You do need to be running a network manager of some description. There's two options here.

The first is to install the still-in-development exalt module & it's supporting tools. I haven't done this, so I can't say what it involves.

The second (and my method) is to run the systray module, and then run GNOME's nmapplet in it.

The systray module should be part of the standard install, so depending on how you got e17, you'll either already have it, or (if you compiled) you can compile the module and install it.

Then you need to run nmapplet as a startup program for e17 - you can do this through the Settings Panel under the Apps menu.

I know this is a brief answer with not much detail (pushed for time!). If you have trouble figuring anything out, post a reply and I'll help out some more.

Steve.

---

### Post by logicalform on 2009-09-26
Thanks for the reply. I'm relatively new to linux, but I think I'll be able to do it... For the systray applet, do I just make it run at startup if it's installed (I used apt-get to install e17 after adding a repo, so it's probably there) or do I need to involve apt-get now?

My new problem is that, while trying to install the opengeu DE (which involved a system upgrade) my network manager somehow completely disappeared (it's gone even from Mint's control panel). How do I get it back with no internet (using a liveUSB right now)? Install disc? Can I use the iso that I have on my HD?
Sorry for being a nuissance, I'm still new! 
 
-Justin

p.s. How do I go about getting dvorak working in e17? Typing this in qwerty is killing my brain...

---

### Post by XubuRoxMySox on 2009-09-26
I suggest installing wicd from the repositories or

```
sudo apt-get install wicd
```

You may have to activate it manually each time you log in until you set it up in your Services menu.

-Robin

---

### Post by squaregoldfish on 2009-09-27
Does mint use GNOME? If so, you should be able to just run the following from a terminal:

```
nm-applet -sm-disable
```

If nm-applet isn't installed, you should be able to get apt to use the install cd as a package source and install it from there.

Steve.

PS Not sure on the Dvorak question.

PPS Check out the [enlightenment-users mailing list]("https://lists.sourceforge.net/lists/listinfo/enlightenment-users") - very useful.

---

