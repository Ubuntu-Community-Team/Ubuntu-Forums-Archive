---
title: "How to make the Gnome interface lighter on older machine?"
date: 2005-05-10
forum: Desktop Environments
---

### Post by ciegalo on 2005-05-10
Hi to all,
I've successfully installed Hoary on my Celeron 700 w/ 128Mo RAM. Works fine, and thanks to the help of other forumers I'm getting close to successfully installing LAMP. 

Yet... This machine is pretty old and responds quite slowly. Can't add RAM as it's old SDRam, hard to find. 

Is there any "eye candy" function I could disable? Under Windows XP I can get rid of font anti-alias, various shadows etc. What would you suggest to make the window manager "lighter"? 

Thanks in advance !
Ciegalo

---

### Post by derrick1985 on 2005-05-10
[QUOTE=ciegalo]Hi to all,
I've successfully installed Hoary on my Celeron 700 w/ 128Mo RAM. Works fine, and thanks to the help of other forumers I'm getting close to successfully installing LAMP. 

Yet... This machine is pretty old and responds quite slowly. Can't add RAM as it's old SDRam, hard to find. 

Is there any "eye candy" function I could disable? Under Windows XP I can get rid of font anti-alias, various shadows etc. What would you suggest to make the window manager "lighter"? 

Thanks in advance !
Ciegalo[/QUOTE]

Regretably, Gnome is pretty much "it's as good as it gets" in terms of performance. Have you tried a lighter weight Window Manager like XFCE4? I use that on an even older machine, a Cyrix II 350mhz with 128mb Ram, and that runs farily decent considering.

---

### Post by defkewl on 2005-05-10
I agree. I think that Gnome by default is already heavy. Try using other WM such as window maker, enlightenment, blackbox, fluxbox etc. Good luck ;)

---

### Post by DaturaX on 2005-05-10
I used to run gnome on a PII 233mhz with 192MB RAM. It'll crawl like a snail. But I recently installed XFCE4 and it works like a charm. And yes, it frees up memory too. XFCE only takes 40MB unlike gnome which takes up 80MB on my box.

Cheers

---

### Post by tread on 2005-05-10
Don't use a pixmap oriented theme: use something like the gnome theme called "simple". Changing the icon theme might help too .. I think svg would take less memory (but I am just guessing, it would be better to experiment :))

Turn off thumbnailing in nautilus.

You can change antialiasing options in System->Preferences->Font.

Fire up Applications->System->Configuration Editor and go to "desktop->gnome".
Browsing through it you will see some options like "thumbnailers->disable_all" which might make Gnome faster.

---

### Post by ciegalo on 2005-05-10
Hi all,
Thanks for these pointers !

I'd already heard about XFCE when I tried a distribution for "compusaurus" (my best shot at "ordinosaure"  ;-) ) . 

I guess I can "synaptic" this WM ? I'll try that right now.

A pity though, because I was getting used to Gnome and it's great menu bar. 

Thanks again !
Ciegalo

---

### Post by h2gofast on 2005-05-10
[QUOTE=ciegalo]Hi to all,
I've successfully installed Hoary on my Celeron 700 w/ 128Mo RAM. Works fine, and thanks to the help of other forumers I'm getting close to successfully installing LAMP. 

Yet... This machine is pretty old and responds quite slowly. Can't add RAM as it's old SDRam, hard to find. 

Is there any "eye candy" function I could disable? Under Windows XP I can get rid of font anti-alias, various shadows etc. What would you suggest to make the window manager "lighter"? 

Thanks in advance !
Ciegalo[/QUOTE]
 try apt-get install fluxbox.

---

### Post by fng on 2005-05-10
[QUOTE=ciegalo]I guess I can "synaptic" this WM ? I'll try that right now.[/QUOTE]

look for **xfce4** (=version 4.2.1) **not xfce** (=version 4.0)

---

### Post by az on 2005-05-10
"Can't add RAM as it's old SDRam"

Huh?   Have you ever searched ebay?  I just bought a 128 meg pc100 stick for 13 dollars canadian.

You have a pretty fast machine.  I think that ram is your main problem.  Gnome should be running at least as fast, if not faster than windows on a 900 Mhz machine.

---

### Post by shakin on 2005-05-10
[QUOTE=ciegalo]I'm getting close to successfully installing LAMP. [/QUOTE]

Curious, what's so hard about installing LAMP?

```

$ sudo apt-get install mysql-server
$ sudo apt-get install apache2-mpm-prefork
$ sudo apt-get install php4
$ sudo apt-get install php4-mysql

```

Then browse to [http://localhost/](http://localhost/)

If you do a search in Synaptic for "php4" you'll find a lot of other modules you can install, like pear, mcrypt, imap, gd, etc.

---

### Post by ciegalo on 2005-05-10
Hi,
Just synaptic'ed (like this one  :) ) XFCE 4.2. Pretty fast indeed ! Rather more comfortable than Gnome... Just took me a couple minutes to figure out that I had to restart my session  ;)  Thanks for the info ! I'll try fluxbox too. 

>Azz :
13$Ca ? Well, around here I could get some for about 20 euros, but quality is generally poor (ie stick out of order). I'm currently looking around my friends et al to get a couple chips. 

> Shakin :
*Getting* LAMP is easy, incredibly so through the magic of synaptic (once you extend the repositories). *Configuring* it is another challenge, especially when one comes from ol' IIS and it's (ugly by easy) GUI, and from the Windows world with "root" rights all over... ROFL! 

Thanks to another post (yours BTW and another), I found how to set up the default site (to a directory I have rights on) and create a password for mysql. Now everything works fine. Last thing I have to fix is my windows xp that can't connect to my samba shares (asks for a password). I'll be searching the forums tomorrow, now's the time to feed the kiddy-cat and put my little neuron to bed ;)

Cheers to all & a good night to all men, women & other creatures of good will !
Ciegalo

---

### Post by ben72 on 2005-10-26
What if I want php5 and still have mcrypt? Does the php4 version work then?

php4-mcrypt - MCrypt module for php4

I can't find any php5 version. And for pear is it now just called php-pear? I can't find any php5-pear...

Thanks for any help! I'd like to install vhcs and php5 on breezy..

---

