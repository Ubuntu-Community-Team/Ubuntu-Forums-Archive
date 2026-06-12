---
title: "GnuCash UI"
date: 2006-06-29
forum: Desktop Environments
---

### Post by rkakkar on 2006-06-29
since GnuCash is an open source GUI app, it looks like crap on ubuntu (see screenshot). is there anyway i can improve/beautify it to atleast use the basic/default buttons provided by ubuntu?

---

### Post by neighborlee on 2006-06-29
what buttons are you talking about ?...if you want a pretty UI try kmymoney.

gnucash has alot more features, but no its not one of the pretty ones at all

cheers

---

### Post by ardchoille on 2006-06-29
[QUOTE=rkakkar]since GnuCash is an open source GUI app, it looks like crap on ubuntu (see screenshot). is there anyway i can improve/beautify it to atleast use the basic/default buttons provided by ubuntu?[/QUOTE]
GnuCash is still GTK1, while most apps are GTK2 which looks much better, so I don't see how you could beautify it much. This is the reason I refuse to use GTK1 apps. It's rather surprising that the GnuCash devs haven't moved to GTK2 yet.

---

### Post by ColinG on 2006-06-29
For me Kmoney is the better of the two anyway - for home use that is. 

Gnucash is a bit of a pig to work with imo but it is well featured if you really need full scale  double entry book-keeping.

---

### Post by ardchoille on 2006-06-29
[QUOTE=ColinG]For me Kmoney is the better of the two anyway - for home use that is. 

Gnucash is a bit of a pig to work with imo but it is well featured if you really need full scale  double entry book-keeping.[/QUOTE]
Yes, I run gnome, but I use KMyMoney.. it's best for home use, IMHO.

---

### Post by bsantos on 2006-07-01
GnuCash has released on 18/06 the first RC for 2.0.0. The one available on the reps is 1.8.12, still gtk1.

Just wait for a backport when 2.0.0 is released... :)

---

### Post by ColinG on 2006-07-01
I read something abour version 2 and the general thread seems to be it is a cosmetic enhancement in the main. The rather complicated workings remain the same and that, really, is the difference. For home use I don't need the complexities of Gnucash. 

Time will tell but thanks for the update :)

---

### Post by bsantos on 2006-07-01
You use what fits you best. :)

I've been searching for an app for this purpose, and while browsing gnucash site, the news stated 2.0.0 was near, and was already using gtk2. I've seen a couple of posters complaints regarding the ugly UI, so I thought it wouldn't hurt to mention. ;)

---

### Post by ColinG on 2006-07-01
I agree Bruno. Have you tried Kmymoney2?
Cheers:p 
Colin

---

### Post by farang.geek on 2006-07-02
Has anyone tried [Grisbi]("http://www.grisbi.org")?  I think its a great app and it uses GTK2

---

### Post by ColinG on 2006-07-02
Is there a Ubuntu deb out there? Loks very nice

---

### Post by bsantos on 2006-07-02
I haven't tried KMM2 yet, Colin, I'll check it out, and Grisbi too.

Grisbi 0.5.8 is in universe.

---

### Post by ColinG on 2006-07-02
[QUOTE=ColinG]Is there a Ubuntu deb out there? Loks very nice[/QUOTE]

Found the deb via synaptic. I'll give it a run!

Thanks
Colin\\:D/

---

### Post by ColinG on 2006-07-02
I've had a couple of seg faults already whilst Kmymoney is rock solid stable in my exoperience. I'll keep an eye on this one though as it could be a nice app.

---

### Post by GOwin on 2006-07-04
[QUOTE=farang.geek]Has anyone tried [Grisbi]("http://www.grisbi.org")?  I think its a great app and it uses GTK2[/QUOTE]

I do. I've been using it for over a year now. 

I see you're from Pasig. I live next to your city, Mandaluyong.

---

### Post by tonyr1988 on 2006-07-04
[QUOTE=ardchoille]Yes, I run gnome, but I use KMyMoney.. it's best for home use, IMHO.[/QUOTE]
As an Ubuntu (and Linux) newbie...how do you run KMyMoney in GNOME? I thought it was KDE-only.

---

### Post by ColinG on 2006-07-05
Just install Kmymoney via synaptic:

sudo apt-get install kmymoney2

Have fun:p

---

### Post by tonyr1988 on 2006-07-05
[QUOTE=ColinG]Just install Kmymoney via synaptic:

sudo apt-get install kmymoney2

Have fun:p[/QUOTE]
Wow...I feel stupid. I kind of assumed that KDE programs were KDE-exclusive, as with GNOME, XFCE, etc.

I have TONS to learn....

---

### Post by ColinG on 2006-07-05
Pleased to have helped a little :p

---

### Post by farang.geek on 2006-07-05
[QUOTE=GOwin]I do. I've been using it for over a year now. 

I see you're from Pasig. I live next to your city, Mandaluyong.[/QUOTE]

Nice to know someone here is within my vicinity (geographically that is)

---

### Post by m83 on 2006-07-05
I have been using [jGnash]("http://jgnash.sourceforge.net") since November 2005 and I must say it's great for home use. It's a Java application so it can run on any OS that supports Java (I've been running jGnash on Windows and Linux without any problem whatsoever).

For Linux you need to download the .jar package and to run it you need to start it like so: ```
java -jar jgnash.jar
```

The documentation is rather scarce, but [the forums]("http://sourceforge.net/forum/?group_id=27240") contain a lot of good advice from users and from the developers.

All in all I highly recommend jGnash as a very stable, portable and easy to use personal accounting application.

---

### Post by nico1278 on 2006-07-05
You can try also homebank ( [http://homebank.free.fr/](http://homebank.free.fr/) ).

---

### Post by kperkins on 2006-07-05
From what I've seen of homebank, it needs a lot of work to be much more than a check register, ie import of files other than CSV, account categories (ie--loans, investment, etc.). If you have simple needs, then it may be good for you.
Kmymoney looks good, but it had big problems importing qif files from the program I use.
Grisbi is good, but didn't have all the features that I needed, so I'm waiting to see how it comes along.
Gnucash is a monster, and ugly besides.  I tried installing 1.9.8, recently, to try it, but had problems and couldn't do it.  If you own a business, Gnucash is the way to go, though.
I'm using Moneydance ( [http://www.moneydance.com/](http://www.moneydance.com/) ) which has all the features I want, and need.  It is not open source, or free, but since it is java based, it works on all platforms, is extensible, and cheap.

---

