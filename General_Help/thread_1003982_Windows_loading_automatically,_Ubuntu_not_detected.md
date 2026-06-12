---
title: "Windows loading automatically, Ubuntu not detected)"
date: 2008-12-06
forum: General Help
---

### Post by ktzqbp on 2008-12-06
Hi guys,

I was messing around with a live usb slackware distro install (BackTrack 3) on my MSI Wind U100, and while it was booting, it froze up due to a bad command I entered into its syslinux.cfg. Anyway, I manually power off the netbook, and when I try to boot back up to hard drive (which would previously load GRUB, showing two different Ubuntu 8.10 Kernels (2.6.27 and .29 iirc), Windows XP and Windows Restore), I'd get the descriptive error 'L 01 01 01 01...'.

So, I boot up from another USB to fix my BackTrack 3 live install's syslinux.cfg. I do all that, get BackTrack 3 working again, and research the L 01 ... problem. I find out I need to issue the command 'lilo -M /dev/sda' from within BackTrack 3.

I do that, and now I have Windows booting up. My new problem, however, is that Windows is now booting up automatically - without detecting Ubuntu.

So I'd like to be able to restore GRUB on /dev/sda so that it detects the two Ubuntu kernels, Windows XP, and Windows restore again.

If anyone could suggest a way of going about this, I'd be most appreciative.

Thanks in advance for your help! :)

---

### Post by caljohnsmith on 2008-12-06
If you have your Ubuntu Live CD, how about booting that, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands, reboot, and you should get the Grub menu again if all goes well. Let me know if you run into problems though.

---

### Post by ktzqbp on 2008-12-07
Hi caljohnsmith,

Thanks for your reply, but I'm sorry to say that I had actually figured it out only a little while after posting this thread. I simply did a search on how to reinstall GRUB, and I came across the exact instructions you've offered here. Unfortunately I was in a bit of a rush to go somewhere after I had figured it out, and thus I had no time to post back on my thread notifying everyone of my solution.

I apologise for wasting your time, but thanks for offering it nonetheless.

I've posted a reply to the thread I started at LinuxQuestions regarding my issue on how I solved the entire problem. You can read it [>>here<<](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/l-99-99-...-on-boot-up-have-no-cd-drive-to-fixmbr-688684/?posted=1#post3367003).

---

