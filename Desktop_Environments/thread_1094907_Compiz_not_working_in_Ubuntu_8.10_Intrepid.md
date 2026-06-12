---
title: "Compiz not working in Ubuntu 8.10 Intrepid"
date: 2009-03-13
forum: Desktop Environments
---

### Post by of_micenmen@yahoo.co.in on 2009-03-13
Hi,

i am a new to the world of linux so any help would be very welcome.

i recently installed 64 bit version of ubuntu and compiz doesnt seem to work on my system, i looked through various threads and couldnt find the problem. i even tried removing compiz completely and reinstalled it but i get the same error, This is the error i get wen i type "compiz start" on the terminal :-

"Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'start'
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format"

i used to get the same error message earlier aswell

---

### Post by 73ckn797 on 2009-03-13
Try this command:
```
./compiz-check
```
What are the results?

---

### Post by mika7367 on 2009-03-13
I'm new to Ubuntu 8.10 as well but I got it working reading this tutorial:

[http://reformedmusings.wordpress.com/2008/12/09/compiz-fusion-in-ubuntu-810-intrepid/](http://reformedmusings.wordpress.com/2008/12/09/compiz-fusion-in-ubuntu-810-intrepid/)

It's a bit long winded but works great :D

---

### Post by of_micenmen@yahoo.co.in on 2009-03-13
I typed "./compiz-check" on the terminal it said "bash: ./compiz-check: No such file or directory"

Look i can acess compiz setting manager and it lets me choose and modify all settings, iv aldo got the compiz tray icon sitting nicely in the tray but i still get no action from compiz.

---

### Post by AlanRick on 2009-03-15
I installed compiz (add programs from canonical) but under   System -> Preferences  there is **no** entry "Compiz Config Settings Manager"

Do I have to download the settings manager from somewhere else?

---

### Post by AlanRick on 2009-03-15
Found the solution:
Search for the application CCSM and install that too.

---

### Post by of_micenmen@yahoo.co.in on 2009-03-15
Hey thanx a ton allan solved my problem too workin fine now :)

---

### Post by vaserlan on 2009-03-16
my compiz worked in 8.04 but now i have 8.10, when i try to which to just normal in appearance visual effects it states  

"Desktop effects could not be enabled" :(

---

### Post by Forlong on 2009-03-17
Please post the output of this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by Vesperatus on 2009-03-17
> **AlanRick said:**
> Found the solution:
Search for the application CCSM and install that too.

It is so incredibly freaking ridiculous that this is not installed by default... I just lost 45 minutes of my life to find that.... 

```
sudo apt-get install simple-ccsm
```

---

### Post by vaserlan on 2009-03-17
I installed that too but although it appeared in the appearance visual effects tab it still didn't work. :(

---

### Post by Forlong on 2009-03-18
I won't be able to help you, if you ignore me.

---

### Post by Vesperatus on 2009-03-18
> **Forlong said:**
> Please post the output of this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

He is right. 

Make sure you run compiz-check first.

---

### Post by vaserlan on 2009-03-18
The check thing didn't help and like i said, it worked in 8.04.  what has changed between then and now?

---

### Post by Vesperatus on 2009-03-18
What do you mean it didnt helped ?!

Did it passed or failed ? It is not supposed to fix anything.

---

### Post by vaserlan on 2009-03-18
> **Vesperatus said:**
> What do you mean it didnt helped ?!

Did it passed or failed ? It is not supposed to fix anything.

Ok. sorry. i'll try again. :$ next time i'm in ubuntu. At the mo i'm in windows using M$ word to write a screenplay. 

I know i can use OO3 and it really good just not as good as M$ word 2007.

---

### Post by Arup on 2009-03-19
OO3 is not MS2007, however it does all that MS2007 does with less drama and razmatazz. From basic WP to presentation to creating databases, it handles all and I have seen countless of big and small offices running OO and doing their business. Also extensions like Writer's tool, Language tool make it a boon for those who are into journalism writing for blogs, magazines etc.

Anyways I thought this was a desktop enviroments thread related to Compiz, you mentioned that Compiz is not working and people posted viable solutions to your problems. Compiz works fine out of the box with all major cards, from ATI, Intel to Nvidia. So far I have installed Ubuntu on hundreds of PCs with vastly different configurations ranging from ancient P-III to cutting edge quad cores and even ones with dual GPU. Not once have I come across any such issues of Compiz disabled unless the PC is old and in that case, Compiz is automatcially disabled during install.

---

### Post by Forlong on 2009-03-19
> **vaserlan said:**
> The check thing didn't help
It would help, if you'd **post the output** here.

---

### Post by vaserlan on 2009-03-19
> **Forlong said:**
> It would help, if you'd **post the output** here.

Sorry. :$

I forgot [seriously it slipped by my ADHD mind] a crucial couple of facts re my situation. 

my 8.04 kept on freezing completely [only switching off power got out it, tried badblocks and all that to correct it].  It again [and crucially] froze up during the instalation of 8.10.  Gradually, via updates and thru the CLI [with the help of a friend], i got it to work.  

So what I'll do is wait till 9.04 is available, install it and thus I'll then have a proper installation.  Thus coz I'll have a good installation, I'll be starting from a solid base when it comes to getting compiz fusion to work.  And if there are any problems, they should be easier to deal with coz i'd have a normal installation ... hopefully. [emoticon for "here's hoping"] - ;)

> **Arup said:**
> OO3 is not MS2007, however it does all that MS2007 does with less drama and razmatazz. From basic WP to presentation to creating databases, it handles all and I have seen countless of big and small offices running OO and doing their business. Also extensions like Writer's tool, Language tool make it a boon for those who are into journalism writing for blogs, magazines etc.

Anyways I thought this was a desktop enviroments thread related to Compiz, you mentioned that Compiz is not working and people posted viable solutions to your problems. Compiz works fine out of the box with all major cards, from ATI, Intel to Nvidia. So far I have installed Ubuntu on hundreds of PCs with vastly different configurations ranging from ancient P-III to cutting edge quad cores and even ones with dual GPU. Not once have I come across any such issues of Compiz disabled unless the PC is old and in that case, Compiz is automatcially disabled during install.

[I]btw: re OO3, i don't like the comments not clearly showing which part of the text they refer to.  Also in M$WORD 2007, I have all my macros set up [for individual paragraphing for dialogue, cue, biz, parenthetical, 'insert date and time' into comments in pink tex, various colours to represent such things as writing typed up from paper notes, writing created in the present draft and writing from previous drafts] and customised context menus and templates. [compared to Final Draft, i prefer my customised M$ Word 2007] I am also used to it, just as i am used to English and won't be learning French even though it is possible that it might, just might, be as good as English. ;)
[/I]

---

