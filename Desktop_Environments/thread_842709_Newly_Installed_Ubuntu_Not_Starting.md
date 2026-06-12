---
title: "Newly Installed Ubuntu Not Starting?"
date: 2008-06-27
forum: Desktop Environments
---

### Post by mirchichamu on 2008-06-27
I installed Ubuntu. I am new to Ubuntu.Everything was ok. I started windows. after that I wanted to switched to Ubuntu. But it is not starting.It goes beyond the boot screen, But then stop before putting the user name and pass. Only there are lines on screen.

I am in trouble. I don't know what to do? Please help me.

---

### Post by overdrank on 2008-06-28
> **mirchichamu said:**
> I installed Ubuntu. I am new to ubuntu.Everything was ok. I started windows. after that I wanted to switched to ubuntu. But it is not starting.It goes beyond the boot screen, But then stop before putting the user name and pass. Only there are lines on screen.

I am in trouble. I don't know what to do? Please help me.

Hi and are you able to boot into recovery mode? It is usually the second choice from the grub when booting. If you boot recovery mode then you can try the command startx.

---

### Post by mirchichamu on 2008-06-28
Thanks a lot. I tried that several times but of no use. I tried even to reinstall but that also failed. It is not going beyond Location.

I need further help pleaase.

---

### Post by overdrank on 2008-06-28
> **mirchichamu said:**
> Thanks a lot. I tried that several times but of no use. I tried even to reinstall but that also failed. It is not going beyond Location.

I need further help pleaase.

Hi and could you give us some system specs?
 Have you checked the cd for errors and also MD5SUM
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Samhain13 on 2008-06-28
Lines... could it be that your monitor is out-of-sync? When you hit CTRL-ALT-F1 can you get to a terminal screen?

---

### Post by mirchichamu on 2008-06-28
> **overdrank said:**
> Hi and could you give us some system specs?
 Have you checked the cd for errors and also MD5SUM
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Thanks overdrank for your support. My computer Fujitsu-Siemens laptop with 1.7 centrino processor, 512 Ram and 80 GB Hard Disk.

Sorry I could not understand your MD5SUM, and how to check.

---

### Post by mirchichamu on 2008-06-28
> **Samhain13 said:**
> Lines... could it be that your monitor is out-of-sync? When you hit CTRL-ALT-F1 can you get to a terminal screen?

Thanks Samhain13 for your support. I didnot know that. At present I am on this forum through Windows. I will switch over to my desktop so that whaatever you ask, I can do that.

---

### Post by Samhain13 on 2008-06-29
So, what's happened? Were you able to get into a terminal by doing CTRL-ALT-F1?
Because if you can, I was going to suggest reconfiguring your x-server by typing (after you login):

```

sudo dpkg-reconfigure xserver-xorg

```

That will provide you with a walk-through (like a wizard) for setting-up yung xorg.conf. Hopefully, you can get to the Ubuntu graphical login screen when you're done.

Good luck. :)

---

### Post by mirchichamu on 2008-06-29
> **Samhain13 said:**
> So, what's happened? Were you able to get into a terminal by doing CTRL-ALT-F1?
Because if you can, I was going to suggest reconfiguring your x-server by typing (after you login):

```

sudo dpkg-reconfigure xserver-xorg

```

That will provide you with a walk-through (like a wizard) for setting-up yung xorg.conf. Hopefully, you can get to the Ubuntu graphical login screen when you're done.

Good luck. :)
 Thanks a lot Mr.Samhein13.
Yesterday I was busy with configuring my laptop until late night. Ultimately I succeeded to reinstall Ubuntu,because I was unable to log on.I tried whatever was suggested.

I am on my laptop now.But ubuntu will take time to learn properly. I am not familiar with the terminology. There are many packages available. I don't know what they are for? How can I select the packages?etc etc.

---

### Post by Samhain13 on 2008-06-29
Ah. Yeah, it's going to take some time to get comfortable. I've been using Ubuntu for the last couple of years and I still don't know a lot, just enough to get some work done.

As for the packages, it really depends on what you want to work on. You will notice that under the Applications mune, there's Add/Remove at the bottom. The applications that you can install/remove are grouped according to what you can use them for, like graphics, programming, etc. And clicking on one of the choices will give you a short description of that particular choice. To select, just click on the check box beside the choice, then click "Apply Changes".

You can try things out, keep what you like and remove what you don't like. :)

---

