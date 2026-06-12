---
title: "Games Not Working"
date: 2010-01-19
forum: Gaming &amp; Leisure
---

### Post by Bone Crusher on 2010-01-19
Lots of the games games I got from ubuntu software center don't work. Is there a problem with the game or my computer here are some Screenshots:

[IMG]http://img215.imageshack.us/img215/8125/screenshotbi.png[/IMG]
[IMG]http://img689.imageshack.us/img689/4964/screenshot1zr.png[/IMG]
[IMG]http://img689.imageshack.us/img689/6635/screenshot2qx.png[/IMG]

An other issue I am having is when I go to load a saved Simutrans game it says fatal error.

---

### Post by ucal on 2010-01-19
A few questions:  Do you have desktop effects enabled, like Compiz fusion?  If you do, you should turn them off, or configure them to shut off when you play games.  

What's your video card?  If it's ATI, then it might be a driver issue, in which case you might want to use a proprietary driver.

---

### Post by Bone Crusher on 2010-01-19
I have Compiz fusion. How do I shut it off? I have a widget layer with saved widgets that turn on automatically. I want to save that.

---

### Post by 5nak3 on 2010-01-19
If I remember correctly the widgets stay put every time you enable and disable Compiz, althought I've not used widgets since 8.04 so I do not know if this is 100% true.

As for compiz disabling, install a program called fusion icon, 

sudo apt-get install fusion-icon

and then before you play a game navigate to:

Applications -> System Tools -> Compiz fusion icon

Click it and a new icon should appear on your top taskbar, right click it and select windows manager and then choose metacity.

The screen will reload with metacity.

Play your game and after you finish to enable compiz do the same thing but when you choose your window manager you have to choose compiz instead.

---

### Post by Bone Crusher on 2010-01-19
Ok, even with Compiz it still is bad. How do I find out what graphics card I have? I know it is a ATI.

---

### Post by PrimoTurbo on 2010-01-19
> **Bone Crusher said:**
> Ok, even with Compiz it still is bad. How do I find out what graphics card I have? I know it is a ATI.

I think that some open source Linux games are buggy in general, you will need to treat each problem separately. Sometimes it's poor drivers, other times it's the program itself or a system setting.

Since I see a battery/plug I will assume you have a laptop. Most laptops have an integrated video card, if it's an ATI card it is most likely a variation of ATI Mobility. Unless you bought a very high end computer.

Best way is to review your computer specifications when you bought the computer, or sometimes you can just Google the model of your computer. There is probably a way to probe some details about your video card from the Terminal, but I'm not entirely sure what the command is for that.

The problem can also be related if you are using propriety ATI drivers or open source drivers. Propriety drivers give better performance but some tend to be buggy under Linux. Open source drivers tend to be slower in 3d or not work at all, but sometimes have more stable performance on the desktop.

---

### Post by Bone Crusher on 2010-01-19
I found it on amazon. It the same model, but it is a bit older. It just doesn't have a built in camera. Any way, here is the link:

[http://www.amazon.com/Toshiba-Satellite-A215-S7422-15-4-inch-Technology/dp/B000VVFULM](http://www.amazon.com/Toshiba-Satellite-A215-S7422-15-4-inch-Technology/dp/B000VVFULM)

I have however made quite a few upgrades/repairs:

I upgraded my Hard Drive to 250GB.
I upgraded my RAM to 2 GB.
I upgraded the battery to the 9-cell.

---

### Post by ucal on 2010-01-19
Okay, looks like you have an ATI Radeon 1200.  What version of Ubuntu are you using?  Apparently, there's some trouble with the catalyst drivers, your card, and ubuntu 9.04.  Might be a similar problem with later versions of Ubuntu as well, depending on what version of xserver they use.  You have two options if this is the case:  Use open source drivers, or downgrade to ubuntu 8.10 at most and use the 9.3 catalyst drivers.   

I'd wait and get someone who's more literate with the drivers before you do anything drastic like that though.

---

