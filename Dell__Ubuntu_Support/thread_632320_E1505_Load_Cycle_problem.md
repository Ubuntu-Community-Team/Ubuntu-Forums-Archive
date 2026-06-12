---
title: "E1505 Load Cycle problem?"
date: 2007-12-05
forum: Dell  Ubuntu Support
---

### Post by Johnny K on 2007-12-05
I have a Dell E1505n, which came with preinstalled Ubuntu. According to what I read it seems like I might have the load cycle problem, but I wanted to know if anyone could please verify. Here are the results of some smartctl commands:

```
john@zecebeme:~$ sudo smartctl -a /dev/sda | grep Load_Cycle_Count
193 Load_Cycle_Count        0x0032   001   001   000    Old_age   Always       -       462002
john@zecebeme:~$ sudo smartctl -a /dev/sda | grep Power_On_Hours
  9 Power_On_Hours          0x0032   098   098   000    Old_age   Always       -       2251

```

Is 462,002 an extremely high number of load cycles considering I have only had the laptop since June?

Thanks alot. :)

---

### Post by dasunst3r on 2007-12-05
I've had my e1505 since March of this year.  It's gone through Edgy, Feisty, and now Gutsy.  Here's my information:
```

Model Family:     Western Digital Scorpio family
Device Model:     WDC WD800BEVS-75RST0
. . .
9 Power_On_Hours          0x0032   096   096   000    Old_age   Always       -       3575
193 Load_Cycle_Count        0x0032   191   191   000    Old_age   Always       -       29750

```

---

### Post by Johnny K on 2007-12-05
Isn't the average lifespan of a hard drive 600,000 load cycles? How could I have possibly already gone through 462,002?

---

