---
title: "Occasionally can't reboot or shutdown"
date: 2006-01-14
forum: Desktop Environments
---

### Post by Navyblue on 2006-01-14
I am running a frsh installed 32 bit Kubuntu on a AMD Athlon 64 system, nForce3 chipset.

When I shutdown or reboot from KDE, instead of seeing X quiting to console scrolling a bunch of text, my screen would just turn black and would stay that way.

First of all, I have to stress that this problem does not happen all the time, only some of the time (may be 30% of the time). I don't remember seeing it  on 32 or 64 but Hoary. I don't remember it happening on 64 bit Breezy, but may be I didn't use it long enough to see this. I have fresh installed 32 bit Kubuntu for at least twice and this problem persist.

Please tell me how to look for its error message and please forgive me that this post has not provided you any tangible information about this problem.

I have two unfounded guess.

One is it has got to do with X server display. At one time I did a "log out" (which I rarely do) and it takes a while (longer than usual) to get me to KDM and the display turnout to be garbled (it shows a tiling of a portion of my wallpaper).

Another is it got to do with USB drive monting, automounting has always been funky on my system, sometimes it would take forever to mount or unmount. And I need an fstab entry in order for it to be mounted.

Again, these are  guess that I have no evidence to substantiate, just in case it might help.

Thank you for reading.

---

### Post by Navyblue on 2006-01-17
:)

---

### Post by grinias on 2006-01-18
I had the same problem on my laptop, till yesterday. I think that my problem solved but in a very strange way :) Yesterday I found the solution for displaying disk partitions on the desktop --in another thread of the forum. What I had to do was 

$sudo adduser hal disk

in a kosole and then rebooted. I rebooted and shuted down my laptop about 20 times till now, and it seems that the problem has been solved!!! 

Hope that this helps....

---

### Post by Navyblue on 2006-01-18
Grinias,

Does your problem happen all the time or only sometimes?

Anyway I have done what you did and let's see what happen.

Thanks.

---

### Post by Navyblue on 2006-01-18
Well it happens on me twice already so I guess that didn't work for me. :p

---

### Post by bulldogzerofive on 2006-01-19
That used to happen to me too, under mandrake and then hoary, then debian.  It was frustrating as hell, no log files or anything.  It has been a long time since this happened and i do not remember what fixed it (sorry!), but it had to do with X and my video card.  Maybe if you check that everything is configured correctly and you have necessary 3rd party drivers working you will be good to go.

---

### Post by grinias on 2006-01-19
[QUOTE=Navyblue]Well it happens on me twice already so I guess that didn't work for me. :p[/QUOTE]

Yes, it happened again yesterday for me too. But, it happened after i tried to 
suspend to ram, which has not work correctly for me, till now. Maybe this is finally the problem. I know that my problems in suspend to ram are caused partially from the 3D ati driver "fglrx" and/or from kernel and/or BIOS, as the answer of  "bulldogzerofive" implies.

I hope i will be able to find more about it some day :)

Sorry anyway for my previous post, "Navyblue" ...

---

### Post by Navyblue on 2006-01-19
Hey no apologise needed. :)

I use ATI's fglrx driver too. How do I check if it is working correctly?

---

### Post by grinias on 2006-01-20
[QUOTE=Navyblue]Hey no apologise needed. :)

I use ATI's fglrx driver too. How do I check if it is working correctly?[/QUOTE]

If you mean how do you check if fglrx works correctly for suspend to ram or
disk, see my post at
[http://www.ubuntuforums.org/showthread.php?t=112814]("http://www.ubuntuforums.org/showthread.php?t=112814")

I found the solution today and reboot/shutdown problems dissapeared. But maybe this is not the case for you. You see AcerTravelmate is difficult to be
configured because of very bad BIOS information and specialized power management. 

See you...

---

### Post by cblanquer on 2006-01-20
Same problem for me on an IBM Thinkpad T22. Actually it did never stop properly so I had to <Ctrl><Alt><Supr> and press Shutdown button.

Two weeks ago after an upgrade I started failing - at least I do not remember last time.
Maybe try to update your programs and check.

(* This does not apply to suspend I am still not able to wake from *)
 And good week-end , schönes Wochenende & kalw sabatwkyriako   :cool:

---

### Post by Navyblue on 2006-01-20
I don't have the acpi-support package thus I have no /etc/default/acpi-support. I think I removed it on purpose. Does this package have any use for desktop? I might be wrong but this appears to me as only for laptop battery charging and screen lid sensor?

---

### Post by Navyblue on 2006-01-25
Anyone else? :)

---

### Post by Navyblue on 2006-01-26
I logged in through SSH to the PC in question from another PC in network. After which I induced the hang. I can't type anything into the SSH session terminal,  the keyboard appears "frozen". Before the hang I could browse around and it just behaved as normal.

At the same time, I opened up another terminal to start another login session, and I got this:

```
ssh: connect to host xxx.xxx.xxx.xxx port 22: No route to host
```

Would this give any clue at all?

---

### Post by getaceres on 2006-01-28
The hang on shutdown happens to me too.
I'm using the ATI fglrx. I think that's the problem, maybe a bug with fglrx and kdm or something like that.

---

### Post by Navyblue on 2006-01-29
I hope that is the case and will be fixed in the next update or so... :???:

---

