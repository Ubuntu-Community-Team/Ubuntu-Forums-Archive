---
title: "Slow boot w/ Ubuntu 7.10 on Dell Inspiron 600m"
date: 2008-02-22
forum: Dell  Ubuntu Support
---

### Post by scarsunseen on 2008-02-22
Hi,

Right now I'm dual-booting Win XP Pro and Ubuntu 7.10 on my Inspiron 600m. This is a new (old) laptop that was a hand-me-down and was "broken", which I fully repaired. The power connector just needed to be re-soldered to the motherboard.

XP loads MUCH faster than Ubuntu. It takes Ubuntu up to 2 or 3 minutes to fully load, but everything works perfectly otherwise. I even upgraded the RAM from 512MB PC2700 SODIMM to 1gb, but the boot-time is approx the same.

My hard drive is a 60gb IDE hdd @ 5400rpm, so I doubt that's an issue, especially since XP boots quick (under 1 min).

I think it might be a RAM issue. The PC2700 RAM is only running at 2.0 CAS @ 133mhz according to CPU-Z.

Any idea what the problem is?

Thanks,
Jaime

---

### Post by SpiderGorilla on 2008-02-23
RAM could be the issue. It could also be a matter of configuration. If Ubuntu has more to load, then it's going to take longer.

Of a curiosity, are you using LILO or GRUB for boot-loading?

---

### Post by Mauriland on 2008-02-23
Hi,

I have the same problem, I'm running Kubuntu 7.10 on a AMD64 (i have the problem with i386 and x64 edition) Athlon XP 1.7GHz 1024MB RAM.
The boot is terribly slow (2-3 minutes), but after the login all work right and quickly. I don't see the splash screen (during boot) too.
I use GRUB,

Thanks,

Mauro

---

### Post by SpiderGorilla on 2008-02-23
Hmm. How long ago did these slow-downs begin occuring?

---

### Post by scarsunseen on 2008-02-23
I use GRUB. Could that be the issue? I have no problem using GRUB as the OS selector on my main system (which has 6gb PC2-6400 RAM and AMD Athlon X2 5200+), but that's much much more powerful than this laptop. I'm running Ubuntu 7.10 x64 on my main system, but x86 on this laptop. I hope that helps.

Oh, and the slow boot-time occurred from the beginning ever since installing Ubuntu. I installed XP Pro first, then partitioned with Acronis Disk Director, then installed Ubuntu.... same process as my main system.

Is it possible that my swap partition is too small? I made it 2gb, which should be large enough, right?

---

### Post by Beefeater on 2008-02-23
You might want to activate verbose and maybe you can see where (and if) the loading stops at a specific place.

---

### Post by scarsunseen on 2008-02-23
Verbose? I'm not sure how to do that. I'm pretty new to Ubuntu honestly.

---

### Post by midnightray on 2008-02-24
When booting do you see the splash screen or text or a blank black screen. A friend had a problem with slow booting too. If its a blank screen its because when ubuntu installed it set the screen resolution for the splash screen too high. In case this is the problem, I posted the solution on my blog at: [http://phils-ubuntu-blog.blogspot.com/2008/02/ubuntu-710-black-screen-on-startup.html](http://phils-ubuntu-blog.blogspot.com/2008/02/ubuntu-710-black-screen-on-startup.html)

---

### Post by Beefeater on 2008-02-24
> **scarsunseen said:**
> Verbose? I'm not sure how to do that. I'm pretty new to Ubuntu honestly.

It should be something like this.

1. When grub is starting press Esc
2. Press 'e' to edit the highlighted kernel.
3. Go to kernel .. and press 'e'.
4. Change splash to nosplash and hit Enter.
5. Press 'b'

---

### Post by scarsunseen on 2008-02-24
> **midnightray said:**
> When booting do you see the splash screen or text or a blank black screen. A friend had a problem with slow booting too. If its a blank screen its because when ubuntu installed it set the screen resolution for the splash screen too high. In case this is the problem, I posted the solution on my blog at: [http://phils-ubuntu-blog.blogspot.com/2008/02/ubuntu-710-black-screen-on-startup.html](http://phils-ubuntu-blog.blogspot.com/2008/02/ubuntu-710-black-screen-on-startup.html)

I did this and it improved the boot-time from about 3 minutes to 1 minute, which still seems pretty slow. XP loads in about 25-30 seconds.

---

### Post by SmallFish on 2008-02-25
I suspect the issue with your hard drive since it boots extremely slow for both windows and ubuntu. It has nothing to do with swap. I do not even have swap at all, just running everything out from 2 gig memory. Just need to reboot every couple weeks to reclaim some runaway processes. Anyway, my boot time somewhere 30 to 40 seconds and i have a 7200 rpm hd. I am not sure if you can see what's running during boot, mine does failed once awhile saying something like "../sda..failed to mount for 30 times" and it will starting to scan for it but never an issue. It just take about 2 minutes for the scanning. 

So, look into your syslog for issues like that.


If it's not your hd then your laptop must be trying to load some unnecessary stuffs.

---

### Post by grenet on 2008-02-26
i've had the exact same problem with a 7.10 copy on my 600m.  It takes sometimes up to five minutes to load for me.  I'll try to edit the kernel with the solution above, but I wanted to toss my two cents in as well.

I'm not dual booting either, just a straight 7.10 install on a old corrupted 600m machine...

---

### Post by scarsunseen on 2008-02-27
Well I actually said that XP loads much faster than Ubuntu, therefore it probably is not a problem with the hard drive. The hard drive is brand new too. Like I said in a previous post, XP loads in about 30-40 seconds. Before changing the resolution of Ubuntu's splash screen, it booted in about 3 minutes. After changing the resolution, it's down to about 50-60 seconds.

---

### Post by midnightray on 2008-02-27
Ok so long time since i replied to this thread. My idea of fixing the splash screen worked.

The splash screen hides the scary linux text, which does show what is slowing your boot up.

My next recommendation is to enable boot charts. During startup it will log what goes and and for how long and make a nice image.

To install this type (in terminal)

sudo apt-get install bootchart


On your next startup it will record and make an image. This is is found at:

/var/log/bootchart

Easiest way is to go Places -> My Computer and navigate to it or type in the address bar.

A sample of my reasonable boot time, on my old slow laptop :)

---

### Post by him610 on 2008-02-28
> The splash screen hides the scary linux text, which does show what is slowing your boot up.

Actually, I have always preferred to watch the text messages scroll up the screen as I found them informative, and one could see what was happening in the boot process. But then again, I always found comfort in listening to the screech of a dial-up modem as it connected and went through its handshake routine with the ISP's distant modem. 

That was a good tip on fixing the black screen; it works for desktops too. Thanks Phil.

---

### Post by dpant on 2008-02-28
Same problem with ubuntu 7.10 dual booting on an Fujitsu-Siemens M1451G. More than 3 mins before fixing splash screen, about 30 secs afterwards. Thanx for the splash fix tip, btw. Bootchar is nice too but it just shows me that my laptop is slower than midnightray's.

Out of curiosity, why a resolution mismatch would slow down the boot time that much?

---

### Post by midnightray on 2008-02-28
Seems to be a common bug with the installer for laptops being too aggresive with the resolutions.

I can only think that it gets stuck into somesort of loop trying resolutions and then gives up. No real expert on linux. Less than a month old convert. :)

I found on my friends bootchart that a service CUPSD (or similar) (for printing) really slowed his boot time. The charts a great way to see the problem without digging through logs.

Once you see if a service is a problem goto google and do a bit of research. More than likely someone in the past has had the same problem.

---

