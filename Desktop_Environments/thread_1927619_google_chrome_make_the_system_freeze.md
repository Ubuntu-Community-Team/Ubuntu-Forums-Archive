---
title: "google chrome make the system freeze"
date: 2012-02-18
forum: Desktop Environments
---

### Post by oren tal on 2012-02-18
Hi,

I am using ubuntu 11.10 and lately sometime when I use google chrome the system freeze.

The mouse don't even move.

Only hard reset solve the problem.

Now one thing is that google chrome freezing, anther is that the whole system freeze.

Why is that ?

And did anyone else had the same problem?

---

### Post by 2F4U on 2012-02-18
Any other applications running at the same time? Does it happen on particular web sites (maybe a flash issue)? Do you have the same problems with other browsers?

---

### Post by oren tal on 2012-02-19
> **2F4U said:**
> Any other applications running at the same time? Does it happen on particular web sites (maybe a flash issue)? Do you have the same problems with other browsers?

It usually happen when I watch movie in youtube.

One thing is if google chrome has problem, anther is if the whole system freeze.

It is not the google chrome that freeze but the whole system.

It happen even if I watch youtube html 5 video (no flash).
Anyway I believe it is a combination of chrome and instability in ubuntu.

I hope that they will solve the problem in next update.

Is anyone else has the same problem?

---

### Post by Jussl on 2012-02-25
Do you use nvidia video drivers?
Look at kernel logs (/var/log/kern.log) is there lines like this:
INFO: task kworker/2:2:2380 blocked for more than 120 seconds.

Maybe we have same issue:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/941195](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/941195)

---

### Post by oren tal on 2012-02-26
> **Jussl said:**
> Do you use nvidia video drivers?
Look at kernel logs (/var/log/kern.log) is there lines like this:
INFO: task kworker/2:2:2380 blocked for more than 120 seconds.

Maybe we have same issue:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/941195](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/941195)

I am using Nvidia video driver.

However I have not find you error message, I did find the following:
```
Feb 26 22:03:49 oren-computer kernel: [   25.373491] input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input7
Feb 26 22:03:49 oren-computer kernel: [   25.373564] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input8
Feb 26 22:03:49 oren-computer kernel: [   25.373604] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input9
Feb 26 22:03:49 oren-computer kernel: [   25.373643] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input10
Feb 26 22:03:49 oren-computer kernel: [   25.373960] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Feb 26 22:03:49 oren-computer kernel: [   25.373967] nvidia 0000:01:00.0: setting latency timer to 64
Feb 26 22:03:49 oren-computer kernel: [   25.373971] vgaarb: device changed decodes:
```

I am not sure if this is from the time of the freeze or not.

But it was not always, at start after the one of the latest update.

---

### Post by LinuxFan999 on 2012-02-26
Does the system freeze when using Firefox, or only with Chrome?

---

### Post by oren tal on 2012-02-27
> **LinuxFan999 said:**
> Does the system freeze when using Firefox, or only with Chrome?

only with chrome or chromium.

I can use firefox or opera to watch video and it doesn't freeze.

---

### Post by Jussl on 2012-02-28
> **oren tal said:**
> only with chrome or chromium.

I can use firefox or opera to watch video and it doesn't freeze.


When it's frozen can you get to terminal with Ctrl + Alt + F1 (Ctrl + Alt + F7 gives desktop back)?

There should be something in logs, usually even in case of total freeze.
Did you look from old logs (kern.log.2.gz, kern.log.3.gz, etc)?

Do you have 64bit system?

I suspect nvidia drivers, they seems to be really unstable.

---

### Post by Draxstyle on 2012-02-28
Maybe a dumb question, but do you have the adobe flash plugin installed/updated?

---

### Post by Draxstyle on 2012-02-29
Oh sorry, now I saw that a similar question already had been asked and then I saw the command lines.... 

Yeah, I'd say the same...**Nvidia drivers...**
[/COLOR][/COLOR]Always a huzzle when it comes to Linux?? 

Not that I would personally know, ATI <3 h3h3

/Dra

---

### Post by Jussl on 2012-02-29
> **Draxstyle said:**
> 

Yeah, I'd say the same...**Nvidia drivers...**
[/COLOR][/COLOR]Always a huzzle when it comes to Linux?? 

Not that I would personally know, ATI <3 h3h3

/Dra


I never had video driver problems until 11.10.

---

### Post by Draxstyle on 2012-02-29
Have you considered using the 10.10 instead?

---

