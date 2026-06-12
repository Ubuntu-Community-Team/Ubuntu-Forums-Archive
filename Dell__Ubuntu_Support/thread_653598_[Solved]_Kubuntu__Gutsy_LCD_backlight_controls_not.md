---
title: "[Solved] Kubuntu / Gutsy LCD backlight controls not functioning on Vostro 1400"
date: 2007-12-30
forum: Dell  Ubuntu Support
---

### Post by neptho on 2007-12-30
Preface: This hack may not work for you.  It worked for me with my Vostro 1400 with the built-in Intel video option.

This was annoying me.  The KPowersave module could control my LCD's backlight, but the ACPI scripts would not.  Obviously, there is full hardware support, but the ACPI system isn't quite up to the task.

The ACPI scripts merely fake the keys when called, with a hard coded value. This, obviously, was not working.

So, I decided on a rather convoluted method.  First, I ended up finding my actual brightness control device (there are several listed on my machine), by running the following as root (it will NOT work via sudo):

```
for n in /proc/acpi/video/**/LCD/brightness; do echo "Trying $n..."; for fade in `seq 1 100`; do sleep 0.01s; echo -n "$fade" > $n; done; done
```

This will print the devices it finds, and attempt to set the LCD levels from 1 (nearly off) to 100 (full brightness).  As different LCDs have different specifications, you can't just randomly assume a single number will work.  I was being lazy, and although it didn't accept them all, it was still a neat effect.

I found that my LCD device was actually: **/proc/acpi/video/VID1/LCD/brightness**

Then, I made the world's ugliest parser to see what the available levels were, and to shift up, or down, according to the script.  Since there are separate 'up' and 'down' scripts, I decided to be lazy.  Have I mentioned yet how incredibly ugly this whole thing is?  I wish there was a more bourne-ish *portable* way to deal with quasi-arrays.

Here's my new **/etc/acpi/video_brightnessdown.sh**:

```
#!/bin/sh
#Yeah, I got kind of lazy.  Arrays in Bourne SUCK.
DEVICE=/proc/acpi/video/VID1/LCD/brightness
#. /usr/share/acpi-support/key-constants
#acpi_fakekey $KEY_BRIGHTNESSDOWN
CURRENTLEVEL=`grep 'current:' $DEVICE | awk '{ print $2}'`
SORTEDLEVELS=`grep 'levels:' $DEVICE | sed -e s,levels:,,g -e 's,\s,\n,g' | sort
 -n | uniq | grep -v '^$' | sed s,\n,\ ,g | xargs echo`
for levels in `echo $SORTEDLEVELS | sed 's,\n,\ ,g'`
do
    if [ $CURRENTLEVEL = $levels ]; then
      echo -n $LASTLEVEL > $DEVICE
      break;
    fi
    LASTLEVEL=$levels
done
```

... and **/etc/acpi/video_brightnessup.sh**:

```
#!/bin/sh
#Yeah, I got kind of lazy.  Arrays in Bourne SUCK.
#. /usr/share/acpi-support/key-constants
#acpi_fakekey $KEY_BRIGHTNESSUP
DEVICE=/proc/acpi/video/VID1/LCD/brightness
CURRENTLEVEL=`grep 'current:' $DEVICE | awk '{ print $2}'`
SORTEDLEVELS=`grep 'levels:' $DEVICE | sed -e s,levels:,,g -e 's,\s,\n,g' | sort -n -r | uniq | grep -v '^$' | sed s,\n,\ ,g | xargs echo`
for levels in `echo $SORTEDLEVELS | sed 's,\n,\ ,g'`
do
    if [ $CURRENTLEVEL = $levels ]; then
      echo -n $LASTLEVEL > $DEVICE
      break;
    fi
    LASTLEVEL=$levels
done
```

Remember to chmod your files, and chown them!
```
chmod 755 /etc/acpi/video_brightnessup.sh
chmod 755 /etc/acpi/video_brightnessdown.sh
chown root.root /etc/acpi/video_brightnessup.sh
chown root.root /etc/acpi/video_brightnessdown.sh
```

I hope these scripts work for you!

---

