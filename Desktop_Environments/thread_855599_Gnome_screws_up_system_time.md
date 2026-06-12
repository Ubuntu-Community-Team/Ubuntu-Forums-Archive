---
title: "Gnome screws up system time"
date: 2008-07-10
forum: Desktop Environments
---

### Post by slythfox on 2008-07-10
I dual-boot between Ubuntu and Windows. Every time I boot into Ubuntu, it changes bios's time, so that when I boot into windows, my time is screwy... It's a viscous circle that I want to fix. Is there a Gnome setting so that it won't change my bios's time?!

---

### Post by sayakb on 2008-07-10
Did you try setting the correct time with Ubuntu? Anyway, right click on the digital clock on the panel and select **Adjust Date and Time** and press **Unlock** button to enter your password. Make sure you have the correct time zone selected there. Also at the **Configuration** drop-menu, select **Manual** and press Close.

---

### Post by slythfox on 2008-07-10
Yes. It's always been like that. It has never been automatic.

---

### Post by mcduck on 2008-07-11
There's also option to select if your system clock is using UMT or not..

The default behaviour for Linux/Unix systems is to keep system clock in UMT and then on the desktop calculate the correct local time based on your time zone information. Windows, however assumes that the system clock uses local time.

Just change the setting in Ubuntu's time configuration and the problem should be gone.

---

### Post by ATSC on 2008-07-12
Hi, I have a similar issue.

I've tried unsuccessfully to change my clocks time, which is two hours ahead (some time ago just one hour). The config-panel however shows the time correctly (see below). Neither manual changes nor the konfiguration via internet-synchronization helps (I've selected four time-servers).
I have the 64bit hardy-version.

Any help would be much appreciated. Sorry in advance, if this has been posted elsewhere, I've had a look and couldn't find anything suitable (unless I've missed something).

---

### Post by Mister.Vash on 2008-07-13
slythfox, did you follow mcduck's suggestion about changing the time?
I believe that this is the bit that you want to change.

 [https://help.ubuntu.com/community/UbuntuTime#Make%20Linux%20use%20%27Local%27%20time](https://help.ubuntu.com/community/UbuntuTime#Make%20Linux%20use%20%27Local%27%20time)

Try that out and it should take care of the issue


ATSC, can you right click on your clock, choose Preferences, then check that the Location matches your timezone.  From your screenshot it looks like you should Europe/Amsterdam - if you have additional entries listed, it could just be showing the time for that Location

---

### Post by ATSC on 2008-07-13
> **Mister.Vash said:**
> 
ATSC, can you right click on your clock, choose Preferences, then check that the Location matches your timezone.

Been there, done that. No changes.

---

### Post by ATSC on 2008-07-25
any further thoughts?

---

### Post by ATSC on 2008-07-29
[IMG]http://img373.imageshack.us/img373/2152/tumbleweeds01fq4.jpg[/IMG]

---

