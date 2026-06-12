---
title: "[SOLVED] Inspiron 6400 56Kb modem"
date: 2007-10-12
forum: Dell  Ubuntu Support
---

### Post by Linicks on 2007-10-12
Hi all,

This has me beat.  Years ago I installed modems easily in Linux (even on my old 486 boxes running mandrake 6.5), but here we are, 2007 with a built in modem and supplied drivers by Dell, and yet the modem is AWOL.

BTW, this isn't important - I just wished to ensure it works OK in case I ever need to dial-up when stuck in Timbuktoo or somewhere.

After a lot of investigation, it appears the hsfdrivers are installed OK:

```
hsfserial              24580  7 hsfusbcd2,hsfmc97sis,hsfmc97ati,hsfmc97ali,hsfmc97via,hsfmc97ich,hsfpcibasic2
hsfengine            1266700  8 hsfusbcd2,hsfmc97sis,hsfmc97ati,hsfmc97ali,hsfmc97via,hsfmc97ich,hsfpcibasic2,hsfserial
hsfosspec             105448  9 hsfusbcd2,hsfmc97sis,hsfmc97ati,hsfmc97ali,hsfmc97via,hsfmc97ich,hsfpcibasic2,hsfserial,hsfengine
```

Checking up with scanModem, I get this:

```
Analysing card in PCI bus 00:1b.0, writing to scanout.00:1b.0
  The High Defintion Audio card with PCI ID 8086:27d8 may host a soft modem chip.
 The modem driver snd-hda-intel is loaded but inactive.
2nd run of scanModem
Checking for match with Archived softmodem information.
IDENT=hsfmodem

```

OK, so it is all there.  BUT the snd_hda_intel module seems to have taken over (why is it inactive?).

I added this to /etc/modprobe.d/blacklist (not caring if this breaks sound for a bit), but it just gets ignored... and loads everytime.

I also added snd_hda_codec, but still the intel modules load and take over the modem.

Why does blacklist just get ignored?  I can't see what else relies on these modules?

Why do they 'take' over the hsf modules?

Any ideas welcome, please.

Thanks,

Nick

---

### Post by neptho on 2007-10-13
Have you rerun mkinitramfs?

---

### Post by Linicks on 2007-10-13
OK, I sussed it:

/etc/modprobe.d/blacklist-modem

```
# Uncomment these entries in order to blacklist unwanted modem drivers
blacklist snd-atiixp-modem
blacklist snd-intel8x0m
blacklist snd-via82xx-modem
```

This file was already populated, but the modules were commented out.  Activating the blackist to these modules, the modem is now visible and working!

Nick

---

### Post by MozartlovesUbun2 on 2007-11-06
sorry i didnt  understand how u solved this problem

i am stuck this month in Montreal renting a place where there is only dial up access

i have a dell inspiron 6400, could you please list a step by step tutoial

thanks

==================
ok i got it, you have to take off the 3 "#"

as i'm at the library using wireless now i cant try it out till i get home
==================

---

### Post by MozartlovesUbun2 on 2007-11-08
thank you nick for taking the time to reply, yes i  did as mentioned in your post and removed the 3 "#"

furthermore:

Install gnome-ppp **(DONE)**

Set wvdial.conf to use 'stupid mode=on'. **Can't find this mentioned file, where do i look for it?**

i did a normal search in the system files "/"
and a search with the "deskbar Applet" (here i found a file with the "stupid mode" line, but it is not wvdial.conf) it is in my home directory and came from the package i downloaded **scanModem.gz**

below the pics

---

### Post by Linicks on 2007-11-08
wvdial.conf lives here:

/etc/wvdial.conf

You may need to run it by hand first:

> sudo wvdial

Then Ctrl+c to stop it.

[B]Whoa!  Stop.  I just see you profile, you are running Gutsy... there is NO driver yet for the Inspiron 6400 modem on Gutsy:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Connexant_Modem_Unavailable](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Connexant_Modem_Unavailable)[/B]


Nick
P.S. to find specific files, there is no need to 'search'.  Just use 'locate' (which queries the updatedb)

e.g.:


> sudo locate wvdial.conf

---

### Post by MozartlovesUbun2 on 2007-11-08
> **Linicks said:**
> wvdial.conf lives here:

/etc/wvdial.conf

You may need to run it by hand first:

> sudo wvdial

Then Ctrl+c to stop it.

[B]Whoa!  Stop.  I just see you profile, you are running Gutsy... there is NO driver yet for the Inspiron 6400 modem on Gutsy:

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Connexant_Modem_Unavailable](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Connexant_Modem_Unavailable)[/B]


Nick
P.S. to find specific files, there is no need to 'search'.  Just use 'locate' (which queries the updatedb)

e.g.:


> sudo locate wvdial.conf

ouch, well that hurts, hmm i can't go back to feisty now just for the 3 weeks, strange why does it work in one version and not in the other? also one would suppose that stuff which worked before in the older version should work even better in the new :) oh well

---

