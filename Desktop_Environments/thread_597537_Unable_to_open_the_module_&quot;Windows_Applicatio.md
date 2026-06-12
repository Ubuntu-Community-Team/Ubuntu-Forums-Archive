---
title: "Unable to open the module &quot;Windows Applications&quot; in &quot;System Settings&quot;"
date: 2007-10-30
forum: Desktop Environments
---

### Post by simsen on 2007-10-30
Hi all!

After playing around with Wine, including installing and uninstalling it using Adept, I have found that I am suddenly unable to access the module called Windows Applications in System Settings.

That module contains settings for Wine.

This is the error message I get:

```

The module Windows Applications could not be loaded.

The diagnostics is:

Possible reasons:
* An error occured during your last KDE upgrade leaving an orphaned control module
* You have old third party modules lying around

Check out these points carefully and try to remove the module mentioned in the error message. If it fails, consider contacting your distributor or packager.

```

That, my friends, is incomprehensible to me, so I would be extremely grateful if you could help me out.

Thank you all in advance.

- S

---

### Post by blazv on 2007-10-31
I have the same problem here. I noticed it in kubuntu 7.04 and it is still here afer upgrading to 7.10. (during which I had problems because of wine repositories). My other computer related problems were a nasty message after emptying trash (managed it), Dolphin closing message (managed it), screen resolution problem related to intel video card (upgrade solved it) and a persistent problem with lexmark x1290 multi-machine (no scan/copy/fax support). 
Still waiting for solutions since I am no computer/linux guru...
I too thank anybody who will solve these in advance. *Buntu really makes the difference! Thanks again!

B.

---

### Post by blazv on 2007-10-31
The most annoying thing is that most applications run smoothly only this one game that obviously needs some adjustment of wine settings. All I get is the splash screen and then a blank black screen.  Will have to find a way around...

---

### Post by Gavin77 on 2007-10-31
The last time I had your problem it seemed to fix itself by rebooting the computer.
Failing that you could try reinstalling wine.

---

### Post by blazv on 2007-11-01
I did both a while ago and... the thing is still there:( Thank you anyway!
B.

---

### Post by blazv on 2007-11-01
An update: just did both again. Just in case... After rebooting it is still there (I really rarely reboot my box these days...). After sudo apt-get remove and then install wine it is still there.

---

### Post by Gavin77 on 2007-11-01
how about trying 

> sudo apt-get purge wine

and then reinstalling.

---

### Post by blazv on 2007-11-03
Thank you. Just did this, too. Unfortunately purging and then reinstalling wine was not what it takes to get rid of this message. I guess wine isn't the troublemaker here. Any other ideas?

---

### Post by Gavin77 on 2007-11-03
> **blazv said:**
>  Any other ideas?


Sorry, I'm not much of an expert.  I'm not sure what could be causing it.

---

### Post by blazv on 2007-11-04
Thank you.

---

