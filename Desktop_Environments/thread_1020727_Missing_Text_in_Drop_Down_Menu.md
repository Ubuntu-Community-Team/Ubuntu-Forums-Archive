---
title: "Missing Text in Drop Down Menu"
date: 2008-12-24
forum: Desktop Environments
---

### Post by sharathpaps on 2008-12-24
Hi,
    I am running Ubuntu Intrepid Ibex 8.10 on my system. I have a strange problem; the text in the drop down menus of some programs that I installed don't show up. I've experienced this problem with Wine (screenshot), Opera (screenshots) among others. I've included the screenshots because I can't better describe the problem with words ( A picture is worth a thousand words ain't it? :P ).

My System Specifications are as follows :

Ubuntu Intrepid Ibex 8.10, Fully Updated
2 x Intel Pentium 4 2.80 GHz
2 Gb RAM
80 Gb Samsung HDD
250 Gb Seagate HDD on SATA
GeForce MX 4000 Graphics Card
Creative Sound Blaster Sound Card

I'm new to Linux and therefore I have not made any configuration changes to the system...



Thanks in advance....

---

### Post by s3gfault on 2008-12-24
k, i think the required fonts are missing or corrupt.  Refer to the documentation for these applications as to what fonts are required and check you installed font packages.

---

### Post by namdung on 2008-12-24
You mentioned *some menus*, does that mean other menus are fine? Did u try to install any new theme?

---

### Post by sharathpaps on 2008-12-24
@ s3gfault
the fonts folder in Wine was empty, but putting in a new font didn't change anything. I'm new to this thing so its kinda confusing.

@namdung
No, all the menu's in these programs are affected. I did install a new theme some time back, but I had not installed Wine then...Will try using the default Ubuntu theme...

Thanx guys

---

### Post by spegru on 2009-01-05
I also have this problem in my brand new setup

Seems to affects additional applications only. eg opera, amarok, kaffeine, openoffice3, but not firefox or thunderbird
However sometimes if you expand the menus, the text appears for the expanded section only

Doesnt sound like fonts to me - more like a screen refresh thing

spegru

---

### Post by zeoss on 2009-01-06
I Have the same problem,when I run compiz fusion.but this is just for kde applications .I just disable desktop effect and every thing is good.

---

### Post by binbash on 2009-01-06
Its nvidia driver bug

---

### Post by spegru on 2009-01-08
I noticed there are several possible nvidia drivers.
Anyone know which ones are or are not affected?
The one that doesnt work properly for me is an MX4000

I have another intrepid setup with nvidia & 3d that works fine, but that's a different chipset - GeForce6100

spegru

---

### Post by spegru on 2009-01-09
I can confirm that this problem only exists with the nvidia drivers. It does not even need the 3d effects to be switched on for the problem to happen.
There appears to be only one nvidia driver available for my card

Fo now I am using the opensource drivers that came by default. They're pretty good actually, although 3d is not supported

---

### Post by sharathpaps on 2009-01-14
spegru & binbash are correct.. I finally got the answer courtesy of austin987, moderator at WineHQ Forums. This is a known bug in Ubuntu Intrepid Ibex 8.10 having the NVIDIA accelerated graphics driver installed. It is not a font problem. I distinctly remember installing the update at some point. I had the problem with Wine, Opera & Filelight.

The bug report is [here]("http://bugs.winehq.org/show_bug.cgi?id=16146")

_The Solution_:

This is the driver that I had to deactivate. In Intrepid Ibex 8.10, go to, System>Administration>Hardware Drivers & deactivate the Nvidia accelerated graphics driver. Use the screenshot as a guide. Restart the system. You might have to reinstall wine & other programs which had this problem. 

[IMG]http://i41.tinypic.com/2n6ergg.png[/IMG]

The native graphic drivers work quite well but the downside is that you wont be able to play games that require 3D.

That's it.

---

### Post by sharathpaps on 2009-01-14
err...I'm sorry. I wanted to mark this thread as [SOLVED] but I can't seem to find the option under 'Thread Tools' although I am logged in.

How do I do that?

---

### Post by sharathpaps on 2009-01-15
Hee hee hee...Looks like I'm talking to myself...Anyway, I just discovered the reason I am not able to apply the [SOLVED] tag has something to do with the recent server downtime we've been having. The ability to thank people too has been temporarily suspended. You can read more [here]("http://ubuntuforums.org/showthread.php?t=1039481")

---

### Post by helmethedd on 2009-06-26
i'd like an answer to this problem as well, but so far, all i'm hearing is ppl who like to hear themselves talk. 
plz only respond if you REALLY know how to fix it

---

### Post by sharathpaps on 2009-06-29
@helmethedd,
I'd help if you read the thread completely. Read [this]("http://ubuntuforums.org/showpost.php?p=6546492&postcount=10") if you want the solution that worked for me..

---

### Post by richarduie on 2009-12-17
Sharathpaps -  Thanks much for diligently pursuing this and sharing the results of your inquiries.

I had this problem on a fresh install with no Wine involved. network-manager and kaffeine menus were affected (might have encountered more, if I'd looked further, but I started seeking an answer and found your thread). Deactivated the acceleration, and all's well.

Note for other who find this...not only were menu text items "missing" (sometimes, they would flash briefly, but usually nothing at all), but tooltip popups for the associated app had no text. Just another indicator symptom, if you're trying to diagnose.

Additional symptom: kaffeine would not play video of .wmv, .mpg, etc. file...audio played - dragon would display video as well.

---

### Post by sbersier on 2009-12-31
I had the same same problem with a few programs (kpovmodeler and rakarack).
My assumption, which you can test, is that metacity is the default window manager you use (ina terminal window type:  **ps -u your_username** and look if you have a metacity process running). If so, then the following worked for me:
in a terminal window, type:  **compiz --replace&**
Of course compiz has to be installed (from the standard repository).
When you want to switch back to normal just type: **metacity --replace&** in the same terminal window. The solution is not 100% perfect but at least I could use these programs.

Regards,
Steph

---

