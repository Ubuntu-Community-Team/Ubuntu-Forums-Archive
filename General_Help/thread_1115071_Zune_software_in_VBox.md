---
title: "Zune software in VBox"
date: 2009-04-03
forum: General Help
---

### Post by ninjapirate89 on 2009-04-03
My desktop is currently dual-booted with XP and Linux Mint but I only use XP for my Zune software. I am wondering how well the Zune software would run through virtualbox. Does anyone have any firsthand experience with this? I would love to be able to remove Windows from my computer completely.

---

### Post by Nostalos on 2009-04-03
I do, and my experience is that its miserable.   Zune Software is a horrid resource hog anyway and under VBox is miserably so.    

But I can make a couple of suggestions.  

1.  Don't try to use VBox Shares for the Music folder.  Zune is slow, share makes it 3 times worse.   You should either copy it to the virtual disk or mount it on a USB drive.

2.  Make sure and setup a USB Filter in the Vbox setup. If you dont' the zune fail 50% of the time if you manually connect it to the Vbox system.  Filter makes it work much more reliably.

It can be done, and it will work.  But it will try your patience at times.  And the wife bought me the zune so going back to my iPod is not an option ;)

---

### Post by ninjapirate89 on 2009-04-03
I love my Zune but you are right the software is one of the biggest resource hogs I have ever used. That is why I was hesitant to just try it myself. I would hate to spend hours installing XP and updating it just to find out that it wasn't going to work well.

All of my media is on a 500GB external hard drive so I would definitely be using the usb option under VBox (if I even decide to try this)

Thanks for the input.

---

### Post by wolfen69 on 2009-04-03
> **Nostalos said:**
> I do, and my experience is that its miserable.   Zune Software is a horrid resource hog anyway and under VBox is miserably so.    


if you have enough system resources and allocate enough memory (and video memory) to xp, it should be no problem. i have done 3D gaming in virtualbox, so zune should be no problem. what are your system specs?

---

### Post by ninjapirate89 on 2009-04-03
All I can remember off hand is it has 1GB of RAM and a Intel Celeron processor (It's not a powerhouse I can tell you that). I guess I'll just leave XP on it. I usually use my laptop anyway so its not that big of a deal it's just that I would love to be rid of Windows.

---

### Post by Nostalos on 2009-04-03
> **wolfen69 said:**
> if you have enough system resources and allocate enough memory (and video memory) to xp, it should be no problem. i have done 3D gaming in virtualbox, so zune should be no problem. what are your system specs?

Has nothing really to do with system specs.  Zune Software is a POS and I do not mean Point of Sale ;)  Its really slow natively on my dual core with 3gigs of RAM.   Add in the delay of a virtual system along with things like the USB connectivity not being anywhere near as fast as native and its.   VBox is an awesome piece of software and is incredibly fast, but as with anything else its not as fast as native.  And when it already sucks natively.......

---

### Post by ninjapirate89 on 2009-04-03
Yeah the software is terrible. When I first bought my Zune I knew nothing of Linux and had no idea that I would ever desire to switch to it. Now I sort of regret buying it. The hardware itself is awesome though.

---

### Post by Nostalos on 2009-04-03
> **ninjapirate89 said:**
> Yeah the software is terrible. When I first bought my Zune I knew nothing of Linux and had no idea that I would ever desire to switch to it. Now I sort of regret buying it. The hardware itself is awesome though.

I feel your pain.  I use to think there was no software I despised more then iTunes.   Then my wife gave me this 80G zune.  Hardware is really nice for sure.  But I am praying for the day there is some 3rd party management software for it.

---

### Post by ninjapirate89 on 2009-04-03
> **Nostalos said:**
> I am praying for the day there is some 3rd party management software for it.

That would be the best solution but I wouldn't count on it happening any time soon (if ever).

---

### Post by superzorro on 2009-04-07
I am waiting for that also, but in the meantime I haven't had any trouble running Zune media player through XP and Virtualbox. The only lag I have is when you are looking for a cover, but is not much.

My experience is good.

---

### Post by jack frost on 2009-04-22
> **wolfen69 said:**
> if you have enough system resources and allocate enough memory (and video memory) to xp, it should be no problem. i have done 3D gaming in virtualbox, so zune should be no problem. what are your system specs?
 
 
what 3d gaming were you able to do in virtual box?  any windows live games?

---

### Post by tacantara on 2009-04-24
I've run into a problem with trying to put music files onto Zune and iTunes through the Virtual Box.  VB will recognize movies/video discs and data discs without any problem.  When I place a music CD in the drive, Windows responds with an error message stating that the CD is not readable/not in a Windows recognized format.  To counter this, I copy the music files to a USB external HD, and then I move the files into a Windows directory to be "discovered" by my Zune/iPod programs.  Does anyone know of a fix that will allow music CDs to be recognized, thus removing the need for the extra step?

---

