---
title: "Slower than XP?"
date: 2006-09-26
forum: Desktop Environments
---

### Post by LostJot on 2006-09-26
My new install of Ubuntu seems to load up slower and generally run slower than my new install of Windows XP. On XP, Word is open in a flash, literally. On Ubuntu, OpenOffice Word is far slower to open. 

I run on a laptop (P4), and for me one of the main issues is the fan. I don't like to overtask the computer, that's just me (I am wierd). So I get disconcerted when the fan switches onto a speed that is noticeably noisy. Now, XP never does this if it's just at there idling. But I have found that Ubuntu does. This may not seem like a major issue, because it probably isn't, but I just don't understand why it is doing this. Also, the hard-drive access light is constantly flickering lightly, what is it doing? Swap file stuff? 

Is it the case that whilst Ubuntu is not necessarily quicker than XP, over a longer period of time it suffers far less and does not suffer significant performance drops that XP is prone to?

---

### Post by andypaxo on 2006-09-26
It's a shame that you are finding Ubuntu to be slow, my personal experience is:

- Ubuntu and Windows take a similar amount of time to load to the desktop... But the Ubuntu desktop is responsive straight away, Windows just sits there with the lights on, but nobody home for some while.

- OpenOffice historically has been slow (version 1 was terrible) but is getting faster with each release. There are 'quick launcher' programs out there (and in apt) which will make OO load faster. (Possibly at the expense of system starting time, I'm not sure)

- XP does seem to get bogged down over time with everything wanting to run at startup, every application wanting a little buddy in the system tray, viruses etc. running away in the background... I've not come across this problem with Linux

---

### Post by frequenicity on 2006-09-26
And don't forget, the main reason that Microsoft apps (Word, Excel, Outlook, IE) boot up faster in Windows than others is that there is ALWAYS part of the program running in the OS, whether you are using it or not. That's not really fair to compare "opening times" of something like Word vs OpenOffice, or IE vs Firefox because of this.

---

### Post by Iam8up on 2006-09-26
The fan is controlled by BIOS.  This means that the temperature of the CPU is increasing, thus, it is being used.  You may want to watch 'top' for a bit and see if anything sprouts up.  I have noticed that a lot of the screen savers and X put the CPU on high load very often, unfortunatly.

How big is you swap file?  Try a df -h for this.  I would suggest a swap file of 1024MB.

---

### Post by doobit on 2006-09-26
> **andypaxo said:**
> 
- OpenOffice historically has been slow (version 1 was terrible) but is getting faster with each release. There are 'quick launcher' programs out there (and in apt) which will make OO load faster. (Possibly at the expense of system starting time, I'm not sure)


The QuickLauncher is available as a setting in the preferences of OO. Also, you can make Open Office a lot quicker by allocating more memory to it (Also in the preferences).

---

### Post by LostJot on 2006-09-26
> OpenOffice historically has been slow (version 1 was terrible) but is getting faster with each release. There are 'quick launcher' programs out there (and in apt) which will make OO load faster. (Possibly at the expense of system starting time, I'm not sure)

Whilst I'm here, what is the equation editor like on OpenOffice? On Word, I tended to use MathType, as Equation Editor 3.0 was not sufficient. But I'm not sure if there is a similar extension for openoffice, espcially not for Linux. 

> - XP does seem to get bogged down over time with everything wanting to run at startup, every application wanting a little buddy in the system tray, viruses etc. running away in the background... I've not come across this problem with Linux

Good point, especially about the buddies in the system tray. Devilware like RealPlayer and Quicktime seem to be fans of this :mad: 

> And don't forget, the main reason that Microsoft apps (Word, Excel, Outlook, IE) boot up faster in Windows than others is that there is ALWAYS part of the program running in the OS, whether you are using it or not. That's not really fair to compare "opening times" of something like Word vs OpenOffice, or IE vs Firefox because of this.

I recall this argument when I was looking into Opera. In the end, I found Opera still loaded very fast, I was impressed. 
I wasn't aware that Office is pre-loaded in such a fashion? Since IE comes with Windows, I assumed that this was the only one that was partly running all the time?

> The fan is controlled by BIOS. This means that the temperature of the CPU is increasing, thus, it is being used. You may want to watch 'top' for a bit and see if anything sprouts up. I have noticed that a lot of the screen savers and X put the CPU on high load very often, unfortunatly.

How big is you swap file? Try a df -h for this. I would suggest a swap file of 1024MB.

Yeah, that's why I don't like it. I want my hardware to last as long as possible, hence I don't like having the fan on high because I assume that there's a lot of heat massacaring my stuff :p 
On screen savers, I always just use a blank screen anyway.

My swap file is 800MB. Is that OK? I have 512MB of RAM (DDR PC2000 I think). 

Thanks for your time guys :)

---

### Post by andypaxo on 2006-09-26
The equation editor for OpenOffice is called Math, and can be launched in the same way as the other parts of OO (If you don't see it in your main menu, go to Accessories -> Menu Editor to enable it)
Not sure how this stands up to MathType, as I've never used either. Just give it a try!

I didn't know about MS Office loading with the OS either. Sounds like what a quick launcher should be doing (and is similar to what the OO quick launcher does)

As for swap - different people recommend different things (usually without giving any reason in particular)
The figures I have seen are usually in between your RAM size, or twice your RAM size, so yours sounds good.

---

### Post by Aleksandersen on 2006-09-26
Hi,

I just installed Ubuntu 6.06 on my computer, and it runs much faster than Windows XP. But the booting takes much longer. After I sign in it starts running much faster tough.

---

### Post by orb9220 on 2006-09-26
And do you have the video drivers installed for your graphics chipset.

The default ubuntu work but are not optimized for using the advance features like 3d accelaration.

Many people complain of gnome being slow until they installed the graphics driver for thier chipset then everything went to normal.

Kinda like the default winxp vga driver and everything is sluggish until you install the video driver.

---

### Post by IYY on 2006-09-26
> Whilst I'm here, what is the equation editor like on OpenOffice? On Word, I tended to use MathType, as Equation Editor 3.0 was not sufficient. But I'm not sure if there is a similar extension for openoffice, espcially not for Linux.

It's text based. Not as intuitive, but I find that after using it for a week or so, I can type my equations much faster than in MS Word.

However, I think that OpenOffice is slower than MS Office, even if you factor in the fact that MS preloads Office into RAM.

---

### Post by waspinator on 2007-03-30
I've noticed the same thing. I've got an IBM A31 1.9 GHz P4Mobile, 512 MB RAM, and XP is MUCH faster then the 7.04 Beta. It might be the beta, in that case I hope it speeds up with the final. Ubuntu also clips (distorts) my audio, something XP never did. I'm sticking with Ubuntu but I wish it responded faster.

---

