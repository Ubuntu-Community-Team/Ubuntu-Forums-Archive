---
title: "Ubuntu, Fonts, LCD, what to do :-("
date: 2006-08-03
forum: Desktop Environments
---

### Post by Jabran Asghar on 2006-08-03
Hi,

I know I am not putting a new topic in this thread, but ...

Has anyone some "working" observations/notes/reference/tips to improve fonts display and reduce overll font size (10) in Ubuntu 6.06 when using a LCD?

I have already tried some other threads which say finetuning DPI and some things in xorg.conf etc., but that did not work to my satisfaction.

I am using 1280x800 (wide, LCD) resolution on Dell 6400 laptop (ATI x300) and 1280x1024 on desktop (LCD) (GeForce 6800). 

I know many like ubuntu fonts, and some do not. So I already declare that Ubuntu Fonts are very good on CRT, but am eager to know if someone really worked it out to have small and "nicer" looking fonts on LCDs :-), Comeon everyone, this must be possible, shouldn't it be??

Jabran

---

### Post by The Keeper on 2006-08-03
Here's what I did.

Go to console and type:
sudo dpkg-reconfigure fontconfig
First select "native" and then "always" and finally "no".

Then go to System > Preferences > Fonts > select subpixel smoothing.

Then read this post:
[http://ubuntuforums.org/showpost.php?p=16896&postcount=1](http://ubuntuforums.org/showpost.php?p=16896&postcount=1)

---

### Post by jase on 2006-08-03
I just followed the steps in this thread:

[http://www.ubuntuforums.org/showthread.php?t=180647](http://www.ubuntuforums.org/showthread.php?t=180647)

..and it worked really well on my Dell 6400 (although I have the 1680x1050 screen).  The fonts are beautifully antialiased, and match or beat Windows now.

---

### Post by Johan! on 2006-08-03
I used [this]("http://www.ubuntuforums.org/showthread.php?t=208396") how-to.

I like it.

---

### Post by Jabran Asghar on 2006-08-04
> **The Keeper said:**
> Here's what I did.

Go to console and type:
sudo dpkg-reconfigure fontconfig
First select "native" and then "always" and finally "no".

Then go to System > Preferences > Fonts > select subpixel smoothing.

Then read this post:
[http://ubuntuforums.org/showpost.php?p=16896&postcount=1](http://ubuntuforums.org/showpost.php?p=16896&postcount=1)

I tried this one, but could not notice much improvement. Some fonts became bold unnecessarily. Not sure what may be wrong with Ubuntu configuration on my side as in the original thread (mentioned above) lots of users seemed quite satisfied by results of this procedure.

Tonight I shall try the other two options suggested in the abovereplies  to compare results and then shall post back.

---

### Post by mafitzpatrick on 2006-08-05
I have reduced font size to 8.5 for all except Window Title, which is set to 9 (although 10 is pretty indistinguishable).

I used 8.5 as it appears the same as 8pt, but aligns better (e.g. Applications, Places, System appear in the middle of the bar, rather than offset upwards a little).

All this is just through System > Preferences > Fonts.

All fonts apart from fixed width are set to Sans (Bold for Window Title), and Subpixel Smoothing (LCD) is switched on.  DPI setting to 96dpi.

---

### Post by Jabran Asghar on 2006-08-07
Well, have tried other options as well, but not a statisfactory result ](*,) Its not that fonts are very bad :rolleyes: , but they are not just upto when I compare to windows. May be If I dont start windows for a month or so then I will get use to it, but thats not gona work for me as I use windows at my work place.

So, will keep lloking for improvements, may be will also try downloading Live CDs of other distros just to see if its just ubuntu or others have the same effects, but for time being I am Ubuntu addicted.

And yes, if anyone comesup with some new thought to improve fonts on LCDs, do let everyone else know :-)

Jabran

---

### Post by der_joachim on 2006-08-08
The Nvidia driver has some options built in to improve font rendering. I do not know about Ati, though.

---

### Post by Jabran Asghar on 2006-08-15
> **der_joachim said:**
> The Nvidia driver has some options built in to improve font rendering. I do not know about Ati, though.

Hi, on desktop I have Nvidia Geforce 6800. Can you please share what are the settigns for Nvidia?

Also I heard of "Freetype" fonts (heard to be reverse engineering of ClearType, but not sure ...)? Does anyone know how to install/configure and optimize FreeType for LCDs on Dapper?

---