### Post by neilius on 2007-12-05
I had the same issue and it's due to Ubuntu using the silly default power management settings imposed by the HD's firmware. Just download the Hitachi Feature Tool: [http://www.hitachigst.com/hdd/support/download.htm#FeatureTool]("http://www.hitachigst.com/hdd/support/download.htm#FeatureTool")

...and use it to disable Power Management stuff. You could also disable Acoustic Management to make the drive a little faster at the expense of louder seek noise (although it is only a little bit louder).

Regards,

Neil.

---

### Post by Johnny K on 2007-12-05
But my drive is already practically dead. I'm up to 460,000 cycles out of an expected 600,000. Considering I didn't do anything to cause this to happen, isn't this a huge problem? What is going to happen when in just a few months hundreds of Dellbuntu hard drives presumably fail?

I am just wondering why a bigger deal isn't being made of this. The bug was first filed over a year ago, and has received considerable attention from slashdot, etc for more than a month. Why hasn't it been fixed?

I certainly don't mean to complain. I have a warranty from Dell so I should be ok, if a little annoyed. If anything, I'm worried for Ubuntu and feel like this could hurt its adoption.

---

### Post by cameroncox on 2007-12-06
```
  9 Power_On_Hours          0x0032   091   091   000    Old_age   Always       -       3831
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       55171
```
Mine seems pretty low (E1505n), (I've had it since June '07), but I also keep it on AC power most of the time. (90% on AC, 10% on battery)

I also made a change to let laptop-mode-utils control the hard driver power management settings.
```
cameron@antilles:/usr/src/laptop-mode-tools-1.34/etc/laptop-mode$ diff laptop-mode.conf /etc/laptop-mode/laptop-mode.conf 
49c49
< VERBOSE_OUTPUT=0
---
> VERBOSE_OUTPUT=1
216c216
< CONTROL_HD_POWERMGMT=0
---
> CONTROL_HD_POWERMGMT=1
```

---

### Post by Johnny K on 2007-12-08
> **cameroncox said:**
> ```
  9 Power_On_Hours          0x0032   091   091   000    Old_age   Always       -       3831
193 Load_Cycle_Count        0x0032   095   095   000    Old_age   Always       -       55171
```
Mine seems pretty low (E1505n), (I've had it since June '07), but I also keep it on AC power most of the time. (90% on AC, 10% on battery)

That's weird. If we have both had E1505n for the same amount of time and neither one of us uses battery power much, why is mine going through so many more load cycles than yours? And when I say "so many more", I mean 837% as many.

---

### Post by Dennis N on 2007-12-09
The load cycles also increase in AC operation because of the APM. My Dell 1505N had amassed nearly 73900 load cycles when I first checked after hearing of this issue (maybe 6 weeks ago). I estmate 150 per hour. This is almost all AC operation. One manifestation of this is a clicking from the hard drive every 20 seconds or so, regardless of power mode being AC or battery.

A good summary of the problem and workarounds are on the launchpad bug report site at:

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

For Ubuntu the importance is stated as critical.

After researching, I decided to disable APM using hdparm about a month ago, and since that time, the load cycles increase only by 1 each day (not each hour) and the annoying clicking was silenced completely. The ways to do this are described in the bug report and other threads on this issue which can be found. Note: I used hdparm -B 255 /dev/sda and it worked for me. Others say to use 254 as the parameter to disable.

In my case, I was comfortable with disabling APM completely, but this choice depends on one's individual circumstances.

---

### Post by Johnny K on 2007-12-09
Thanks for the info. But now that my hard drive is practically dead, what do I do? Should I just let the hard drive die down completely and then have Dell replace it under warranty? Or should I just ask Dell to replace the drive because of the clicking sound it is making. Would Dell replace the drive because of something that is caused by a software issue?

---

### Post by Dennis N on 2007-12-09
I don't know the expected life in terms of load cycles of your drive, but if your information of 600,000 lifetime load cycles is true, that probably gives you 100,000+ remaining load cycles based on your count (462,000)  shown in your first post. Since I disabled APM, the load cycle count is increasing only by 1 each power on. This has been the case for about a month now. 

Theoretically, at that rate of increase, 100,000 more power ons with let's say 2 power ons each day, gives you 50,000 days or nearly 137 years until that assumed 600,000 lifetime figure is reached.

---

### Post by Johnny K on 2007-12-09
> **Dennis N said:**
> I don't know the expected life in terms of load cycles of your drive, but if your information of 600,000 lifetime load cycles is true, that probably gives you 100,000+ remaining load cycles based on your count (462,000)  shown in your first post. Since I disabled APM, the load cycle count is increasing only by 1 each power on. This has been the case for about a month now. 

Theoretically, at that rate of increase, 100,000 more power ons with let's say 2 power ons each day, gives you 50,000 days or nearly 137 years until that assumed 600,000 lifetime figure is reached.

So do you think the drive would have to actually die before Dell replaces it?

---

### Post by Dennis N on 2007-12-09
I can't speak to Dell policies, and am only guessing here (could be totally wrong).  I would think that unless the drive has actually failed within your warranty period, they would not replace it. 

The choice for anyone noticing this problem seems to be do nothing and risk a far earlier than normal drive failure, or manage the APM to reduce the load cycle count rate of increase. I just didn't see any downside for disabling it in my case. 

Even your drive with its > 400,000 load cycle count can be expected to last for a long time with the APM disabled as the theoretical calculation of my last post suggests.

---

### Post by Johnny K on 2007-12-10
Thanks alot for the suggestion! I think I will just disable APM and hope it's not too late.

How exactly did you do it? It seems like you just did **hdparm -B 255 /dev/sda** in terminal, but the comments of the bug report say that you should also edit hdparm.conf because using the terminal command alone will allow the settings to revert after a hibernation.

---

### Post by Dennis N on 2007-12-10
You can enter the command in the terminal at any time and the effect is immediate. It works like a switch.

sudo hdparm -B 255 /dev/sda

and enter your password. That should do it. It will be in effect for the remainder of your current session.  You can then verify that the load cycle count stops increasing with smartctl. 

Yes, the command has to be executed during or after startup to work for that session. To get automatic execution of the command, the fix is to make a script as described here:

[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695/comments/14)

and then it should be automatically executed at startup.

---

### Post by Johnny K on 2007-12-10
Great! Thanks for the info!

And now to the other issue. What will this mean for Ubuntu? Certainly most users aren't going to enable the fix, so do you expect that within the next few months there will be widespread hard drive failure and a big panic? Whether there is widespread failure or not, will this issue greatly hurt Ubuntu's reputation?

---

