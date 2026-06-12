---
title: "Computer running very slow, trouble with partition size"
date: 2009-07-29
forum: Desktop Environments
---

### Post by brandon2010 on 2009-07-29
I just switched over from Gentoo because it started resembling my Windows partition; in other words, I had to wait a few minutes after booting to run anything, and simple things like minimizing a window would make the computer lock for a few seconds (it was great for a long time, though). Anyway, I downloaded the latest Kubuntu last night since I like KDE better than Gnome. Even Konsole takes 10 sec to open! Keep in mind I only have ~250 MB RAM, so would I be better off with Gnome?

Last, my Linux partition (ext3) was only 9 GB so I tried making it larger this time around. Well I shaved 3 GB off the Windows (ntfs) partition and it goes into the 13 GB unusable partition. I tried making the ext3 larger, but no dice. I can enlarge the ntfs one, though. How can I go about fixing this?

---

### Post by krazyd on 2009-07-29
switching to gnome is not likely to make much difference.

have you considered a simple window manager such as blackbox, fluxbox or enlightenment?

---

### Post by brandon2010 on 2009-07-29
Yeah, but I had an older version of Ubuntu before Gentoo with Gnome, and it worked fine. And I ran both Gnome and KDE on Gentoo for a long time and it was fine. It all of a sudden just slowed down so I thought formatting the partition would help, and I didn't want to go through compiling Gentoo again so I went with Kubuntu.

---

### Post by NathanLT on 2009-08-18
K/Ubuntu as a distribution is well known for being resource-intensive due to the large number of background services it runs by default. If you open up System Monitor you can see how much RAM you're using, and what programs are using it. For example, at the moment I'm using approx. 680Mb RAM. I have only opened four programs - Firefox, KMail, vim and System Monitor - but also listed in the Process Table in System Monitor are a whole host of other programs that the system is running automatically, such as krunner, kwalletmanager, networkmanager, and a pile of others whose function I couldn't guess. All of this eats up my RAM.

Try going through the Process Table and removing programs you know you don't use or need. krazyd's suggestion of trying a lighter window manager is a good one, but looking at System Monitor I can see that kwin (KDE's window manager) is currently only using 6Mb of RAM, whereas update-notifier-kde (that little icon that sits in my system tray telling me when I have updates available) is using 48Mb! I also have kblueplugd (bluetooth daemon) using 9Mb of RAM, even though I don't own any bluetooth devices. Etc, etc. Kubuntu installs and runs all of these programs by default so that everything will 'just work', but they all eat up your RAM, so if you know you're not going to use them, you can kill them in System Monitor and then uninstall them using Synaptic, KPackage, or apt-get.

However, you might remove everything you don't need and still be short of RAM! In this case you may need to try another Desktop Environment or even another distribution. I previously used the XFCE desktop environment on Debian Lenny and was using around 180Mb RAM, but there are distributions out there that are even more frugal.

Regarding your second question, at the partition stage of the install process there is an option for manually configuring your partition table, which will allow you to reallocate the 3Gb to your new Linux partition. I'm not sure, but as far as I'm aware ext3 partitions need to be reformatted before they can be resized (unlike NTFS, which can be resized without having to wipe the data first).

Good luck!

Nathan

---

