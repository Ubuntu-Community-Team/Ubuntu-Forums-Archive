---
title: "Input event numbers change after reboot!"
date: 2006-07-25
forum: Desktop Environments
---

### Post by jon_benge on 2006-07-25
Hi

I've noticed that Kubuntu changes the event numbers for my input devices after every reboot. I have a mouse, Keyboard, joypad and Hauppauge remote control. Usually, my Hauppauge remote control is assigned Event3, and Lirc is configured to accept input from Event3. When the event numbers get changed around, my mouse freezes because Lirc is using the wrong device!

Is there anyway I can assign a permanent event number for my input devices?

---

### Post by SeanHodges on 2006-07-29
I'm having the same problem, my remote keeps switching with my mouse. The only thing I can think it might be is my USB mouse is hotplugging at different times to the remote, though I don't know enough about it to be sure thats the problem.

I'll raise the issue with the lirc team. They were very helpful last time.

---

### Post by SeanHodges on 2006-07-29
Well I worked this out... You need to tell udev (the program that generates /dev) to create a symlink for each of your problem devices, so they always have a fixed location. I only needed to do this for one device (my hauppauge remote control) but the same concept should work for other devices too.

First, find out which /dev/input/event the device is on, using evtest (Ctrl-C to stop):

```
sudo evtest /dev/input/event0
sudo evtest /dev/input/event1
sudo evtest /dev/input/event2
sudo evtest /dev/input/event3
```

One of those will respond to pressing the remote control buttons, send this node to udevinfo, using:

```
udevinfo -a -p /sys/class/input/event1
```

You'll get a load of information about the device. This could be the tricky bit, you need to find a piece of information that is unique to the device. the UDEV manual recommends SYSFS{product}, but I didnt get that for my remote so I used SYSFS{modalias} instead, which looks something like:

> SYSFS{modalias}=="pci:v000014F1d00008802sv00000070sd00009002bc04sc80i00"

also, note down the BUS value:

> BUS=="pci"

Now tell UDEV that this device needs a symlink. UDEV creates symlinks for devices matching rules in the file /etc/udev/rules.d/60-symlinks.rules:

```
sudo nano /etc/udev/rules.d/60-symlinks.rules
```

Add the following line anywhere in this file, replacing the bus/modalias values with your own:

```
BUS=="pci", KERNEL="event[0-3]*", SYSFS{modalias}=="pci:v000014F1d00008802sv00000070sd00009002bc04sc80i00", SYMLINK="input/remote"
```

Now all thats left is to tell the device driver to use the symlink instead of the eventX node, for example, my hauppauge remote needed the following change in /etc/lirc/hardware.conf:

```
DEVICE="/dev/input/remote"
```

Heopfully, thats it! Save the file and reboot. The devices should not conflict anymore.

I'll monitor this post in case you have any other problems. I'll also send a bug request to Launchpad when i get chance.

Cheers,

Sean

---

### Post by jon_benge on 2006-07-30
Hey, thanks for this :)

I've been looking for a fix for ages!

I'll try and implement it later on & let you know how I get on.

If I am successful, I'd like to add your information to my [Hauppauge Remote Control in Kubuntu]("http://www.ubuntuforums.org/showthread.php?t=183545") guide, if you don't mind?

---

### Post by SeanHodges on 2006-08-08
Sorry for the late reply,

I have no problem you adding this information to your guide, in fact I think I used some of that guide to get other parts of my remote working, so least I can do!

Cheers,

Sean

---

