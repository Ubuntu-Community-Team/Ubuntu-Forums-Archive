---
title: "Compiz / XGL / Beryl on Edgy 6.10"
date: 2006-10-14
forum: Desktop Environments
---

### Post by danran on 2006-10-14
Hi, I'm not sure what the difference between XGL and beryl is but i'd sure like to get the 3d desktop working.  It looks freaking awesome.  I'm using an Nvidia Geforce 5200 on Ubuntu Edgy 6.10.  I need a clear, concise, and up-to-date guide on how to get this working.  Can anyone help me out please?  Thanks in advance!  :o

---

### Post by galileon on 2006-10-14
[http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

---

### Post by danran on 2006-10-14
> **galileon said:**
> [http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

Ahhh, thank you galileon.  That was exactly what I was looking for.  In particular, for my setup, I used this guide([http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)) and I had it up and running in no time.  Unbelievable!

Thanks.

--Dan W.   :mrgreen:

---

### Post by galileon on 2006-10-14
im going thru a self-imposed sabbatical holiday from tweaking my linux box until edgy is released!! ill give it a try when the time comes..

edit: is there the aiglx already? if so, we can then use divx codecs and GL programs while using compiz...

---

### Post by alejandrops on 2006-10-14
hi, i've followed the wutorial in 
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)
but when I enter the new created XGL session it bouce back (after a while) to GDM screen.

any idea?

---

### Post by IronMan7491 on 2006-10-14
You shouldn't need to use XGL in Edgy.

---

### Post by alejandrops on 2006-10-14
I have an Ati x1400, so XGL is the only way to go :(

---

### Post by Happydude123 on 2006-10-15
What is the best way to get the 3d desktop [compiz/beryl + aiglx/xgl] for an ati 9200?

What driver should I use with xorg 7.1.1 or edgy?

---

### Post by russianpirate on 2006-10-15
> **Happydude123 said:**
> What is the best way to get the 3d desktop [compiz/beryl + aiglx/xgl] for an ati 9200?

What driver should I use with xorg 7.1.1 or edgy?

Obviously beryl cause your video card doesnt affect the choice of window manager. However, I would choose to use aiglx since its included with X 7.1+, but the person above posted that he could only get XGL working with his x1400.. so you might try that (gotta disable air-core first somehow..)

PS: Andrew, also search "GLXWithComposite" somewhere on forums or wiki cause I read that you need that enabled to get GL and Composite to work :D

---

### Post by alejandrops on 2006-10-15
I solved my problem. One package missing.

thanks

---

### Post by fated on 2006-10-25
> alejandrops  	I solved my problem. One package missing.

thanks
how did you configure your AIGLX to run compiz? I have a ATI X1400 too and every time i try to configure the xorg.conf file as written in the tutorial [http://gandalfn.wordpress.com/howto-compiz-aiglx-on-edgy]("http://gandalfn.wordpress.com/howto-compiz-aiglx-on-edgy")
or []("http://ubuntustorm.wordpress.com/2006/10/15/edgy-aiglx-ati-9600-xt")
it fails and I have to reset it from single user mode.

---

