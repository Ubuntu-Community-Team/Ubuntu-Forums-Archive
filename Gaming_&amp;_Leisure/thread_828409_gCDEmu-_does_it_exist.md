---
title: "gCDEmu- does it exist?"
date: 2008-06-13
forum: Gaming &amp; Leisure
---

### Post by MEGAMANULTIMATE on 2008-06-13
Hi all, 

I've been trying to painstakingly covert .cue files to .iso for the last couple of days, and nothing seemed to be working. I've recently downloaded cdemu and all of it's dependencies. There even seems to be a GUI of the program, but nothing I type in the command line does anything. Indeed, Ubuntu seems to refute its existence. And every other forum I've googled seem to be allergic to the subject. So, how exactly do I get this GUI to run? Any help on this matter is greatly appreciated. I'm running Gutsy on a Dell M1210.

---

### Post by Grishka on 2008-06-13
> **MEGAMANULTIMATE said:**
> Hi all, 

I've been trying to painstakingly covert .cue files to .iso for the last couple of days, and nothing seemed to be working. I've recently downloaded cdemu and all of it's dependencies. There even seems to be a GUI of the program, but nothing I type in the command line does anything. Indeed, Ubuntu seems to refute its existence. And every other forum I've googled seem to be allergic to the subject. So, how exactly do I get this GUI to run? Any help on this matter is greatly appreciated. I'm running Gutsy on a Dell M1210.

cdemu never worked for me. try AcetoneISO, for example from here: [http://getdeb.net/app/AcetoneISO](http://getdeb.net/app/AcetoneISO). it doesn't seem to work for everyone, but if if fails for you, try ccd2iso from the repos. this one's command-line only, mind you.

---

### Post by MEGAMANULTIMATE on 2008-06-13
Thanks Grishka, but it looks like that Acetone ISO 2 doesn't support .cue, and the ccd2iso only seems to support .img. Do you happen to know if there's anything else out there?

---

### Post by bulletxt on 2008-06-13
if you absolutly need to read the cue file, then your image is a multisector image I suppose. in that case, no. there ain't anything that can do the job. however, if you're able to make cdemu 1.0 work, you should be able to mount the img via cue.

---

### Post by Grishka on 2008-06-13
> **MEGAMANULTIMATE said:**
> Thanks Grishka, but it looks like that Acetone ISO 2 doesn't support .cue, and the ccd2iso only seems to support .img. Do you happen to know if there's anything else out there?

whoops. that's not ccd2iso, but iat, I think. you can convert .bin files with AcetoneISO, a .cue file is not needed.

---

### Post by desowin on 2008-07-13
There is offical gnome applet...

There're also unoffical things ;)
I wrote tiny app to control cdemu, which should work in every Desktop Environment, you can get it from here:
[http://people.atheme.org/~desowin/cdemu-tray/](http://people.atheme.org/~desowin/cdemu-tray/)

(read the comments on top of that file, and you'll know pretty eveyrthing ;) )

---

### Post by Major_Kong on 2008-07-15
You should win, just for using C. :P

What are the dependencies ? ( libdbus-glib-1-dev libglib2.0-dev libgtk2.0-dev, and what else ? )

---

