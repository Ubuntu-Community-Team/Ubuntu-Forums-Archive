---
title: "Compiz Fusion Install Issues--Yet another lost sould"
date: 2007-09-10
forum: Desktop Environments
---

### Post by besidethewoods on 2007-09-10
I have just started this week using Ubuntu and working on reforming from my evil Windows ways.  I'd like to install Compiz Fusion (or a comparable 3D environment).  I attempted to using this [http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/) guide.  As I proceeded through the instructions provided I have noticed one error after the "sudo aptitude -y update" instruction that says:

Ign [http://dl.sourceforge.net](http://dl.sourceforge.net) ./ Release.gpg                                    
Ign [http://dl.sourceforge.net](http://dl.sourceforge.net) ./ Translation-en_US
Ign [http://dl.sourceforge.net](http://dl.sourceforge.net) ./ Release
Ign [http://dl.sourceforge.net](http://dl.sourceforge.net) ./ Packages
Ign [http://dl.sourceforge.net](http://dl.sourceforge.net) ./ Sources
Err [http://dl.sourceforge.net](http://dl.sourceforge.net) ./ Packages
  302 Found [IP: 193.190.198.97 80]
Err [http://dl.sourceforge.net](http://dl.sourceforge.net) ./ Sources
  302 Found [IP: 193.190.198.97 80]
Fetched 4B in 2m1s (0B/s)
Reading package lists... Done

I get through everything else just fine but when I try type compiz --replace in the command window nothing happens except it tells me:

nick@Fitz-William:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
nick@Fitz-William:~$ 

I have a Dell/Pentium 4 3 GHz and an ATI x600 pro graphics card.

I know ATI doesn't seem to play nice with linux but if someone could help I'd surely appreciate it.

Thanks for reading.

Nick

---

### Post by Happy_Man on 2007-09-10
So.... did you install the fglrx drivers and an XGL session and try running Compiz from that?

---

### Post by besidethewoods on 2007-09-10
No I don't believe I have, but thanks for the idea.  I'll give it a try in a bit and post the results.  Like I said I'm new to the world of linux so I'm still learning.  Thanks for helping.  :)

---

### Post by mtbsoft on 2007-09-11
I'll be honest, after four different attempts (and associated rebuilds), I've given up on getting Compiz working with my ATI X1400 and have gone back to Beryl which works fine.  If you don't get anywhere with Compiz, I can send you a couple of links which work fine for my Inspiron 9400.  (if you do, can you let me know how!)

---

