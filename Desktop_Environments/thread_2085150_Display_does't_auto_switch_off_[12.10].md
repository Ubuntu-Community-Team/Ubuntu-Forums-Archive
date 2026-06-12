---
title: "Display does't auto switch off [12.10]"
date: 2012-11-17
forum: Desktop Environments
---

### Post by p1r0 on 2012-11-17
I am running Lubuntu on 12.10 and I've set the display to switch off after 10 minutes. 
After inactivity the display goes blank but never switches off.
I've tried running:

```
xset dpms force off
```

from the terminal and it works just fine.

Any ideas what might be the problem with lubuntu?

Thanks!

---

### Post by kalehrl on 2012-11-17
Do you have [acpi-support]("http://packages.ubuntu.com/precise/acpi-support") package installed?
I had to install it to get the monitor to shut down after lid is closed.
I didn't have to configure anything - it worked right after installation.

---

### Post by p1r0 on 2012-11-17
I am no sure that I have that. But I have disabled the screensaver now and it seems to be working.

Will update this post after confirmation.

---

### Post by p1r0 on 2012-11-17
I confirm that I have acpi-support installed, but no, this still doesn't work

---

### Post by kalehrl on 2012-11-17
Disable all xscreensaver and other actions affecting lid closing.
Reboot and try again.

---

### Post by p1r0 on 2012-11-17
This seems to have fixed  it [http://ubuntuforums.org/showpost.php?p=12247108&postcount=8](http://ubuntuforums.org/showpost.php?p=12247108&postcount=8)

Thanks!

---

### Post by kalehrl on 2012-11-18
Yes, but you have to type the command manually for something which should be done automatically. Glad you are happy with the solution.

---

### Post by p1r0 on 2012-11-18
Not really, weird thing, after playing around with those commands, now it automatically turns the display off :)

---

### Post by kalehrl on 2012-11-18
Yes, sometimes weird things happen.
When I first installed Lubuntu a couple of years ago, I remember not being able to switch off the laptop backlight on closing. It turned out it was xscreensaver messing with the acpi functions. When I disabled it, it monitor turning off started to work.
A couple of day ago I installed Lubuntu minimal without xscreensaver and I thought monitor shutting off will work right. I was wrong. It turned out acpi-support wasn't installed and after installation, it started to work as before.

---

### Post by p1r0 on 2012-11-18
Yup, in my case was definitely a combo of all the above, hehe.
First thing was to disable xscreensaver, that thing was messing with my attempts to switch of the display.

---

### Post by p1r0 on 2012-11-24
As I could check because this happened again, the solution was:

First ***to disable the screen saver as it was messing with the display***

And second run:

```
xset +dpms
```

as root.

---

