---
title: "Smallest aptitude (apt-get) enabled distribution"
date: 2009-04-16
forum: General Help
---

### Post by willz06jw on 2009-04-16
Hi,

I am running a vintage computer and I am looking for the smallest (by hard drive space needed) and lightest (by ram used and cpu power needed) Linux distribution **that has aptitude (apt-get) fuctionality**.  

Thanks for your help,
Will

---

### Post by bytor4232 on 2009-04-16
You can use Ubuntu, you just can't install a full desktop environment, and need to do a lot of tweaking at the command line.  It requires a LOT of hacking, but its very satisfying.

Here is my blog detailing how I got Ubuntu working, and working well, on a Compaq Presario 700 (500 mhz athlon, 256 megs of ram):

 [http://leanubuntu.blogspot.com/](http://leanubuntu.blogspot.com/)

I loved using my Compaq so much, I installed it on my other Laptop, and it screams.  My Acer Aspire Gemstone (Celeron 1.7, 2 gigs of ram) boots in 13 seconds to login, and starts my xfce4 desktop in 9 seconds.

Depending on how "vintage" your PC is, my lean method should work for you.

---

### Post by willz06jw on 2009-04-17
I am currently using 9.04 alternate install command-line-only Ubuntu .... with lwm used as my window manager (when needed).  I currently am using a more vintage computer than you -- a 333Mhz Celeron with 64MB RAM.  I enjoy using very old PCs and trying to push the most out of them (dos gaming, web browsing, coding, etc)...but I keep wanting older(more vintage) ones!  I am afraid that I am at the limit of vintagability for Ubuntu.  This is because that if I have any less RAM the alternate install won't even work (I have read).  

But back to what I am trying to coax out of ya.  I am trying to find a more vintagable apt-get enabled distribution to keep up my challenging passtime.  

Note to anyone who wants to try this:  you have to enable control-alt-backspace to exit out of many of these ultra light WMs.  Also, the best low-CPU&RAM-footprint javascript-enabled browser I found was Epiphany.

Thanks for your help,
Will

PS: Also any more ideas of words I can combine with vintage would be a big help

---

### Post by bytor4232 on 2009-04-17
I was afraid of how far back you wanted to go!  Yeah, I threw out everything older than a Pentium a long time when my family moved.  My collection was getting out of hand.  I kept all my AMD Duron and Athlon hardware though, I have enough equipment to build six machines if I wanted to, just don't have a need for them right now.  Everything I have running in my house is Pentium 4 or Pentium D, or a laptop.  My vintage Compaq Pentium 100 mhz laptop died a few years ago, which replaced a Tandy laptop which died a few years before that. 

I would suggest Debian, but from what I understand the Alternate Installer is just the Debian Installer.  I'm afraid going lower than 64 megs of RAM might not work out for you if your wanting to stay in the apt world.

---

### Post by anjilslaire on 2009-04-17
Check out DSL, it's debian/apt-based
[http://damnsmalllinux.org/](http://damnsmalllinux.org/)

---

### Post by willz06jw on 2009-04-17
I have tried DSL and I was impressed.  I didn't think you could upgrade the OS or add things via APT and have them be there after you restart.  Hmmm.  

Thanks,
Will

---

### Post by sdennie on 2009-04-17
If you actually install DSL and not just run it, you can do all those things.  It's a bit misleading in that it's a live disk.  It can also be installed though.  (And will likely be much faster for having done so).

---

### Post by ddrichardson on 2009-04-17
> **willz06jw said:**
> Hi,

I am running a vintage computer and I am looking for the smallest (by hard drive space needed) and lightest (by ram used and cpu power needed) Linux distribution **that has aptitude (apt-get) fuctionality**.  

Thanks for your help,
Will
+1 for DSL - I installed it on a Pentium 133 with 32Mb of RAM. Firefox is obviously a non-starter but Dillo works fine. You need to specify a fair amount of swap file too.

It doesn't have package management as such but has install scripts and frankly, depending on the specs you wouldn't be installing vanilla packages anyway.

---

### Post by timcredible on 2009-04-17
puppy linux works great on the old 128MB pc a relative has, and it has a repository program for adding more apps.  keep in mind that puppy and dsl won't have all the apps that ubuntu has because things like openoffice require too much memory.

---

### Post by tokico on 2009-04-17
> **willz06jw said:**
> 
Note to anyone who wants to try this:  you have to enable control-alt-backspace to exit out of many of these ultra light WMs. 

How can I do that? Enable Ctrl-Alt-Backspace?

---

### Post by sdennie on 2009-04-17
Actually, Ctrl-Alt-Backspace has to be explicitly turned off to NOT work.  It's a kill switch that works unless you go out of your way to disable it.

---

### Post by ddrichardson on 2009-04-17
> **sdennie said:**
> Actually, Ctrl-Alt-Backspace has to be explicitly turned off to NOT work.  It's a kill switch that works unless you go out of your way to disable it.
Its now the other way around in the most recent versions of Xorg - Jaunty has disabled it too. Magic keys still work though.

---

### Post by sdennie on 2009-04-17
> **ddrichardson said:**
> Its now the other way around in the most recent versions of Xorg - Jaunty has disabled it too. Magic keys still work though.

That's unfortunate.  The "DontZap" option in xorg.conf used to be a joke.  Why it's the default now is beyond me.

---

### Post by ddrichardson on 2009-04-17
> **sdennie said:**
> That's unfortunate.  The "DontZap" option in xorg.conf used to be a joke.  Why it's the default now is beyond me.
Yes, it came as a surprise to me too

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/90434](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/90434)

---

### Post by tokico on 2009-04-17
> **ddrichardson said:**
> Its now the other way around in the most recent versions of Xorg - Jaunty has disabled it too. Magic keys still work though.

Since I'm a kind of a newbie, I have 2 questions:

How can I enable Ctrl-Alt-Backspace in the newers Xorg versions?

and

What are the "magic keys"? Is it "Raising Skinny Elephants Is Utterly Boring"? :D

---

### Post by ddrichardson on 2009-04-17
> **tokico said:**
> Since I'm a kind of a newbie, I have 2 questions:

How can I enable Ctrl-Alt-Backspace in the newers Xorg versions?
Setting the dontzap option to false in Xorg.conf I'd have thought - although I haven't checked (I'm on an Arch system at the moment).
> **tokico said:**
> What are the "magic keys"? Is it "Raising Skinny Elephants Is Utterly Boring"? :D
Yes, although I always remembered it as **R**eboot **E**ven **I**f **S**ystem **U**tterly **B**roken.

---

### Post by tokico on 2009-04-17
Thanks, then.

---

### Post by willz06jw on 2009-04-20
To enable the Control-Alt-Backspace combination just follow the directions on the below link.

Note: This information was written for Ubuntu 9.04 (Jaunty)

[http://ubuntuforums.org/showthread.php?t=1108971](http://ubuntuforums.org/showthread.php?t=1108971)

Have a good one,
Will

---

