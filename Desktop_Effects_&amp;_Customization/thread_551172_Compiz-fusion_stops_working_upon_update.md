---
title: "Compiz-fusion stops working upon update"
date: 2007-09-14
forum: Desktop Effects &amp; Customization
---

### Post by What_the_deuce on 2007-09-14
Hi guys
Ubuntu updated compiz-fusion and all the packages that go with it some time this evening, and since then, it has stopped working

I was running XGL with compiz-fusion on the ATI propriety drivers on my 200M card very well before this evening, but since the update, it fails a lot.

If anyone could tell me either if this will be fixed in the next update or how i can fix it myself, that wuld be grand. 

On another note, Avant Window Navigator doesn't work anymore either.

---

### Post by GernBlansten on 2007-11-04
Mine stopped working after update as well. If have intel graphics, and after update I can't even turn effects on.

---

### Post by Yfrwlf on 2007-11-04
This may be what happened to me too.  All I know is upon initial installation, Gutsy worked with Compiz with the restricted driver.  After changing to the open source ones, and then back again, and in general screwing around with things, it now does not work.  Says it can't do compositing, and I have to force quit the Appearance window because the error message won't go away.

I just figured I messed up my xorg.conf, and that the reinstall of the ATI restricted drivers didn't reconfigure xorg.conf correctly like the installer did, or that basically there were some things in xorg.conf upon initial installation that were removed somewhere down the line that it needed.  I maaaaaay do a reinstall to find out, and then save my xorg.conf.

Will let this thread know, or if someone else would like to try a reinstall to test this theory.  Whatever you do, if you do get it working again, save your xorg.conf so next time it messes up you can compare and see why, if this is indeed the cause of this problem.

---

### Post by Forlong on 2007-11-04
Post the output of ```
compiz
``` in a terminal.

---

### Post by Bigdeath on 2007-11-04
What repo's for compiz do you have?

---

### Post by GernBlansten on 2007-11-04
Here is what I get when I type compiz into the terminal:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2582 (rev 04) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :20.0

---

### Post by Yfrwlf on 2007-11-05
Hmm weird, mine simply said```
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
```which means that the fglrx driver isn't whitelisted anymore and should be I guess?  Maybe that's all my problem is then. :P  *looks up how to whitelist drivers*

---

### Post by Yfrwlf on 2007-11-05
I whitelisted the driver and am now getting```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4150 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity
```I guess this may be an unrelated issue though, sorry, I'll stop hijacking this thread now. :)  I found this other thread that has to do with my specific problem: [http://ubuntuforums.org/showthread.php?t=587633](http://ubuntuforums.org/showthread.php?t=587633)

Both of our outputs do mention that XGL is not present though, but you have texture_from_pixmap and I don't.

I'll post my xoirg.conf output here though so that everyone will have a fresh functional one to use after I reinstall. ;)

---

