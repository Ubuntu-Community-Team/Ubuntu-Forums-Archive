---
title: "X Window System - Is it the problem?"
date: 2009-04-29
forum: Desktop Environments
---

### Post by juantao on 2009-04-29
For more than 10 years I get excited at each new release of my favorite distro. From RedHat Hurricane 5.1 > Mandrake > Debian to today's Jaunty Jackalope. 'Maybe this time, X will be able to render fonts like the other computer systems' I tell myself. But,no. Each time I'm disappointed again. 

The fat, crayon-like menu headings that are default on every Gnome and KDE desktop I've ever seen, send me right back to Microsoft. 

Not that I wouldn't LOVE to thumb my nose at the evil empire. I want open-source to take over the world, in more than software and the tricks I can do with compiz and the customization available in all things Linux are *almost* worth looking at these ugly, ugly fonts. It's kinda like people that hunt. They always say 'Venison the way my wife fixes it, is good as steak' but it turns out to be just more shoe leather. Everyone says 'If you just configure your font-settings like I do, looks just as good as Winders' but they must need new glasses... Here's a side-by-side picture. Tell me again how to make the one on the right look like the one on the left (File Edit View - The red text 'Download' under Get Ubuntu) and I'll bake you a cake!

Maybe what we really need to do is completely scrap the X Window System and start over(?) Pic > [http://serveronthewall.com/compare.png](http://serveronthewall.com/compare.png)

---

### Post by kerry_s on 2009-04-30
system> preferences> appearance> fonts

i think you check best contrast. if you install the microsoft fonts you can set the fonts to those to get a even closer look.
look in synaptic for the fonts, i think it's called ttf-mscorefonts.

on mine i set the all to arial and use verdana for monospace.
i'm on my other machine i can only show you firefox.

---

### Post by juantao on 2009-04-30
Thank you kerry_s - but... I installed the mscorefonts and chose arial for all, still not thin and crisp. 

It's the crisp, distinct sharp edge that is inherent in MS and MacOS fonts that seemingly cannot be achieved in X

I've been dinking around with this for a decade on dozens of machines - dual-booting many of them and the difference is always there.

The one that comes close is Sawasdee, which is thin, but still has some bit of blur or shadow. 

It's just pixels on a screen. How hard can it be?

Here's another screenshot :

---

### Post by kerry_s on 2009-04-30
have you tried changing the dpi?

anyways here's what my setting looks like in gnome.

---

### Post by juantao on 2009-04-30
Thank you for posting your screenshot. However... Look at the 's' at the end of 'Best Shapes' There is shadow or bleeding in the middle of that letter (and other examples throughout).

My point is... I think there is something inherently lacking in the X Window System. There seems to be no possible way to match the crispness of character rendering of MacOS or MS Windows in X. This is true of Solaris, FreeBSD and all the Linux distros I've seen.

For me, it's a show-stopper and it's heart breaking. I want to use Ubuntu for my desktop - all my desktops, not just my servers, but I can't stand looking at it for more than a few days.

Somebody (probably lots of somebodies) PLEASE... Fix X !!

---

### Post by kerry_s on 2009-04-30
:lolflag: the fonts are fine to me, but if your that picky, give it another year and try again.

---

### Post by PacSci on 2009-05-01
If this is really that big of a deal, learn to code and implement it yourself, or hire a programmer to implement it for you. That's why it's open source.

A great deal of the progress Linux has made in the past fifteen years has been due to the X Window System. If we scrap it now, it would set Linux back a minimum of five years. And for those five years you would have *no* font rendering.

I've never noticed a difference, though. Ever. At least, not until you pointed it out. When you've got an operating system that is fast, stable, free, and fun, font rendering shouldn't really be that much of an issue.

---

### Post by juantao on 2009-05-03
One guy (me or anybody else) is not going to re-write X by himself - But it is going to be replaced by something better sooner or later,but it's gong to take many, many hours to re-write it.

By the way - asking for improvement should not merit a 'go fix it yourself' response. 

X is 25 years old - written in the days when your dumb terminal connected to a mainframe (it's client-server based [waste] rather than stand-alone like a all other modern systems). 

X is out dated, wasteful and incapable (apparently) of drawing a fine line. I'll be glad when it's is brought into the modern age, that's all...

---

### Post by kowspot2000 on 2009-05-08
Did some research and found a solution to your problem:

Ubuntu tries to do this anti-aliasing thing with the fonts to make them smoooooth. However, the result is just a fuzzy and ugly font that will give you a headache if used for too long. Ubuntu, for legal reasons, does not include any of the TrueType Windows fonts that just about every webpage uses, so you'll notice a lot of webpages, perhaps even your own, do not look right. The steps below will explain how you can install the Windows fonts and turn off the default Ubuntu anti-aliasing feature so everything looks good.

   1. There is a great thread about how to do this on the Ubuntu Forums. But I'll outline process here.

   2. First download the fonts package from [http://www.osresources.com/files/centos-windows-fonts/msfonts.tbz]("http://www.osresources.com/files/centos-windows-fonts/msfonts.tbz") and unpack the file as so.

      sudo tar xvjpf msfonts.tbz -C /usr/share/fonts/truetype/

   3. Now you have the fonts installed, you need to download some XML files to make them function. Download the file from [http://www.osresources.com/files/centos-windows-fonts/fontconfig.tbz]("http://www.osresources.com/files/centos-windows-fonts/fontconfig.tbz"). And extract the files to /etc/fonts/

      sudo tar xvjpf fontconfig.tbz -C /etc/fonts/

   4. Now reboot and enjoy your new fonts. I also opted to change my default system fonts to Tahoma using the System > Preferences > Fonts tool. I guess I still have a little Windows in me :) 

- Source "http://toddnelson.net/?page=ubuntu6"

Here's a screen of what the new fonts will look like:
[IMG]http://img412.imageshack.us/img412/6972/ubuntu5ui.png[/IMG]


Hope it Helps!

- Tuna

---

