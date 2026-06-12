---
title: "Dell XPS 1530 Ubuntu Installation"
date: 2008-09-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by chamkaran on 2008-09-03
Hi everyone,
I am having Dell XPS 1530 but can't install Ubuntu.
Initially it starts good when it comes to the partition it can't format the drive nor can makes any new drives.I tried with both version of ububtu 7 and 8. Is it correct might it don't have the SATA drivers or ?
Yours help will be highly appreciated.

Regards

---

### Post by jwalker on 2008-09-03
G'day mate

Not sure what you're harping on about? I got a 1530 here in the UK about two months back, came preinstalled with Vista, I put Ubuntu (64bit) on straight away. This required a bit of partitioning and I had no grief at all. Later I decided 64 bit was not ready for the 1530, so I dropped down to 32 bit. Again I had no troubles. 

What version of Ubuntu are you trying? Where did you get your laptop (what country)? Have you tried calling Dell? Ha ha just joking on that last one, this forum is your best bet for help. 

The laptop requires a few tweaks when you finally get Ubuntu installed, but you should like it, I do.

---

### Post by chamkaran on 2008-09-03
Hi 
Thanks for quick response.
I am also in the UK and bought it roughly 4 months back.i have vista home edition.
i want to install ububtu 7 or ubuntu 8 32bit.
Even in vista by disk management tool it does't allow me to make the third primary drive as i got 120 gb hard drive.

Regards

---

### Post by OffHand on 2008-09-03
By default it already uses 3 primaries. A small hidden tech troubleshoot partition and one that I think is called media direct or restore (I forgot). So that gives you only room for one more primary. You gotta work with a few logical partitions.

---

### Post by putz3000 on 2008-09-03
I have this same laptop (purchased with Vista Ultimate) and have had no trouble installing Ubuntu 32-bit on it.  But, I used the vista disk utility to shrink the drive.  Then I booted from live cd and selected install.  When the option was available I told it to install to largest unallocated space.  Everything went smooth from that point on.  I can still dual boot, vista boot option was not lost in the process. 

I also have an older HP that has vista home on it and I had previously installed Ubuntu 7.10 on that one using the same approach.

---

### Post by laurence91 on 2008-09-03
I would suggest reading a few Dual boot posts before you do anything, i read and read for weeks before i completed my dual boot on Vista / kubuntu.

Its not as easy to dual boot on the dell xps m1530 as other laptops due to Media Direct.

For starters the partitioning requires some thought, in the factory state mine already had 3 primary partitions and an extended, a dell utilities (47mb) a windows restore (approx 10gb) a windows home (230gb) and a 2gb extended with 2gb logical for media direct.

If you install over the media direct partition and grub ends up in the MBR then the media direct key (looks like a house) bricks your laptop when pushed.

I started by using WUBI a non invasive windows installer, and played around with kubuntu first and learnt how it works. How to change settings in the konsole etc first.

Then i (backed up as you will lose everything) zeroed the hardrive and reinstalled the dell utilities (i figured its only 47mb and it contains the dell splash screen etc...... if i take away all of laptops history it might not forgive me when it grows up...)

and created a windows home, Linux root, home + swap (the home and swap being on an extended partition.). Then using one of the widely available guides i reprogrammed the media direct key to start Linux leaving the normal power button for windows.

Needless to say i suggest you research exactly what you want first. Its not all straightforward, thankfully mine works perfectly despite a few bugs. I actually hardly use vista anymore..... if ever. But its all about planning your own install.

heres some suggested reading (sorry i work at a university!!....)

[https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530)
[http://linuxevangelist.blogspot.com/2007/10/dual-boot-in-dell-xps-m1330-with.html](http://linuxevangelist.blogspot.com/2007/10/dual-boot-in-dell-xps-m1330-with.html)
[http://www.youtube.com/watch?v=bTEc601aXVc](http://www.youtube.com/watch?v=bTEc601aXVc)
[http://www.blog.iknition.net/2008/dual-boot-ubuntu-vista-usando-dell-mediadirect/](http://www.blog.iknition.net/2008/dual-boot-ubuntu-vista-usando-dell-mediadirect/)

Good luck

Laurence

---

### Post by chamkaran on 2008-09-04
Thanks for usefule Replys .

Regards

---

### Post by wajiguqu0223 on 2008-09-04
Now we've not only seen those people, but we've scholarly from them about how to create our games outdo."The inactivity to exhibit the[ lineage 2 adena ](http://www.ugamegold.com/c_Lineage2-Adena/)Bunk Beautify's highly expected Experience of Warcraft Miniatures Boardgame speedily approached the 2+ time deutschmark. So piece it was understandably the most anticipated job at the assemblage,

---

### Post by jespdj on 2008-09-04
My page: [http://jesperdj.pbwiki.com/Ubuntu+on+the+Dell+XPS+M1530](http://jesperdj.pbwiki.com/Ubuntu+on+the+Dell+XPS+M1530)

---

