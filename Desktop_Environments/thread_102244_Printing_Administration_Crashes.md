---
title: "Printing Administration Crashes"
date: 2005-12-11
forum: Desktop Environments
---

### Post by zoiks on 2005-12-11
I have breezy installed on two laptops, with similar setups.  One of them crashes every time I try to either add a printer or get the properties of an existing printer.  (I finally managed to work around the printer adding problem connecting to cups via [http://localhost:631](http://localhost:631), after setting "RunAsUser = No" in /etc/cups/cupsd.conf).

But this problem is annoying so I come here for help.

If I run gnome-cups-add from the command line, get about 2000 lines to stderr like

** (gnome-cups-add:9413): WARNING **: Two ppds have driver == 'hpijs (recommended)'
        ->hplip/HP-PSC_2350-hpijs.ppd (HP PSC 2350 Foomatic/hpijs[1]) and
        ->foomatic-ppds/hplip/HP-PSC_2350-hpijs.ppd (HP PSC 2350 Foomatic/hpijs)[1]


and then I see the gnome crash handler just as the "Add a Printer" window is appearing.  (BTW the "Inform Developers" option is ridiculous.  It's the hardest bug reporting helper I've ever seen.)  If I run gnome-cups-manager, the proper window opens, and then when I right-click on a printer and choose Properties, I get the same crash behavior.

So the question is, do I have to uninstall something to get the printing admin working normally/correctly?  Something in my configuration?  Any clues?  Note I have installed Japanese input methods on this laptop but not on the other, but that shouldn't make any difference.  I've noticed there've been a couple others reporting this problem in the ubuntu forums, but the best they could do was to work around it using cups over http.

---

### Post by jyona on 2006-01-09
I've been having the same problem, and I also just last night installed a Japanese input method editor (Anthy) - this seems consistent to me as well, since I had no problems with this before installing the Japanese IME - I'll remove it later this afternoon and post here again if that appears to fix the problem.

---

### Post by jyona on 2006-01-09
Update - Okay, so apparently the Japanese IME doesn't affect this cups problems as I've just removed it and am still having the same issue as before. Just thought I'd let you know.

Ditto to your comment on the 'Inform Developers' option when error messages appear. I tried to submit a bug report and (most likely because I'm a total linux newb) it crashed too:???: Oh well...

---

### Post by kamaaina on 2006-01-21
Same thing here!
when I run gnome-cups-add the first line looks like this

```

 ** (gnome-cups-add:10862): WARNING **: IPP request failed with status 1030

```
then about 3000 lines down
```

** (gnome-cups-add:10862): WARNING **: Two ppds have driver == 'hpijs (recommended)'

        ->hplip/HP-PSC_2500-hpijs.ppd (HP PSC 2500 Foomatic/hpijs[1]) and

        ->foomatic-ppds/hplip/HP-PSC_2500-hpijs.ppd (HP PSC 2500 Foomatic/hpijs)[1]


```

The messages all look very similar but seem to apply for different model printers.  I'm trying to install a HP Photosmart P1100.

Any help is appreciated!

---

### Post by saxonthebeach908 on 2006-02-02
I'm having the exact same problem with an HP deskjet 630c, and I also noticed it after installing anthy Japanese IME.

---

### Post by kamaaina on 2006-02-05
Intresting, I'm using Anthy as well.  I never thought that would have anything to do with it.  I wonder if someone could help us with some diagnostic ideas.

---

### Post by chikuwabu on 2006-02-18
I'm having the same problem.  I have ubuntu on two machines.  On one without Japanese input I have no trouble adding printers, but on one with Japanese input cups crashes every time I try to add a printer.  Hence I've been running ubuntu on the second machine without printing capabilities.  

I wonder if anyone has found a solution to this.  

Anyway in the meantime I did try the method as described by zoiks, but I'm having trouble installing the pdf printer driver.  The instructions make sense for an actual physical printer.  

[INDENT]I have breezy installed on two laptops, with similar setups. One of them crashes every time I try to either add a printer or get the properties of an existing printer. (I finally managed to work around the printer adding problem connecting to cups via [http://localhost:631](http://localhost:631), after setting "RunAsUser = No" in /etc/cups/cupsd.conf).[/INDENT]

After I go to [http://localhost:631](http://localhost:631) and click to the 'add printer' page, there's a list of printer manufacturers.  But I can't seem to find one for a pdf printer driver.  I have a feeling that there's another way of doing this, but I'm quite new to linux and haven't figure it out yet.  

Incidentally, I did apt-get the pdf printer driver.  When I use cups and try to add printer, the pdf driver is listed as "PDF Printer" among the printers detected (before cups crashes). 

Any help would be greatly appreciated.

---

### Post by saxonthebeach908 on 2006-02-25
I'm still having the same problem as before...I'm also disappointed that no developers are looking into this...it certainly seems like enough people want to use japanese input and printing to warrant further inquiry

---

### Post by spetey on 2006-03-05
Add me to the list of folks with this problem.  It seems to be for both serial and usb printer.

I too had anthy running for Japanese input.  Seems unlikely to be a coincidence though I don't know *anything* about why they would interfere like this.

Thanks!
spetey

---

### Post by s|k on 2006-03-07
I've had the exact same problem as you all, and I've gotten printing to work following the advice in this thread:
[http://www.ubuntuforums.org/showthread.php?t=84037&highlight=gnome-cups-add](http://www.ubuntuforums.org/showthread.php?t=84037&highlight=gnome-cups-add)


 Funny thing is on the same system before I re-installed I didn't have this problem.

---

### Post by akaihola on 2006-03-16
I've had this problem for some time, too, and I didn't have any clue that the Japanese input system could cause it.

I'll try to remove Anthy now and see if it helps for me. What are the exact packages which cause this problem?

---

### Post by akaihola on 2006-03-16
I found a [bug entry]("https://launchpad.net/distros/ubuntu/+source/gnome-cups-manager/+bug/27355") for this issue in Launchpad.

---

