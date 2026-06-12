---
title: "Dell C 400 freezes often after upgrade to 8.04"
date: 2008-04-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hal_bg on 2008-04-28
Dear all,
I have a problem with my laptop Dell C400 after I have upgraded to Ubuntu 8.04. it started to freeze on a regular basis. It rarely takes more than an hour to freeze after reboot. Also while working the screen gets dim sometimes and I have to brighten it manually. So my primary suspect was ACPID and APMD and both were disabled but the freezes continue.

I ran memtest for almost 10 hours tonight with no errors reported. 

Nothing appeared in logs, no errors printed.. just a solid freeze no mouse moving no keyboard, no brightness control.

So any idea what might be wrong? Is there a solution? If no how can I go back to 7.10? 

I have no CD and I am upgrading online since Ubuntu 6.10. This is my workhorse and I need it working again ASAP.

Thanks!
Hal

---

### Post by neptho on 2008-04-29
Hi Hal.

Did you try installing/monitoring i8k to see if it's overheating?

Open a terminal and run:

```
lsmod | grep i8k
```

If it says 'i8k', it is loaded.  If not, edit your /etc/modules, and add 'i8k force=1', then run 'sudo /usr/sbin/update-initramfs -u', and reboot to load i8k.

You may wish to install gkrellm-i8k, and use that to control/monitor your fans, and see if that resolves the problem.

---

### Post by hal_bg on 2008-04-29
Thank you for the suggestion, but no overheating. 
Last freeze happened at 57degC.

I did my best to load it as much as possible, but the temperature never exceeded 71degC.

It made 1h30min uptime, have started to think the problem was solved and I left the laptop for 2-3 minutes and when I came back it was frozen.

Is there any way to downgrade to 7.10? Or any other suggestions.

Hal

---

### Post by embro on 2008-05-09
Hi Hal,

We are several to report the same problem with a Dell C400. There is another thread on this issue (not solved so far):

[http://ubuntuforums.org/showthread.php?t=782904](http://ubuntuforums.org/showthread.php?t=782904)

My colleague told me that he experienced a similar problem a few days ago on his IBM laptop after upgrading to Hardy. For him, a system update was enough to fix it. 

I tried that on my C400, but it seems that it freezes even more often now, sometimes it even happens as soon as the log-in page appears.

Did you find a way to downgrade to 7.10?

---

### Post by daveb272 on 2008-05-25
> **neptho said:**
> Hi Hal.

Did you try installing/monitoring i8k to see if it's overheating?

Open a terminal and run:

```
lsmod | grep i8k
```

If it says 'i8k', it is loaded.  If not, edit your /etc/modules, and add 'i8k force=1', then run 'sudo /usr/sbin/update-initramfs -u', and reboot to load i8k.

You may wish to install gkrellm-i8k, and use that to control/monitor your fans, and see if that resolves the problem.

I have tried this and cant get it to work!

---

### Post by hal_bg on 2008-05-26
dave do not bother with i8k it is not due to overheating. there is a bug in the kernel. For me 2.6.25 works but the sound stopped working properly for some reason.

---

### Post by linkxs on 2008-08-05
hey guys, i was wondering if this was fixed yet

thanks

---

