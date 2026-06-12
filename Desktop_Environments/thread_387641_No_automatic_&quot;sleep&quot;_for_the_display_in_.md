---
title: "No automatic &quot;sleep&quot; for the display in X windows"
date: 2007-03-18
forum: Desktop Environments
---

### Post by believekevin on 2007-03-18
Hi everyone, 

I have two dapper installs being used in an art gallery.  I need to stop them from automatically putting the display to "sleep".  

The power management options in the GNOME administration menus do not have an effect.  I suspect that this is because I am using an [auto login hack]("http://doc.gwos.org/index.php/Automatic_Login_No_Authentication") that uses startx rather than gdm.

Can someone point me to the x config file that controls display power management?  

Thanks!

Kevin

---

### Post by dreadlord_chris on 2007-03-18
Why are you using that auto login hack? It's not necessary, both GNOME & KDE have an option to designate a user to automatically log on. You can even set a delay time.

Since mostly, I'm the only one using this box I set it to wait 30 secs then log on to my account & lock the screen. But I do have a roommate who occasionally likes to surf - so she has her own account. This way, my box always comes back to my desktop in case of random reboots - but still allows my roomie to access her account (switch-user)

---

### Post by airtonix on 2007-03-18
Yeah i second that dreadlord_chris.

And once you have set the "Puter" to auto-login in this fashion, you can then stop the thing going to sleep by changing the screensaver and the power options.

but you may already know this.

---

### Post by believekevin on 2007-03-22
Der.  That makes a lot of sense.  However, my curiosity was piqued and I found the solution.

DPMS (Display Power Management System) controls the blanking, sleeping, and shutting off of the  screen.  Randomly sifting through xorg.conf was useless because the DPMS default settings are hardcoded into X!

I found the answer on a [Shallow Sky linux tips page]("http://www.shallowsky.com/linux/x-screen-blanking.html").

First, to check your current settings, use

```
xset -q
``` 

Next, you need to override the defaults in your xorg.conf.  Quoting from the shallow sky page:

> the timeouts can also be specified in the X configuration file: /etc/X11/xorg.conf. In the "Monitor" section, you need a line like:

        Option          "DPMS"

Then, in the "ServerLayout" secdion, include lines like this:

        Option          "BlankTime"     "4"
        Option          "StandbyTime"   "0"
        Option          "SuspendTime"   "0"
        Option          "OffTime"       "5"

Caution: note the numbers are all small. xorg.conf needs times specified in minutes, not seconds as with xset.

If you're seeing a timeout that isn't one of the defaults, but isn't specified in xorg.conf -- as with the two-minute timeout which set me on this quest in the first place -- you may have to hunt around for a place that's calling xset dpms with a different set of timeouts. In my case, it turned out that Ubuntu Breezy sets the dpms timeouts in /etc/acpi/power.sh, which gets called at boot time. So anything you set in xorg.conf may well get overridden.

Hint: when debugging timeouts, try setting them to unusual numbers like 765 or 666 instead of 300 or 600. That makes it easier to be sure whether you're seeing your own numbers or something coming from a system setting somewhere else. 

I simply set these timeouts for greater than 8 hours (the longest shift during which the gallery is open.)

---

