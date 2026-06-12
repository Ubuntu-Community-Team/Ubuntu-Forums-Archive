---
title: "Switching to Ubuntu- a few questions?"
date: 2009-04-27
forum: General Help
---

### Post by Aristai on 2009-04-27
Hello Ubuntu forums

I'm currently running Windows Vista (and getting fairly tired of it) and have heard nothing but praise for Linux in general, especially Ubuntu. I'm going to run a dual boot and try it out, but I have a few questions.

Running outside programs- I know there seems to be a solution to everything when it comes to running Windows or Apple programs, but i just wanted to make absolutely sure. The most important ones for me are in the Adobe CS4 collection (Windows version), as well as music/MIDI based programs such as Guitar Pro and Cubase. Is anybody else running these? I am also an avid gamer, and have been told most games can be run through Wine- but I have also heard of problems with more graphic-intensive games (Everquest 2, for example). How does Wine work exactly? How reliable is it, and does it often have problems with newer games?

On a similar note, will non-Linux programs run differently? Will i need to open them through an emulator program or would they open as normal?

My last question is on the general interface. Every screenshot i see seems to be completely different, which is fantastic, would definately ease the transition- but how easy is it to customise your own? Or are most interfaces simply pre-made and downloaded?

Thank you for your responses
-A Linux novice

---

### Post by nothingspecial on 2009-04-27
Hi, if you are planning to run a dual boot then your first 2 questions wont be an issue. Far better to run windows programs (if you need them) in windows.

As to the interface question, there are packages you can download to customize your system if you want, I think. But that`s not the point. Part of the fun of linux is to customize your system exactly how you want it. And, I`m afraid it`s like anything else - it`s easy when you know how but might seem a littl`e daunting at first.

Give it a go, you`ve nothing to loose.  :)

Just make sure you backup anything you don`t want to loose before you install....... anyone can press the wrong key.

---

### Post by Alterax on 2009-04-27
Well, it's been awhile since I've been in the Windows world, but let's see what I can come up with for you:

You can find out about WINE compatibility through their site, winehq.com.  Not all programs will run on it, but they do have a good list of known working and non-working programs.  I --think-- Photoshop CS4 is in the list, but it's also worth mentioning that the GIMP project has a plugin available that lets you use photoshop addins--which may be all you need.

Some programs do fine in Wine.  Others don't, but you can get a paid version called Cedega, which does have more supported Windows programs than Wine.  

Another option is to consider programs not by name, but by the function you want to accomplish with them.  There's usually a program in the repositories, available free of charge, that does the same job as the program you're accustomed to on Windows and Mac.

As far as customizing the GUI, it's not difficult at all.  You'll probably start off using the GNOME environment, which is the default environment used by Ubuntu.  You can do plenty within it; even after using others extensively I still fall back to it as my favorite.  KDE (Kopernicus Desktop Environment, the default for Kubuntu) can be a lot more customizable, but the options can sometimes prove to be too many for people new at customizing.  XFCD (which means nothing!) is more lightweight; it's not as customizable as either, but it's very snappy and can make older hardware usable.

My advice is to start off with GNOME and find some fresh components for it at [www.gnome-look.org](www.gnome-look.org), most notably the GTK+ kits (which handles the controls inside the windows) and the Metacity themes (which handle what your window's borders and title bars look at).  They can be installed through SYSTEM > PREFERENCES > APPEARANCE.

Have fun!

---

### Post by LoneWolfJack on 2009-04-27
first: don't expect linux to be "windows without problems".

you can run many windows programs through wine, though not all. go here to check whether your windows app is working or not: [http://appdb.winehq.org/]("http://appdb.winehq.org/")

the wine project tries to re-implement all necessary inner workings of windows. this is not always that easy because, for example, there is no directx for linux, so the wine programmers need to learn how directx (all versions and all updates) work and re-implement the entire thing though the use of open gl. whether or not an app is working through wine depends on whether all necessary windows behavior is correctly implemented (or at all). its quite a daunting task.

gnome (the GUI of ubuntu) is highly customizable. you decide where you put your bars, how many there are, what icons are on them, how big they are, etc. etc. etc.

---

### Post by LoneWolfJack on 2009-04-27
vorlon B gone :P

---

### Post by fballem on 2009-04-27
> **Aristai said:**
> Hello Ubuntu forums

I'm currently running Windows Vista (and getting fairly tired of it) and have heard nothing but praise for Linux in general, especially Ubuntu. I'm going to run a dual boot and try it out, but I have a few questions.

Running outside programs- I know there seems to be a solution to everything when it comes to running Windows or Apple programs, but i just wanted to make absolutely sure. The most important ones for me are in the Adobe CS4 collection (Windows version), as well as music/MIDI based programs such as Guitar Pro and Cubase. Is anybody else running these? I am also an avid gamer, and have been told most games can be run through Wine- but I have also heard of problems with more graphic-intensive games (Everquest 2, for example). How does Wine work exactly? How reliable is it, and does it often have problems with newer games?

On a similar note, will non-Linux programs run differently? Will i need to open them through an emulator program or would they open as normal?

My last question is on the general interface. Every screenshot i see seems to be completely different, which is fantastic, would definately ease the transition- but how easy is it to customise your own? Or are most interfaces simply pre-made and downloaded?

Thank you for your responses
-A Linux novice

I can answer your last question - it's your choice. If you want, you can use the stock interfaces that come installed with ubuntu. These consist of themes (generally include icons, fonts, and backgrounds in any combination) or change your background to a solid colour or to some other image, or change your fonts, or get really fancy with the eye-candy.

To be honest, I would go with the stock items until you get more comfortable with ubuntu. Do research into GTK Themes (which are the items that make up a GNOME Desktop) and possibly GDM Themes (which are the items that make up the log-in). This assumes that you want to use GNOME as your desktop.

You may want to look at KDE, in which case, you might want to download and install Kubuntu or openSUSE. Kubuntu is ubuntu with KDE, openSUSE is a different distribution that has both Gnome and KDE. I have heard that openSUSE has an excellent implementation of KDE, but I prefer GNOME.

In any case, there are six things to keep in mind:
1. Linux, in any flavour and any distribution, is not Windows.
2. The fact that Linux is not Windows is a good thing and a bad thing, depending on whether it is good or bad for you at that particular time.
3. It will take you time to learn - be patient with yourself and don't be afraid to ask for help.
4. You will, I'm sure, be pleasantly surprised at the amount and quality of the help you will get.
5. You will also be appalled at the ferocity of some of the flamewars that you will accidentally start.
6. Ignore the flamewars, accept the help, and offer it when you can.

Hope this helps,

---

