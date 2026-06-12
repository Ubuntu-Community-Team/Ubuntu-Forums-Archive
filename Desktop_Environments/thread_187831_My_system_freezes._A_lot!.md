---
title: "My system freezes. A lot!"
date: 2006-06-03
forum: Desktop Environments
---

### Post by johan.t on 2006-06-03
hi, i need some help with bug-searching. my system crashes about 3-4 times/day so something has to be very wrong. the thing is I don't know where to look. someone told me to look in the logs, but where are they? could someone maybe take a look at them for me?](*,)

---

### Post by az on 2006-06-03
If you are using wireless, what kind of card do you have?

Did your computer work fine otherwise?

Did previous versions of ubuntu work fine?

---

### Post by johan.t on 2006-06-03
[QUOTE=azz]If you are using wireless, what kind of card do you have?[/quote]
I'm not using wireless.
[QUOTE=azz]
Did your computer work fine otherwise?
[/quote] Yes, it's quick and fine, no strange warnings and stuff...
[QUOTE=azz]
Did previous versions of ubuntu work fine?[/QUOTE]
No, but then I was running Kubuntu (5.10). So I thought that the problem was in KDE, one of the reasons I switched to GNOME. And when I was running KDE the similar problem only occured when doing things in kcontrol.

---

### Post by az on 2006-06-03
OK, well look at the logs in /var/log.  Use the log too (System, administration, System log).

Start with the messages log and then try the kernel log.   The current log is the simply named on, while the log from past sessions (computer on) are compressed and can have numbers appended to the (messages.0)

Also, does your graphics card work fine?  Do you have proper 3d acceletration?  There used to be a problem with some native xorg drivers that caused some memory leaks and crashes and what would happen is that the screensaver would randomly pick a 3d-screensaver and sometimes your card would work fine and then all of a sudden poof...

---

### Post by johan.t on 2006-06-03
Hmm.. The logs are plain greek to me.  ](*,) 

My graphic card is working just fine. Maybe it has to do with the cpu-temp?  With my table-fan (or whatever you say in english) standing by my computer I have not yet experienced any crashes. I have also installed a monitor to see what temp it is, with the extra fan it's about 43*C-44*C and without it more or less instantly rises to about 55*C.

---

### Post by az on 2006-06-03
If that is the case, turn off the fan and try to do something that wil tax the box and make it crash.  PLay some cpu-intensive games or something.

If you can open the case and see of the case fan or the cpu fan ar able to work properly and are not encumbered in dust?

If you can search the logs by time to find an incidence of when it crashed and post the last two dozen lines before that, maybe there is something telling there...

Copy and past them into the text editor and post them as an attachment...

---

### Post by johan.t on 2006-06-03
Here is the messages log. The crash occured approx 02.57. The lines included are the ones from just before and just after the crash.

---

### Post by az on 2006-06-03
[QUOTE=johan.t]Here is the messages log. The crash occured approx 02.57. The lines included are the ones from just before and just after the crash.[/QUOTE]
Nothing abnormal there.

---

### Post by johan.t on 2006-06-03
So it's safe to assume that temperature is the reason?

---

### Post by JoWilly on 2006-06-03
Try do diable agp and see how it goes (agp is often the cause of freezes).

What card are you using? nvidia ?

There is a problem with the latest nvidia 8762 drivers. When agp is enabled it often freezes on some motherboards.

---

### Post by johan.t on 2006-06-03
disable agp? sudo dpkg-reconfigure xserver-xorg?

I am using a Nvidia geforce mx400 with the 8762-driver installed.

---

### Post by JoWilly on 2006-06-03
Yep.

Add
Option "NvAGP" "0" 
to disable agp in your xorg.conf (nvidia section)... restart x and report back.

---

### Post by Valavien on 2006-06-03
I hve turned off AGP but still get total freeze :(
what is the command to determine which nvidia driver you are using?

---

### Post by JoWilly on 2006-06-03
[QUOTE=Valavien]I hve turned off AGP but still get total freeze :(
what is the command to determine which nvidia driver you are using?[/QUOTE]

Check if agp is working with: "cat /proc/driver/nvidia/agp/status"

Check the version with : "cat /proc/driver/nvidia/version"

---

### Post by Valavien on 2006-06-03
thank jowilly

I do have 8762 and agp is indeed disabled.  I have booted to the 386 kernel instead of the k7 I will see how that goes.

---

### Post by denzilla on 2006-06-03
Run a memory diagnostic program like memtest for a few hours and see if your memory is failing. Also a failing HDD could cause this. Any odd clicking could be a sign of that. Not saying that either of these is the cause, but they can cause the behavior you're experiencing.

---

### Post by JoWilly on 2006-06-03
[QUOTE=Valavien]thank jowilly

I do have 8762 and agp is indeed disabled.  I have booted to the 386 kernel instead of the k7 I will see how that goes.[/QUOTE]

hmm... if agp is diabled your problem is somehwere else I gess,

Yes try the i386 kernel, but I don't think it will change anything.

Is your system overclocked ?

edit: and follow denzilla's good advices :)

---

### Post by Valavien on 2006-06-03
I doubt it's memory or HDD as breezy worked no problems.

but will try anyway.
thanks

---

### Post by JoWilly on 2006-06-03
[QUOTE=Valavien]I doubt it's memory or HDD as breezy worked no problems.

but will try anyway.
thanks[/QUOTE]

And if you don't find anything but breezy works, don't forget to post a bug report on launchpad (search the bugs first) ;)

---

### Post by johan.t on 2006-06-04
Now I have installed a clean ubuntu 6.06. If the problem is still around I will report.

---

### Post by johan.t on 2006-06-06
Ok, problem solved. Switched HDD and everything is smooooth... :)

---

