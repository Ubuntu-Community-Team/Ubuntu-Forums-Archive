---
title: "Ubuntu 19.04 Slow"
date: 2019-05-06
forum: Desktop Environments
---

### Post by ping-wu on 2019-05-06
Without going into details such as hardware etc, I want to point out that Ubuntu 19.04 is awfully slow, to the extent that I have to grub back to 18.04.2.

Has anyone experienced the same slowness?

---

### Post by oldfred on 2019-05-06
See also, various issues:
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453)
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)

After most of the changes mentioned in threads above my SSD boots quicker:
fred@Bionic-Z170N:~$ systemd-analyze
Startup finished in 3.089s (kernel) + 9.246s (userspace) = 12.336s
graphical.target reached after 9.223s in userspace

Was on the order of 30+ sec.

19.04 on HDD still slower, not sure if I implemented all the settings changes, yet or not, or if just because HDD.

---

### Post by ping-wu on 2019-05-06
The biggest problem I am having with 19.04 vis-a-vis 18.04.2 (and everything else such as 19.10 budgie) is that Chrome is very slow.

---

### Post by wojciech-chojnacki on 2019-05-13
Yes, I have also experienced a similar problem with Ubuntu 19.04

---

### Post by nikt3 on 2019-05-14
I am not sure if that's because of update, but looks like same story for xubuntu updated from 18 to 19. I have dual boot with ubuntu 16 and it works the same, fine, faster.

---

### Post by ping-wu on 2019-05-19
> **nikt3 said:**
> I am not sure if that's because of update, but looks like same story for xubuntu updated from 18 to 19. I have dual boot with ubuntu 16 and it works the same, fine, faster.

My was a fresh install (never a fan of version upgrade).

---

### Post by ping-wu on 2019-05-25
installed 19.10 daily built, much faster than 19.04!!!

---

### Post by amano on 2019-05-29
The combination GNOME and Firefox on 19.04 is faster than any GNOME before  on my machine. 
Can this be a Chrome issue? What about Chromium?

---

### Post by ping-wu on 2019-05-29
> **amano said:**
> The combination GNOME and Firefox on 19.04 is faster than any GNOME before  on my machine. 
Can this be a Chrome issue? What about Chromium?

Yes, this is a Chrome issue!  I tried Chromium, strangely, it started OK but then it began trudging, just like Chrome.
c
Ubuntu 19.10 also crashed a couple of times, both occurred when running Chrome.  Running Chrome in 19.04 was painfully slow, but no crash.

---

### Post by &amp;wP*!) on 2019-06-07
[LIST=1]
[*]To speed up the things in general: If your computer has enough RAM, swap usage can be reduced. This can be achieved by adding **vm.swappiness=1** at the end of **/etc/sysctl.conf**.
[*]Analyze the boot procedure by the command **systemd analyze critical-chain**. I doubt you can save something there, but just  in case. 
[*]To speed up the browser, you can use memory as cache, not harddisk. You can also use  the RAM disk as a cache, i.e. tmpfs. Enablle the options to empty the cache before exiting the browser application.
[*]Use a more lightweight distro like Lubuntu. Its memory footprint is very small, thus achieving another speed gain.
[/LIST]

If you had already looked at these things, ignore this post.

---

### Post by rafael-a-faria on 2019-08-28
Hello,

I don't know if this applies to you, but I felt that ubuntu was really slow and was annoyed because I have a pretty good computer, one thing that I did that completely change my experience was installing the CompizConfig and change the behaviour for Static Application Swicher.

You can download Compiz with apt get, open the application using the GUI, and in the left panel -> Windows Management -> Static Application Switcher -> Behaviour (tab)
Set the speed to the MAX possible (50), timestamp around 9, Popup windows delay set to 0.

I hope this help you.

---

### Post by adbask2 on 2019-08-30
> **ping-wu said:**
> Without going into details such as hardware etc, I want to point out that Ubuntu 19.04 is awfully slow, to the extent that I have to grub back to 18.04.2.

Has anyone experienced the same slowness?

I have a pretty fast machine I used it with windows 7 and it was extremely fast, however the minute I installed Ubuntu 19.04 it's now crawling and it is driving me insane, to say I am disappointed by Ubuntu is an understatement of the year, it's with a heavy heart that I am leaving it, and the same applies to Firefox, it's with great sadness that I am going back to Chrome which I really despise anything to do with Google or Microsoft.

And the sluggishness is not the only thing wrong with it, frequent freezing of applications, also the fact that practically every application you click on takes up to a minute to appear.
I have been using Ubuntu since the very first one 15 years ago, I can't use windows 10 if you paid me, so I have no other option but to use Win7.

---

### Post by Autodave on 2019-08-30
I would try 18.04 before running away.  There are a lot of posts here with issues pertaining to 19.04, but I really don't see any about 18.04 and slowness issues.

You didn't give us info on your system, but Ubuntu, especially with Compiz, may be way too heavy.  I use Xubuntu on a variety of machines here with no issues.

---

