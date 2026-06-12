---
title: "gvfsd process - Memory leakage?"
date: 2009-05-07
forum: General Help
---

### Post by MysticalRiotCandy on 2009-05-07
Running 9.04 Jaunty on 2 GB of RAM.  The process 'gvfsd' is eating up my memory, quickly and horrifyingly so.  It grew from 18 MB to 1.2 GB of usage in a manner of minutes.  On Hardy and Intrepid, I did not run into this problem.  I've tried killing the process repeatedly.  This works temporarily, but it starts back up again and starts eating my memory.  This gets extremely problematic when I'm running virtualized machines, or leaving it on as my ssh server.  
I would like to know:

1) What does this process actually do
2) Why is it consuming my RAM?
3) How can I resolve this issue?

Regards.

---

### Post by jawvvd on 2009-06-30
I have this too, in Jaunty..

gvfsd ate up all RAM and swap..

---

### Post by lduperval on 2009-07-28
I'm seeing this also. Any ideas? I'm on Jaunty.

L

---

### Post by HankB on 2009-09-20
Me too. I found that gvfsd had consumed all available RAM and swap on my system. I filed a bug report ([https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/433500](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/433500).)

If you have any further information on this, please add it to the report.

thanks,
hank

---

### Post by mattman on 2009-10-17
I am experiencing this problem also. Has anyone found a solution to the problem?

Edit: apparently rebooting fixes the problem, at least temporarily. It would be nice to know what caused the leak in the first place though.

---

### Post by burgechris on 2010-01-04
Ditto...Virtual Memory is 6.2 gigs and Resident is 4.7 gigs...no apps open

---

### Post by llawwehttam on 2010-01-04
Hmmm I have Karmic and I had a similar problem on 64 bit with udevd. I have 4GB ddr3 ram and a 5GB swap and It was on 100%. I used ```
killall udevd
``` and I have never had the same problem again.

I suggest upgrading to karmic.

---

### Post by Anubis on 2010-01-19
> **llawwehttam said:**
> **5GB swap**

:lolflag:

BTW, upgrading to Karmic is not a solution.Nor is killing udev a sane option.

---

### Post by Exüberance on 2010-03-10
Take all disks out of your CD/DVD drives. That fixes it for me. (You don't get your memory back, but it stops increasing)

Apparently gvfsd has a rather embarassing bug which causes it to leak memory forever if you have a CD in your CD drive. I'm amazed this hasn't been fixed yet. *Almost* as bad as Windows updates lol

---

### Post by dustinsilva on 2010-03-16
I had this same issue, and it was because I was running Windows 7 in Virtual Box - with my iPhone plugged in....  I physically unplugged the phone, ended the GVFSD process, and plugged the phone back in, and the file didn't continue to grow like it had been growing...  ~update~ a few minutes later the file popped back up and continued to grow larger... as soon as I unplug the phone, it stops.... but then when its plugged in, it eventually starts getting larger..

---

### Post by foxmajik on 2010-03-19
> **Exüberance said:**
> Take all disks out of your CD/DVD drives. That fixes it for me. (You don't get your memory back, but it stops increasing)

Apparently gvfsd has a rather embarassing bug which causes it to leak memory forever if you have a CD in your CD drive. I'm amazed this hasn't been fixed yet. *Almost* as bad as Windows updates lol

This worked for me as well.

I found that this problem happens with the version of gvfsd that you have to install to use iPod Touch or iPhone with Ubuntu.

---

### Post by Eul_Mulot on 2010-04-23
Same problem for me, really embarrassing when I plug in my iPod Touch. Unplug it as say before and kill the buggy gvfsd. 

Any idea if this issue will be solved with Lucid ?

---

### Post by el.pescado on 2010-04-29
Quite funny - just experienced it too on openSuse. I had running Windows XP in VirtualBox and iPod Touch plugged in.

---

### Post by Affendi on 2011-02-21
I had the same problem using Ubuntu 10.04 (Lucid), I just wanted to add that I wasn't running Windows XP on virtual box but simply had my Sansa Clip plugged in.  I also found that I couldn't close system monitor except by force quit.

---

### Post by lite1979 on 2011-03-22
Using 10.04 LTS and just happened to me. Funny thing is I never noticed it until today, which just so happens to be my first time using the Gnome System Monitor. I've had a CD in the DVD-RW drive for a month with no problems until now. Coincidence?

---

### Post by Throne777 on 2011-05-16
> **lite1979 said:**
> Using 10.04 LTS and just happened to me. Funny thing is I never noticed it until today, which just so happens to be my first time using the Gnome System Monitor. I've had a CD in the DVD-RW drive for a month with no problems until now. Coincidence?

I always have a CD in my disc drive (my hardware's screwy, if I don't have one in there, the drive fails to open -takes about 50 attempts to get it open)
Suddenly gvfsd-photo2 ate 920MB of RAM for no reason whatsoever. I'm also running 10.04. I only noticed the huge leak because I monitor RAM, CPU & internet activity.
Far as I know, this is the only time it's happened.

---

