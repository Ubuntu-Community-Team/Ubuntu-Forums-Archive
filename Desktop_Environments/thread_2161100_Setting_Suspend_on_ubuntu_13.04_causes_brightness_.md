---
title: "Setting Suspend on ubuntu 13.04 causes brightness to change when waking up"
date: 2013-07-09
forum: Desktop Environments
---

### Post by bjackfly on 2013-07-09
Hi, I am running Ubuntu 13.04 and I usually don't shutdown my system I just put it in suspend. I am running 1 external monitor and the laptop monitor but most times when unsuspending the brightness will be turned all the way down even though I don't have the "dim screen to save power" option checked on the brightness screen. Prior to suspending the brightness is turned up and the dim screen to save power is unchecked.  Afterwards everything is the same but the brightness is turned all the way down. It seems like a bug.  The first thing I usually have to do is just change it back but was wondering if there was a work around for this.


BTW: How do you post a graphic in here? I wanted to put a before and after screen shot of the brightness setting screen to help show what I am talking about, basically the only thing that is changed is the slider from full to all the way down.

---

### Post by Toz on 2013-07-09
> **bjackfly said:**
> Hi, I am running Ubuntu 13.04 and I usually don't shutdown my system I just put it in suspend. I am running 1 external monitor and the laptop monitor but most times when unsuspending the brightness will be turned all the way down even though I don't have the "dim screen to save power" option checked on the brightness screen. Prior to suspending the brightness is turned up and the dim screen to save power is unchecked.  Afterwards everything is the same but the brightness is turned all the way down. It seems like a bug.  The first thing I usually have to do is just change it back but was wondering if there was a work around for this.
We can reset the brightness via a suspend/resume script in /etc/pm/sleep.d. But first, can you run the following script in a terminal window and post back the results so that we can see what backlight interfaces you have?
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```


> BTW: How do you post a graphic in here? I wanted to put a before and after screen shot of the brightness setting screen to help show what I am talking about, basically the only thing that is changed is the slider from full to all the way down.
You can either insert an image from a url (click on the picture icon) or upload an image from your computer (click on the paper clip icon). If you don't see those icons, you need to click on "Preview Post" or "Go Advanced" depending on where you are.

---

### Post by bjackfly on 2013-07-13
*for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
0
10
/sys/class/backlight/acpi_video1
10
10
/sys/class/backlight/radeon_bl0
255
255

---

### Post by Toz on 2013-07-13
You have 3 backlight interfaces. You need to find out which one is the active one. Run the following commands and identify which set changes the brightness:

_Set 1:_
```
echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 10 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

_Set 2:_
```
echo 5 | sudo tee /sys/class/backlight/acpi_video1/brightness
echo 10 | sudo tee /sys/class/backlight/acpi_video1/brightness
```

_Set 3:_
```
echo 128 | sudo tee /sys/class/backlight/radeon_bl0/brightness
echo 255 | sudo tee /sys/class/backlight/radeon_bl0/brightness
```

Enter your password when prompted.

What is the make and model of your laptop?

---

### Post by jback2 on 2014-06-21
This seems to be the right approach. The following works for me:

```
echo 15 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

What can I do now to execute this automatically after wakeup?

---

### Post by Toz on 2014-06-21
With root privileges, create the file **/etc/pm/sleep.d/000brightness_fix** with the following content:
```

#!/bin/bash
case $1 in
    hibernate|suspend)
        # do nothing
    ;;
    thaw|resume)
        echo 15 > /sys/class/backlight/acpi_video0/brightness
    ;;
    *) 
    ;;
esac

```
...and make sure the file is set executable.

---

### Post by jback2 on 2014-06-21
Thank you so much!

---

