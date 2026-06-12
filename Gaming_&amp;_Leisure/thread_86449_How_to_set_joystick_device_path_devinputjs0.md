---
title: "How to set joystick device path /dev/input/js0"
date: 2005-11-05
forum: Gaming &amp; Leisure
---

### Post by mhancoc7 on 2005-11-05
I have a Logitech Dual Action Gamepad. It is working great with stella, tuxnes, zsnes,  and supertux. I had to set the path to /dev/input/js0 in supertux using a command line argument and in tuxnes using GTuxNES. 

I have installed lxdoom and it works great, but it is looking for the joystick at /dev/js0. How can  I change this or is there a command line argument that will set it at the launch?

Thanks in advance. Jereme

---

### Post by mhancoc7 on 2005-11-08
Ok, I finally tracked down another post that fixed the issue. It creates a link at boot from /dev/js0 to /dev/input/js0.

Here is the post [http://www.ubuntuforums.org/showpost.php?p=174600&postcount=4]("http://www.ubuntuforums.org/showpost.php?p=174600&postcount=4")

After launching lxdoom I have to push a button on the gamepad 4 times and lxdoom starts with joystick support.

I hope this helps someone.

Thanks, Jereme

---

