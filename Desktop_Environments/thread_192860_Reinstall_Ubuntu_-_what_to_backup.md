---
title: "Reinstall Ubuntu - what to backup?"
date: 2006-06-09
forum: Desktop Environments
---

### Post by Lunar_Lamp on 2006-06-09
I stupidly installed dapper without a separate /home partition, and now after playing around with it I have a wide range of junk sitting on the partition.  I want to wipe it and just reinstall the programs/drivers that I want and need.  

Besides copying my /home directory to a usb drive, and then copying it back again, what other files should I be looking to backup?

 - Evolution tasks/calendar - where and how?
 - Thunderbird settings/mail accounts/downloaded mails - where and how?
 - xorg.conf (just for reference)
 - sources.list (just so I can copy and paste it back in without thinking)

Pointers would be appreciated.  Also, I have about 30gigs to play about with in Ubuntu - what partition sizes would you recommend - ie is a 25gb /home excessive?

---

### Post by taurus on 2006-06-09
Your home partition is good.  If X is working the first time, it will work again so no need to back up /etc/X11/xorg.conf unless you have to configure it for some extras.  Again, all your personal settings, mails, downloads, etc., should be in your /home directory...

Depending on what you plan to download to your /home, 25GB should be more than enough...

---

### Post by jazzgossen on 2006-06-09
I would backup /etc and /usr/local as well, just in case.

---

### Post by Zed on 2006-06-09
I always back up /etc (for reference) too. And do /opt if you have anything there. And save a text file of the output of apt-cache pkgnames so you can see what you had installed.

---

### Post by FredB on 2006-06-09
Home directory and your xorg.conf file if you modified it. I've done this every time I changed my distro. And no problem so far ;)

---

