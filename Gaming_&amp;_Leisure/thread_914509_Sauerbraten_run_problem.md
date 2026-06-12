---
title: "Sauerbraten run problem"
date: 2008-09-08
forum: Gaming &amp; Leisure
---

### Post by dkdias on 2008-09-08
Just downloaded and installed Sauerbraten.  It's not running properly. I have an older Nvidia GeForce2 32 meg video card. I downloaded the drivers for the video card and according to the hardware drivers tab under system, it says they are enabled? I've read how I can change the settings on the card to lower the resolution, but I need more help. I'm new to Linux.  How do I change the settings to lower video resolution after starting the game?  Or do I change the setting in a terminal window?  When I run the game, it freezes up on the first screen.  I even have a hard time getting the menu to come up once the game has been started?  There is no keyboard or mouse control at all once it has been started..........Thanks for your help!!

---

### Post by J.K.Makowka on 2008-09-09
Edit the config.cfg in .sauerbraten

Make sure you turn off all shaders as you card can't handel them.

---

### Post by dkdias on 2008-09-09
Where do I find the config.cfg file?  How do I get to it to modify it? I am new to Linux and used to windows XP.........Thanks for your help!

---

### Post by J.K.Makowka on 2008-09-09
It's a simple text file you can edit (refer to the Sauerbraten wiki or manual/doc in the directory where you installed it).

About the location, well similary to the "my documents" folder in WinXP most of the settings of Linux programms are stored in your home directory, but hidden (all directorys that start with a "." are hidden by default).

So your .sauerbraten directory is under "/home/"your user name here"/.sauerbraten/"
And your filebrowser should have a "show hidden directorys" option somewhere too.

---

### Post by dkdias on 2008-09-09
Thank you for your help!!  I will try your fix after I get off work (which is for me in about 5 hours).  My son (16 yrs) has been wanting to play this game since I downloaded it over the weekend, but it didn't work.  I will post my results. Hopefully this will work and he will be able to play this game.  Thank you again for your help!!

---

### Post by J.K.Makowka on 2008-09-09
[http://cube.wikispaces.com/Performance+Guide](http://cube.wikispaces.com/Performance+Guide)

If you start it once with the -f0 from the terminal it will most likely work, and then you can change the settings in the menu.

Edit: [http://cube.wikispaces.com/FAQ](http://cube.wikispaces.com/FAQ)

Other tips.

---

### Post by collinp on 2008-09-09
After you get it working, dont expect any playable frames (Playable is 30 or above), my Geforce 6200 can barely get 40 consistently.

---

### Post by dkdias on 2008-09-10
I am going to try all these fixes, but it sounds like I may ultimately need to upgrade my video card.  Does anyone one have a suggestion for a good card that will work on the latest games, but not break my bank to buy it?  I briefly looked at cards a few minutes ago and saw some quite expensive ones, over $400.  Are there any video cards out there that are around $100.00 that would work for me?...(maybe I'm dreaming for a good card for around $100)  What should the card requirements be to be able to run the latest games? ........any suggestions for a good card at reasonable price would be appreicated.  Thanks

---

### Post by Perfect Storm on 2008-09-10
A nvidia card for sure - you can get 8xxx and 7xxx cheap if you buy them at the right place. Also you need to find out what your motherboard support (PCI,AGP x2/x4, express)

---

### Post by dkdias on 2008-09-10
I'm 90% sure my current Nvida card is a PCI card, but I will double check it.........Okay, I've been out of the loop for a while, I know what AGP is, but what is X2/x4 and express?

---

### Post by Perfect Storm on 2008-09-10
There's diffrent kind of AGP. The normal, then there's AGP x2 and AGP x4... I've heard of AGP x8 but I do not know if it's true. Express is PCIexpress which new motherboards have.

---

### Post by dkdias on 2008-09-10
Wow, I had no idea about the PCIexpress or the x2/x4.  I really don't think I have the express or the x2/x4.  I have a 8100 series Dell P4 with 512 megs ram. (I know I can upgrade my ram too)  The computer is about 6 or so years old.......I've got a PCI card slot available.  Where are the good deals for Nvidia cards! ...........so if I have an older motherboard I need to make sure I don't purchase a X2/X4 or an express because it won't work, Right?

---

### Post by dkdias on 2008-09-10
Is there any way to know what kind of AGP card slot I have?  I was wrong, my Nvidia GeForce2 card is in an AGP card slot.  I have several PCI card slots empty too.

---

### Post by J.K.Makowka on 2008-09-10
Just check what your Mainboard supports. But if it is of roughly the same age as your Geforce 2 than you will more likely be looking for a complete system upgrade. There arn't really any AGP cards you can buy anymore anyways.

Oh and the old PCI is something completely different from PCIExpress, the new standard for graphic-cards.

P.S.: Sauerbraten on low settings might still run reasonably on your computer. Try it first ;)

---

### Post by Ethyrdude on 2008-09-10
There is an 8x AGP but most likely your mb supports 2 or 4.  It sounds like it's time to upgrade, new systems have come down quite a bit in price and remember, you don't need to buy an operating system.

---

### Post by collinp on 2008-09-13
More than likely, the $400+ cards you saw was the bleeding edge GTX series of cards, you dont need one to play sauerbraten. A Geforce 9600GT would be great for Sauerbraten, as long as your Motherboard supports PCI Express x16 or PCI Express 2.0 x16 (They are cross compatible, you can put a PCI Express x16 card in a 2.0 x16 slot, and vice versa).

---

