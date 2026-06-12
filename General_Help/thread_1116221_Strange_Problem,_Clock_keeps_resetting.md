---
title: "Strange Problem, Clock keeps resetting"
date: 2009-04-04
forum: General Help
---

### Post by casmok on 2009-04-04
We recently changed our clocks, i.e put them one hour forward for summer. I changed it on the PC too.

Several time now I boot up and find the clock on my PC has reverted back one hour to winter time. Whats strange is that this is happening in both Ubuntu and Windows on the other partition which make me wonder if its something to do with the WiFi router? 

This just happened again so I booted into Windows to check. Sure enough there too so I changed it back to correct time. Then when I came back to Ubuntu it was changed here as well. Anyone know what going on and why?

Mike

---

### Post by ukblacknight on 2009-04-04
This **could** be something to do with the clock on your BIOS.  It's strange that two different OS's would do that.

If you know how, I'd suggest you have a look in your BIOS to see what the system time is, it may not be updating accordingly.

---

### Post by linuxuser21 on 2009-04-04
> **ukblacknight said:**
> This **could** be something to do with the clock on your BIOS.  It's strange that two different OS's would do that.

If you know how, I'd suggest you have a look in your BIOS to see what the system time is, it may not be updating accordingly.

If it was the BIOS, which I'm pretty sure it is, it would probably be because of your battery.  In that case, all you need to do is buy a new one.

---

### Post by ukblacknight on 2009-04-04
> **linuxuser21 said:**
> If it was the BIOS, which I'm pretty sure it is, it would probably be because of your battery.  In that case, all you need to do is buy a new one.

I was thinking on the lines of the battery as well, I've heard about that problem a long long time ago, just wasn't sure if it was still a problem in todays day & age!

---

### Post by linuxuser21 on 2009-04-04
> **ukblacknight said:**
> I was thinking on the lines of the battery as well, I've heard about that problem a long long time ago, just wasn't sure if it was still a problem in todays day & age!

Lol, definitely.  The newer ones, you don't have to worry about as much because they are more efficient; however, a battery is a battery, and they will go dead eventually.

---

### Post by casmok on 2009-04-04
> **linuxuser21 said:**
> If it was the BIOS, which I'm pretty sure it is, it would probably be because of your battery.  In that case, all you need to do is buy a new one.

All looks OK in the bios set up
OK maybe the battery but if that the case why would the clock go back **exactly** one hour, i.e back to winter time? and why when I changed it back to summer time in windows would it also then be changed in Ubuntu?

---

### Post by ukblacknight on 2009-04-04
> **casmok said:**
> All looks OK in the bios set up
OK maybe the battery but if that the case why would the clock go back **exactly** one hour, i.e back to winter time? and why when I changed it back to summer time in windows would it also then be changed in Ubuntu?

The winter time is the normal time, where summer time is where they changed the clocks in WWII.  It looks like the BIOS is not recognising the time change, either it's not writing properly or because the battery is low, it's reseting it to the default, winter time.

We figured it was the BIOS because both Ubuntu and Windows are behaving in the same mannor, meaning that it's very unlikely it is a fault with the OS.

How old is your laptop?

---

### Post by casmok on 2009-04-04
> **ukblacknight said:**
> The winter time is the normal time, where summer time is where they changed the clocks in WWII.  It looks like the BIOS is not recognising the time change, either it's not writing properly or because the battery is low, it's reseting it to the default, winter time.

We figured it was the BIOS because both Ubuntu and Windows are behaving in the same mannor, meaning that it's very unlikely it is a fault with the OS.

How old is your laptop?

Two years old. OK maybe I should look at a new battery. It not a mega problem at this stage more a minor anoyance!

---

### Post by CatKiller on 2009-04-05
I'm surprised no one has mentioned the solution; it's a fairly common thing. The UNIX way (which Linux uses as its default) is to have the hardware clock set to UTC and do the translation into local time in the OS. The Windows way is to have the hardware clock set to local time. If you have both on the same computer, and your local time isn't UTC, then they both interpret the clock differently. There's probably some way to get Windows to use UTC for the hardware clock, but I don't know what it is, so I'll tell you how to get Linux to not use UTC.

```

sudo nano /etc/default/rcS

```

find the line about UTC and change it:

```

# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=no

```

FWIW, this defaults to UTC=no in Intrepid, since dual-booters found it confusing.

---

### Post by casmok on 2009-04-05
> **CatKiller said:**
> I'm surprised no one has mentioned the solution; it's a fairly common thing. The UNIX way (which Linux uses as its default) is to have the hardware clock set to UTC and do the translation into local time in the OS. The Windows way is to have the hardware clock set to local time. If you have both on the same computer, and your local time isn't UTC, then they both interpret the clock differently. There's probably some way to get Windows to use UTC for the hardware clock, but I don't know what it is, so I'll tell you how to get Linux to not use UTC.

```

sudo nano /etc/default/rcS

```

find the line about UTC and change it:

```

# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=no

```

FWIW, this defaults to UTC=no in Intrepid, since dual-booters found it confusing.

Hmmm..Interesting. Thanks
What I did not mention earlier is that I'm not at home in the UK right now. I actually in Southern California for a couple of months. So the clock has been resetting back one hour to Pacific Standard Time. We changed clocks forward here at the beginning of March. I guess its likely the battery from what people say since it doesnt happen every time (since yesterday its not happened again). The thing that still puzzles me was when I corrected it in Windows XP and booted back to Ubuntu it was then corrected here as well
Mike

---

