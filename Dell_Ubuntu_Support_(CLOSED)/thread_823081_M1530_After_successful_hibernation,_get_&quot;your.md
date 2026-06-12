---
title: "M1530: After successful hibernation, get &quot;your computer failed to hibernate&quot; message"
date: 2008-06-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hackel on 2008-06-08
Both suspend to ram and suspend to disk work fine on my M1530, however whenever I resume from hibernation, I get a libnotify message: "Sleep Problem - Your computer failed to hibernate. Check the help file for common problems."

I don't know what is triggering this, even though the hibernate functions normally.  I get 4 loud beeps prior to resuming from hibernation, I don't know what this means or if it is related.  Any help would be appreciated.

---

### Post by mtbsoft on 2008-06-08
I can confirm the same happens occasionally on my Inspiron 9400, probably about 50% of the time.  Mine also seems to work fine afterwards, despite the error.

---

### Post by mozillar on 2008-07-22
This workaround quieted the shrill beeps that accompanied the "Your computer failed to suspend" message when waking from suspend for my laptop. This error would occur occasionally, despite always suspending just fine. 

Those shrill beeps had to go, 'cuz that's no way for me to wake-up before having coffee.

Workaround:
uncheck "Use sound to notify in event of error" in
System->Preferences->Power Management->General

I'm curious if this addresses the issue for your hibernation too.

---

### Post by freonchill on 2008-07-25
same problem here
dell 1150

sometimes the wireless needs to be restarted
"sudo ifconfig eth1 up" fixes that problem

---

### Post by Ralph L on 2008-08-24
I get the same "your computer failed to hibernate" message about half the time.  In addition, now and then the window box to enter the password won't appear.  The computer seems to have reloaded the hibernate file but hangs up in displaying the password window.

Dell Latitude D610 laptop running Hardy

Ralph

---

### Post by Giacecco on 2008-09-13
Same happens here on a ThinkPad X60 running up-to-date Ubuntu 8.04.

Giacecco

---

### Post by Zaff on 2008-10-07
Same on a macbook 2nd Generation and an ASUS M3N78 Pro Motherboard. Has anyone found a fix for this ?

---

### Post by dseybert on 2008-10-25
Same problem on a Sony Vaio VGN-A150 with 8.04.1

I have noticed this message as it's about to power down:

```
[ 107.664863] i8042 kbd 00:03: activation failed
```

The first number in brackets changes each time, but the rest is verbatim each time.

---

### Post by dseybert on 2008-10-31
Anyone?

---

### Post by FreakTimmah on 2008-11-01
I get the same message on my Dimension 4600.

---

### Post by yldouright on 2008-11-01
I have the same problem with an Asus P2BDS running a fully updated Feisty. My bios is configured for minimal power savings.

---

### Post by yldouright on 2008-11-05
Well, for my system it is not a configuration issue. My motherboard needs some mods to do ACPI properly.

---

### Post by kaixi on 2009-02-08
Sorry for bringing up this old thread, but I'm having the same problem here with a Dell Vostro 1510 laptop. Any ideas of what's going on?

---

### Post by jtellerelsberg on 2009-12-20
I have nothing useful to add, only "ditto" that I get the same problem on a Dell XPS M1330 with Hardy Heron 8.04 preinstalled. The error occurs for me more often--nearly or fully every time--if I put the computer into suspend, rather than hibernate. While in suspend it does actually go into full hibernate, and then when un-hibernating I get that "failed to hibernate" message. I get the message much less often if I go directly into hibernate. I don't recall having any problems coming out of hibernation beyond this pseudo error message popping up.

---

### Post by hortstu on 2010-03-25
I guess I'll bumb this with,

I have the same problem.

Anyone figure out how to fix it yet?

---

