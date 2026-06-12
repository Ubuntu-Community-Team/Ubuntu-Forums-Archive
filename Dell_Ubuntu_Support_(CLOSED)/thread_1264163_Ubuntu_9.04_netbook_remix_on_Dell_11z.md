---
title: "Ubuntu 9.04 netbook remix on Dell 11z"
date: 2009-09-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bsawers on 2009-09-11
I have a Dell 11z, which means installing from a thumb drive.  The netbook remix lists Atom processor as requirement, but the 11z has the Celeron 723.

Can I install the netbook remix?  Also, will I miss out on anything?

Thanks in advance for your help.

---

### Post by ugm6hr on 2009-09-12
> **bsawers said:**
> The netbook remix lists Atom processor as requirement

Really?

9.04NBR is a standard i386 kernel (not lpia).

I have used it to install a number of computers; it works fine.

---

### Post by snowpine on 2009-09-12
> **ugm6hr said:**
> Really?

9.04NBR is a standard i386 kernel (not lpia).

I have used it to install a number of computers; it works fine.

Yup, that annoying piece of misinformation has been on the download page since day 1, see for yourself:
[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)

(right hand column)

---

### Post by bsawers on 2009-09-12
I suspected as much, but I wanted to check beforehand.  I'm no computer expert.  Thanks for the confirmation.

Secondly, am I missing anything if I use the netbook remix?  Also, does anyone have any experience with the 11z?  Expected problems, etc.

Thanks again

---

### Post by Untergeher on 2009-09-13
Hi,

it will work. By the way, you can always try out things before installing just by running Ubuntu without installing it. It lists it as an option in the start menu once you started up from the usb-drive. I have the 11z too. With 9.04 I can not get the ethernet to work. I installed 8.04 and everything (except the webcam) worked out of the box. Also, if you happen to get sound problems, refer to the following link [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695). Just follow the directions.

I am using 9.04 at work. The netbook remix has a slightly different 'touch', things look not the same. I'd prefer the desktop version. I installed it using an external cd-rom drive. If you don't have one, you can create a bootable usb-stick with the desktop verion on it.

Good luck,
Der Untergeher

---

### Post by ugm6hr on 2009-09-13
NBR lacks a handful of applications, and uses the netbook interface.

Easy enough to add any components you want (and remove).

---

### Post by bsawers on 2009-09-15
Thanks for all the replies.  Is there anywhere to see screen shots for desktop and the netbook remix to see the differences?

Untergeher, did the wireless work with 9.04?  Otherwise, it sounds like I shouldn't bother with 9.04 and just install 8.04.

---

### Post by swallisa on 2009-09-16
I would have to concur with the others just upgraded my 10V and it's working just dandy.  Oh and also went from 8.04.2 which is also supposed to be a no no.

---

### Post by ohiomoto on 2009-09-17
I'm running it on the Acer AS1410 (and since I liked it so much, I put it on my Dell Vostro 1400 too!)  It installed perfectly right out of the box, but I needed to switch my BIOS SATA driver from AHCI to IDE.  If it runs fine on the USB but hangs on boot after installing, you might want to keep that in mind.

UNB is awesome.  WAY snappier than MS Shitsa. My only complaint is that is seems to use more power and battery life is a little shorter than I would like. I might need to tweak something.

---

### Post by bsawers on 2009-09-20
UNB = Ubuntu Netbook?

MS Shitsa = Microsoft [swear word]?  Windows?

I really need to use Office 12 for work.  Does Wine work better with either of these?

Also, anybody use gOS.  I read some nice reviews.

---

### Post by ugm6hr on 2009-09-20
If you need MS Office 2007, make sure you read the wine website for details.  Crossover Office is considered a valuable investment for MS Office users, although it can be made to work with wine.  There are a number of how-tos here on this forum too.

I understand that Word, Excel and Powerpoint all work fairly well.  However, if this is imperative, you may find it easier to stick with MS Windows.

As for gOS, it comes in a number of different versions, and is now essentially Ubuntu with a different look and wine preinstalled.  I don't see any useful benefits over Ubuntu itself.

---

