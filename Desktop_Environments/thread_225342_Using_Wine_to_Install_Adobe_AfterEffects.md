---
title: "Using Wine to Install Adobe AfterEffects?"
date: 2006-07-29
forum: Desktop Environments
---

### Post by BetaMaster on 2006-07-29
I'm not sure if this is the right forum to post this in, but I'll try anyways:
I have Adobe AfterEffects 7.0 on DVD. I wanted to reinstall it on Ubuntu because I'm going to be using it for a video me and a mate will be making. I can't get wine to install it. I cd to the directory, and type 'wine Setup.exe' but I get this error:
```
fixme:ole:CoRegisterMessageFilter stub
fixme:ole:CoRegisterMessageFilter stub
```
I try running another file on the disc, instmsi30.exe, and that does something.
A window pops up titled "Extracting Files"
says "Verifying File:     instmsi30" in the window, with an empty progress bar below.
Simultaneously with that, an error pops up, also in Wine, titled "Extraction Failed"
```
Unable to find a volume for file extraction. Please verify that you have proper permissions.
```
I get the same error when I type 'sudo wine instmsi30.exe' so I dunno what the problem is.

A little help please?
Thank you!

---

### Post by BetaMaster on 2006-07-29
I really don't like bumping, but could someone please offer any help?

---

### Post by cptnapalm on 2006-07-29
I'm not much of a Wine user, so I can't really help, but Google popped up this: [http://appdb.winehq.org/appview.php?iAppId=648](http://appdb.winehq.org/appview.php?iAppId=648)

Don't think that it is currently doable :(

---

### Post by philstopford on 2006-08-10
You cannot run this at the moment due to the complex Digital Rights/Restrictions Management that Adobe has implemented. Codeweavers is hoping to deliver the support in Wine before early 2007, but for now you are stuck and it's not worth trying to install it.

One option might be to purchase and install Parallels, using that to install Windows within Ubuntu.

---

