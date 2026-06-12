---
title: "Kubuntu boots into console, startx works fine.."
date: 2005-06-12
forum: Desktop Environments
---

### Post by c2h5oh on 2005-06-12
For a while now my kubuntu boots into console, which is quite strange as ubuntu starts X regardles of runlevel (which in my case is ok by debian standards). 
The problem started when I tested one of the new kernels, which for some reason continued to fill my logs with error messages at full write speed of my hdd ;-). The kernel is long gone, but the problem is still there. I can't see how the kernel could have caused that, but just in case..

I don't get any error messages about kernel modules or xwindows (double-checked logs), except for some minor font problems (cyrylic fonts missing if I am not mistaken, which I don't use anyway).
If I log in and startx it works fine. 
I managed to avoid dodgy repositories (all I've got from them are some w32 codecs), so it shouldn't be the cause..
Already tried reinstalling xorg and kde related packages with no success and I am running out of ideas. Any suggestions or better yet a solution would be welcome  :) 

Thanks in advance

---

### Post by FizDev on 2005-06-12
Hello there,
I am new to linux and just intalled kubuntu a few days ago so I'm not too sure about what I am about to say...
You can try to add "startx" at the end of "/etc/init.d/bootmisc.sh"
Hope this helps/works!

---

### Post by elsewhere on 2005-06-12
Just a thought, but maybe check to make sure that kdm is still set to start as part of your init scripts at login.

Cheers,
KV

---

### Post by Xian on 2005-06-12
[QUOTE=c2h5oh]For a while now my kubuntu boots into console, which is quite strange as ubuntu starts X regardles of runlevel (which in my case is ok by debian standards). [/QUOTE]
What do you have set as the default when you run this command:

```
$ sudo dpkg-reconfigure kdm
```

---

### Post by c2h5oh on 2005-06-12
yeah, I've done a quick check and there seems to be something wrong with kdm (synaptic shows it's installed, but it isn't and on the other hand it show there's no gdm in the system while it's up and running) 
things going on with my system add a whole new meaning to 'odd' ;-)

---

### Post by Xian on 2005-06-12
Well, you of course have the options of reinstalling KDM or even installing GDM and seeing if you have better luck with that application.

What happens at the prompt after boot when you login and issue this:

```
$ sudo /etc/init.d/kdm restart
```

---

### Post by c2h5oh on 2005-06-13
It used to be odd, now it's totaly crazy :/

After reinstalling kdm system boots up right into X, with a nice login sceen but due to some strange and nasty screw-up my keyboard ceases to word at this point (while working fine just seconds before). the only character that works is 
'=' (which is displayed as '9').
luckyly I have started ssh server on that box couple of days ego, so I can still access it.

already tried:
-reinstalling kdm once again
-dpkg-reconfigure localeconf
-dpkg-reconfigure console-data (just in case)
-restored old xorg.conf (i backed it up just minutes before installing kdm)
-dpkg-reconfigure xserver-xorg
-dpkg-reconfigure kdm (which fails tostart)

the keyboard I am using is a generic, 105-key, ps2

Any ideas?

P.S. Note to myself: never, absofuckinglutly never start messing with your system 12 hours before project deadline ;-)

UPDATE: I can confirm it is a KDM issue - removing kdm (and going back to the previous problem :/) solves keyboard problem. And now I'm off to google to search for a solution.

---

### Post by c2h5oh on 2005-06-21
I wonder if anybody has any ideas... I managed to find some other people having exacly the same issue with KDM + non-US keyboard layout, but no solution yet..

---

### Post by fdoving on 2005-06-24
[QUOTE=c2h5oh]I wonder if anybody has any ideas... I managed to find some other people having exacly the same issue with KDM + non-US keyboard layout, but no solution yet..[/QUOTE]
 Sounds very strange. What if you install gdm - just to test?

---

### Post by fdoving on 2005-06-24
[QUOTE=fdoving]Sounds very strange. What if you install gdm - just to test?[/QUOTE]
 Note: If you'd like to remove gdm later, it's smart to write down the depends it pulls in.

---

### Post by c2h5oh on 2005-07-01
Now it's even stranger (than fiction ;-) ). gdm works fine (but it sucks anyways :P) If anybody has any idea why the f### kdm refuses to work I'd be grateful.

---

### Post by akvik on 2006-05-08
this is kind of a stupid suggestion, but are you sure that the kubuntu-desktop package is installed? There might be packages that are missed out because of this. The kubuntu-desktop package is easy to "loose" since it sometimes uninstalls when you remove other packages. Then in an upgrade situation you miss out on a lot of packages.

:-)

---

