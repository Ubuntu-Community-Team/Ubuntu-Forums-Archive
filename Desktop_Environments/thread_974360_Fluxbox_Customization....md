---
title: "Fluxbox Customization...?"
date: 2008-11-07
forum: Desktop Environments
---

### Post by icanfly0307 on 2008-11-07
Hey there,
                   Last night, I went through the tedious process of reinstalling Ubuntu 8.04.1 via the internet. I basically installed the base system first and then dumped Fluxbox on top. So far, I've gotten my wireless, desktop icons, and transparency working. I'm trying out Rox Filer for my file manager but it seems a little too gaudy and unorganized when it comes down to copying, pasting, cutting, etc.

So, I was just wondering... what file managers would you recommend for Fluxbox. I want it to be quick, slick and look a bit like Nautilus.

Thanks for any suggestions... :lolflag:

---

### Post by baugen on 2008-11-07
thunar...

try xfe

i still use xwc and emelfm

---

### Post by icanfly0307 on 2008-11-07
> **baugen said:**
> thunar...

try xfe

i still use xwc and emelfm

I tried out thunar, BUT....

I can't get any icons for the folders. By icons, i mean the little folder pictures above the text. Do you have any idea why that's happening? 

Thanks again...

---

### Post by kerry_s on 2008-11-07
if you want it like nautilus, then pcmanfm.
sudo apt-get install pcmanfm

rox is the most powerful of the light filemangers, what are you having problems with? rox supports drag and drop for copy,move,link.

you'll also want to learn the customize menu. i have scrips which i just drag and drop. also take the time to put the program you want to use as root in the sudoers(visudo)
example:

you ALL=NOPASSWD: /usr/bin/rox, /usr/bin/leafpad, /sbin/shutdown, /usr/sbin/synaptic, etc...

then you can use sudo without needing a password.

changing the look of rox is just as easy, there's the right click set icon and the gtk method.

i use rox on jwm, just let me know what you want, a lot of us use rox and can help.

---

### Post by icanfly0307 on 2008-11-07
> **kerry_s said:**
> if you want it like nautilus, then pcmanfm.
sudo apt-get install pcmanfm

rox is the most powerful of the light filemangers, what are you having problems with? rox supports drag and drop for copy,move,link.

you'll also want to learn the customize menu. i have scrips which i just drag and drop. also take the time to put the program you want to use as root in the sudoers(visudo)
example:

you ALL=NOPASSWD: /usr/bin/rox, /usr/bin/leafpad, /sbin/shutdown, /usr/sbin/synaptic, etc...

then you can use sudo without needing a password.

changing the look of rox is just as easy, there's the right click set icon and the gtk method.

i use rox on jwm, just let me know what you want, a lot of us use rox and can help.

Thanks alot Kerry! PCMan FM was just what I was looking for. Loving Fluxbox so far... :guitar:

---

### Post by n2stc on 2009-02-09
> **kerry_s said:**
> 
you'll also want to learn the customize menu. i have scrips which i just drag and drop. also take the time to put the program you want to use as root in the sudoers(visudo)
example:

you ALL=NOPASSWD: /usr/bin/rox, /usr/bin/leafpad, /sbin/shutdown, /usr/sbin/synaptic, etc...

then you can use sudo without needing a password.

changing the look of rox is just as easy, there's the right click set icon and the gtk method.

i use rox on jwm, just let me know what you want, a lot of us use rox and can help.

I am looking for an easy way to create shortcuts, menus and toolbars.  Maybe a way to auto populate them.  Thanks!
Stan

---

### Post by BLTicklemonster on 2009-02-09
I've always wondered how to get to my network when in fluxbox.

---

### Post by snowpine on 2009-02-10
> **BLTicklemonster said:**
> I've always wondered how to get to my network when in fluxbox.

Simply choose a network manager (nm-applet, wicd, etc.) and add it to your ~/.fluxbox/startup file.

---

### Post by n2stc on 2009-02-10
> **snowpine said:**
> Simply choose a network manager (nm-applet, wicd, etc.) and add it to your ~/.fluxbox/startup file.

Will this work for OpenBox as well?

---

### Post by snowpine on 2009-02-10
> **n2stc said:**
> Will this work for OpenBox as well?

Yes, except that the file is ~/.config/openbox/autostart.sh

Check with an openbox/fluxbox tutorial if you aren't sure of the exact syntax, but I find it to be pretty self-explanatory.

---

### Post by icanfly0307 on 2009-02-10
Wow! This is an old thread! Anyways, I've switched over to LXDE which is as light as Flux but looks like GNOME. I've actually also switched from Ubuntu to Fedora, so I don't think I can offer any suggestions for Flux.

---

### Post by BLTicklemonster on 2009-02-10
> **snowpine said:**
> Simply choose a network manager (nm-applet, wicd, etc.) and add it to your ~/.fluxbox/startup file.

Thanks for the reply. I saw no such things in synaptic.

And if I did, and put then in startup, then once in fluxbox, where does it show up? Could thunar have it show up? I see a nice desklet in gdesklets that allows nautilus to run without taking over, but forgot to look to see if it showed the network... I'll have to log off and on again, lol.

Anyway, what's the deal with those two, and how do I implement them?

---

### Post by BLTicklemonster on 2009-02-10
Okay, gdesklets worked last night, but doesn't now for some reason. I added nm-applet, and see the network manager icon. That's great. I want, however, to see the other computers on the network. How can I do that from within fluxbox?

---

### Post by icanfly0307 on 2009-02-11
If they're Windows PCs, you need samba. If they're linux pcs, you need to go to "network:///" in Nautilus and they should come up.

---

### Post by n2stc on 2009-03-24
> **BLTicklemonster said:**
> Al Gore didn't invent the Internet, but he did make up global warming.

Love it!;)

---

### Post by BLTicklemonster on 2009-03-24
lmao woot woot!!!!

---

