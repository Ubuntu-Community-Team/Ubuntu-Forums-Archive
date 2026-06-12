---
title: "W32/Magistr.a@MM found by Aegis"
date: 2005-05-01
forum: Desktop Environments
---

### Post by gingermark on 2005-05-01
Hi,

So, I thought I'd better give the 'ole home directory a scan, about a month after I started using Ubuntu (although I am currently sitting in Kubuntu - dunno if that matters) and Aegis Virus Scanner has picked up W32/Magistr.a@MM, which according to the McAfee site is a Windows virus.

Aegis says it's located in the ./wine folder (which would be fine, but I removed WINE from my system, at least  thought I did) and in the Totem add-ons folder. Each time it is vp31vfw.dll that is infected.

I am still pretty new to Linux in general, so I was wondering:

Is this a problem, given it is a Windows virus?

Aegis doesn't appear to have any virus removal options (although this is my first time using it, so apologies if I got that wrong). Is there another free anti-virus program for Linux that one might consider more 'complete'?

The virus is supposed to be delivered via email, but I only use a webmail service and have not received any emails with any executable files attached, and as such am bemused as to how it arrived on my system. Is it possible that it came with Totem and / or WINE?

Any help would be most appreciated,

best regards,
gingermark.

EDIT: Aegis actually seems to be caught in a loop within the WINE directory, ie claiming the virus is in "/home/gingermark/.wine/dosdevices/z:/home/gingermark/.wine/dosdevices/z:/home/gingermark/.wine/dosdevices/z:/home/gingermark/.wine/dosdevices/z:/home/gingermark/.wine/dosdevices/z:/home/gingermark/.gnome2/totem-addons/vp31vfw.dll"

So I assume there is only one virus, within the totem-addons directory. Given that I have removed wine and libwine in Synaptic, is it ok to delete the ./wine directory?

---

### Post by dmn_clown on 2005-05-02
You have very little, if anything, to worry about here.

The virus (If the file really is infected and not a false positive... try scanning it with a different A-V program to be sure) will not execute in any environment other than windows.

However, the endlessly looping scan is a problem that has been fixed in the latest version of Aegis.  Try the current version from CVS.   :)

---

### Post by shof2k on 2005-05-31
[QUOTE=dmn_clown]You have very little, if anything, to worry about here.

The virus (If the file really is infected and not a false positive... try scanning it with a different A-V program to be sure) will not execute in any environment other than windows.

However, the endlessly looping scan is a problem that has been fixed in the latest version of Aegis.  Try the current version from CVS.   :)[/QUOTE]
 If you want to verify the virus, and have java installed, google for Trend micro's "Housecall" scanning service.  It's a java based web scanner.

---

### Post by martbd on 2006-07-29
This software detected viri on my Windows drive but when I ran TrendMicro housecall it found nothing what is going on here

---

### Post by findus on 2006-10-30
Aegis has just found the same virus in the same file on my computer. Is it in one of the codecs that I installed (from Automatix2)?  Or is it a false positive?  Only slightly concerned but have two Windows machines on my home network and don't really want them getting infected. Having said that, AVG (on my Windows machines) hasn't picked anything up yet.

Any advice would be greatly appreciated!

Fin

---

### Post by Perfect Storm on 2006-10-30
It's false detection.

---

### Post by findus on 2006-10-30
> **Artificial Intelligence said:**
> It's false detection.

Thank you!

---

### Post by Rothchild on 2006-11-05
Please can someone confirm this as a false detection with Aegis

It says win32.magistr is present in a fresh download of the via hyperion drivers here: [http://www.viaarena.com/default.aspx?PageID=420&OSID=1&CatID=1070](http://www.viaarena.com/default.aspx?PageID=420&OSID=1&CatID=1070)

Shome mishtake shurely?

How can I get aegis to be more accurate?

Child

---

### Post by Rothchild on 2006-11-06
Bump

Anyone?

Cheers
Child

---

### Post by Perfect Storm on 2006-11-06
If you're unsure you can try it with diffrent anti-virus applications.

> How can I get aegis to be more accurate?
I don't quiet understand your question here.

---

