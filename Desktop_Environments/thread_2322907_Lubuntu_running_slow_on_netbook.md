---
title: "Lubuntu running slow on netbook"
date: 2016-05-01
forum: Desktop Environments
---

### Post by olie2 on 2016-05-01
Hey all.  I've been using Lubuntu on my home computer and netbook for quite some time now, but over the last few weeks there has been a significant decrease in performance on the netbook.  I'm going to upgrade to 16.04 and see if there's a change, but maybe its just that Firefox is too bloated now.  I was just wondering, is there a way to install a pre-configured ubuntu distro but with a fluxbox or lighter weight window manager?  I was thinking of trying Debian with a light window manager, but I think configuring the whole system securely is a little beyond me, hence why I'd like to stay in the Ubuntu family for now.  Thanks in advance.

---

### Post by ajgreeny on 2016-05-01
Take warning with the netbook, if it's getting a bit old in particular.

I have a re-badged MSI 100U (I think) with an Atom 270N cpu, integrated Intel graphics, 1GB ram and 160GB HDD, which refuses to show any sort of desktop with 16.04; I can not even get it to a tty using Ctrl+Alt+F1, as that appears momentarily, and then goes back to a black screen with a blinking cursor in the top left corner.

I have tried both Lubuntu and Xubuntu but neither of them manage to get to a desktop.  So far I have not had time to investigate further or try using nomodeset or other boot-option from the grub menu (or is it syslinux in a live USB system?).

14.04 of both Lubuntu and Xubuntu works brilliantly, if a bit slow opening things like firefox, so I tend to use midori or qupzilla, but otherwise they are both good OSs for that netbook.

---

### Post by him610 on 2016-05-01
FWIW: 
I too have a netbook. Mine is an Acer AOA 110L with the 8GB SSD, originally came with Linpus Linux. I have successfully installed Crunchbang (no longer available), Knoppix, Chromixium (no longer available), and most recently Xubuntu 16.04. I upgraded the RAM from 512MB to 1.5GB.  I thought it ran great on those operating systems. Maybe some folks would think it ran slow, but what does one expect from an Atom N270. It will run slower! These machines are going on, what, eight years now. 

That was my travel machine.  I truly liked that little machine. The 8GB SSD I mentioned earlier, it died two days after I installed Xubuntu 16.04. I am going to replace the SSD and will probably reinstall Knoppix 7.6 on it.

---

### Post by olie2 on 2016-05-04
> **ajgreeny said:**
> Take warning with the netbook, if it's getting a bit old in particular.

I have a re-badged MSI 100U (I think) with an Atom 270N cpu, integrated Intel graphics, 1GB ram and 160GB HDD, which refuses to show any sort of desktop with 16.04; I can not even get it to a tty using Ctrl+Alt+F1, as that appears momentarily, and then goes back to a black screen with a blinking cursor in the top left corner.

I have tried both Lubuntu and Xubuntu but neither of them manage to get to a desktop.  So far I have not had time to investigate further or try using nomodeset or other boot-option from the grub menu (or is it syslinux in a live USB system?).

14.04 of both Lubuntu and Xubuntu works brilliantly, if a bit slow opening things like firefox, so I tend to use midori or qupzilla, but otherwise they are both good OSs for that netbook.

Yeah, I might have to go back to 14.04.  I managed to install Xubuntu 16.04 ( would have done Lubuntu, but I couldn't get into the live session to set up encryption on the netbook), but it seems to just chug along.  Not like I'm doing a lot of things either, but just typing resumes and web surfing at the same time seem to slow everything down.

---

### Post by olie2 on 2016-05-04
> **him610 said:**
> FWIW: 
I too have a netbook. Mine is an Acer AOA 110L with the 8GB SSD, originally came with Linpus Linux. I have successfully installed Crunchbang (no longer available), Knoppix, Chromixium (no longer available), and most recently Xubuntu 16.04. I upgraded the RAM from 512MB to 1.5GB.  I thought it ran great on those operating systems. Maybe some folks would think it ran slow, but what does one expect from an Atom N270. It will run slower! These machines are going on, what, eight years now. 

That was my travel machine.  I truly liked that little machine. The 8GB SSD I mentioned earlier, it died two days after I installed Xubuntu 16.04. I am going to replace the SSD and will probably reinstall Knoppix 7.6 on it.

I tried playing around with Debian Jessie with LXDE on it, but the setup was becoming a pain with non-free software/drivers, repositories, installing / setting up ufw, etc, and I don't think I know enough to securely set up a desktop with Debian. Pretty sure I found the Freebsd desktop setup easier than the Debian one.  I used to use Crunchbang as well, which is why I tried Debian, and I was going to switch back to it, but like you said, it's no longer available.  

Is there a way to streamline Lubuntu?  Like install it, then uninstall the Lubuntu-desktop (sudo apt-get autoremove --purge lubuntu-desktop), install Lubuntu-core, then just install then pick and choose what I need?  I guess I could always do the minimal install too...

---

### Post by mörgæs on 2016-05-05
> **olie2 said:**
>  I guess I could always do the minimal install too.

Yes, begin from a small system and add stuff as you need it. Better than doing a big install and remove unneeded stuff.

---

