---
title: "Laptop screen dims to minimum settings upon boot"
date: 2013-01-17
forum: Desktop Environments
---

### Post by Jim01 on 2013-01-17
Been a very long time since I've played with linux but have decided to get back into it! :popcorn:

Have done my usual research and I'm finding a consistent result for fixing this issue of adding a line to /etc/rc.local

The problem is the folder "rc.local" doesn't exist!

I'm using Lubuntu 12.10

Cheer's guys

James

---

### Post by Toz on 2013-01-17
/etc/rc.local is a file, not a folder. Add the command to the end of the file above the existing "exit 0" command. You will need administrative rights to edit this file, so execute it as (from a terminal window):
```
gksu leafpad /etc/rc.local
```

---

### Post by Jim01 on 2013-01-18
Sorry for the late reply, been pretty busy.

Ok so I've got the file up using the command you gave me, a possibly silly quesiton:  How do I enable that script? or rather what exactly is it I need to change?

---

### Post by cmcanulty on 2013-01-18
install xbacklight, then do command xbacklight when you have first set the screen brightness to what you want. After you see the number xbacklight gives you type command
```
xbacklight set -numberyouwanthere
```
for example my command  is ```
xbacklight -set 80
```
finally in startup applications add xbacklight as name and xbacklight as command. Let me know if it works.

---

### Post by Jim01 on 2013-01-18
Almost there!

Installed xbacklight, and I've used the command you've given me to set it at the prefered brightness, I'm now just a little stuck as to adding it to the startup applications, I've done some googleing but I can't really find anything that helps me much.

Cheer's dude :guitar:

---

### Post by cmcanulty on 2013-01-18
just go to Startup applications and type what I show in the screenshot except note the screenshot leaves off the last letter in the command should end in backlight

---

### Post by Jim01 on 2013-01-21
Hey guys, sorry for yet another late reply :(

The following is a screenshot of what I get in Lubuntu when I try to edit my startup applications, I can't find the same sort of edible "startup" section like you have used, I'm assuming that screenshot was taken in ubuntu rather than lubuntu?

---

### Post by cmcanulty on 2013-01-22
did you look under the advanced tab?

---

### Post by Jim01 on 2013-01-22
I sure did:

---

### Post by cmcanulty on 2013-01-24
I have to get to work but research adding ubuntu system settings to your system it has the other options

---

### Post by Jim01 on 2013-01-24
Found this:

[http://forum.lxde.org/viewtopic.php?t=111&f=8]("http://forum.lxde.org/viewtopic.php?t=111&f=8")

Where can I find xbacklight so I can shove it in the autostart directory as descibed in that link?

---

### Post by cmcanulty on 2013-01-25
type xbacklight in synaptic and install it

---

### Post by TheBigH on 2013-02-03
Hello everyone. Sorry for hijacking this thread, but I had and solved a very similar problem, and I thought it might help someone in the future to know what I did.

I couldn't get xbacklight to work because it looks for the screen brightness information in the directory /sys/class/backlight/acpi_video0/ and I do not have that directory; mine was /sys/class/backlight/asus_laptop, so I kept getting the  error message "No outputs have backlight property".

The fix was very simple. The directory has a handful of files in it with names like actual_brightness, brightness and max_brightness, and these contain a single number. I found that brightness was 3 out of a max_brightness of 15, which explains why my screen was so dark. So all I did was 
```

sudo echo "12" > brightness

```
entered my password, and the screen brightened *instantly*. After a reboot my change has persisted. Nice.

---

