---
title: "my video card"
date: 2011-10-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TheRacerX on 2011-10-12
im having this weird issue with my video card im now running Ubuntu 10.10 on my Dell Dimension 3000 desktop i just installed a ATI Radeon 7500 PCI and its giving me 2 problems 1)its making my monitor too bright and ive tried every combination of configurations to turn it down but nothing works and 2) my computers Embedded graphics are weaker then my video card but my video card lags the graphics SOOO much worse then the Embedded video, can anyone help?

---

### Post by Basher101 on 2011-10-12
ATI cards still have rather poor support in linux in general so its the driver for sure. The developers do make progress but it sometimes still aint enough. To turn down the brightness try the command ```
sudo setpci -s 00:02.0 F4.B=dd
``` The two letters at the end are HEX code. So "0" is the brightest and "ff" is the darkest. Just try to find yourself your prefered brightness if the command works. As for the driver, try a 11.04 Live CD and see if it lags there too.

---

### Post by TheRacerX on 2011-10-12
11.04 wont even run on this old computer ive tried it and had to downgrade one distro just to be able to use my computer

---

### Post by Basher101 on 2011-10-12
then i guess the lags are a combination of poor drivers + your pc not being able to handle Gnome. Try a Lubuntu live CD or Xubuntu (which are specifically made for older computers using the LXDE and XFCE Desktop Environments. In other words, they use alot more lightweight interfaces.) The different interface may uncomfort you at first, but i guess its better than having constant lags perhaps?

---

### Post by TheRacerX on 2011-10-12
but again like i said when i plug my VGA into the Embedded graphics of the motherboard the graphics dont lag one bit other then i cant watch high def videos which is why i bought the more powerful video card to help with that problem but its become more of a hindrance then a help.

---

### Post by Basher101 on 2011-10-12
it is the driver for sure then. right now the only thing you can do is:

1.wait for better drivers to come out

2.get a card with higher compatibility (nVidia)

3.get another distro where the Desktop Interface does not lag

otherwise there is nothing you can do.

---

### Post by TheRacerX on 2011-10-12
well that was a waste of $25 then

---

### Post by Basher101 on 2011-10-12
the one thing i learned is IF you upgrade ANY hardware, get something decent. Look for a nVidia card, those are much better supported. 

my GTX 570 (most powerful single GPU card after the GTX 580 avaiable) has just arrived :3. But the gtx 580 costs twice as much as the 570...so the 570 was the best bang for the buck i could get^^ problem is, its the first part that arrived...motherboard, cpu and everything else has yet to come :/

---

### Post by TheRacerX on 2011-10-12
i know what your getting at but im a man on a VERY strict budget i barely have 25 to $30 to spend on random crap so uber powerful PCI video cards just arent in my budget otherwise id buy a whole new computer and throw this dinosaur of a computer in the garbage bin

---

### Post by Basher101 on 2011-10-12
thats why Xubuntu and Lubuntu are so great since they run on ancient stone computers. Nice try getting Windows 7 run on that...

so if a new card is no option, try Lubuntu or Xubuntu if they work better with your card.

---

### Post by TheRacerX on 2011-10-12
would the Bios have anything to do with it cause my BIOS is the old A01 version not the A03 that they say on the Dell site i should be upgrading too....my effing CELLPHONE is faster then my computer haha

---

### Post by Basher101 on 2011-10-12
Thats a good idea. just be careful tho, if you mess up flashing your BIOS you render your Motherboard unusable.

---

### Post by TheRacerX on 2011-10-12
then im thinking i shall get a more skilled person then myself to do it so i dont render my computer useless

---

### Post by Basher101 on 2011-10-12
> **theracerx said:**
> then im thinking i shall get a more skilled person then myself to do it so i dont render my computer useless

+1

---

### Post by TheRacerX on 2011-10-12
question though how would i get the file to upgrade the BIOS? cause ive seen it done on Windows but never on Ubuntu

---

### Post by Basher101 on 2011-10-12
Your BIOS is not Operating System bound. You can only get it from your computer manufacturer's website. Somewhere there will be a download section where you can get it. As for the installation, it depends on the motherboard. In your case you must make a Bootable CD with the bios files and a special program to install a new BIOS.

---

