---
title: "help troubleshooting graphics inspiron 11z"
date: 2012-02-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pete04 on 2012-02-06
Hi, 

I'm hoping someone might help me put my finger on a small issue with a new Insprion 11z running 11.10, .32 bit

The machine is an i3 u330 model with, according to the system info Intel® Ironlake Mobile x86/MMX/SSE2 graphics.

Everything appeared to work great out of the box, but I've run in to issues that I'm pretty sure are graphics related. I've had a number of freezes during which I can still control the cursor on the screen with the mouse or touch bad but can't select anything. I can't launch the dash with the super key but I can open the shutdown dialog box with a push of the power button, which allows me to cycle through the choices (suspend, restart, etc.). 

Twice the freezes occured when running Chrome.( I switched to Chromium without incident)Two other times, the crashes occurred when I was trying to make adjustments with compiz config manager. I've avoided any wild effects, like desktop cube, etc. I've only adjusted the opacity of the launcher and the pixel size of its icons. When I've tried to enable other graphical tweaks, I've had pretty long hangs -- not freezes, just a solid 5 to 10 seconds of system lock. Today I had two big freezes over the course of a solid 7 to 8 hours of work.

These freezes occured when I was doing a decent amount of multi-tasking, Thunderbird, Come, Shotwell, gNote, Libreoffice all open at the same time. 

I've looked through the forums and haven't found anything that seems to match what I'm experiencing. I'm wondering if maybe the install didn't go quite right (I used a unetbootin USB stick). Perhaps the integrated graphics aren't powerful enough to handle eyecandy. Perhaps I should try working a day under unity 2D.

My issue is more of a mild annoyance and not a deal breaker for me. Just hoping someone has some experience with this machine or maybe the graphics .

---

### Post by pete04 on 2012-02-07
I'm beginning to think there's really nothing wrong with my machine or graphics card but that I'm just seeing bugs present in Unity... I'm going to run Unity 2D for a few days and see if I have the same experience.

---

### Post by mörgæs on 2012-02-07
Better to try something a little further away, like a live boot of L/Xubuntu.

---

### Post by pete04 on 2012-02-07
Thanks. I installed the Xubuntu  desktop with synaptic and everything seems to be working well. I'll give it a thorough testing tomorrow. I'm thinking more and more there are just goofy bugs in Unity, at least on my machine.

BTW, Unity 2D is pretty lousy. ...

---

### Post by pete04 on 2012-02-08
Re installed Ubuntu 11.10 64 bit and am leaving everything alone. Gonna live with stock setup and not tempt fate with Compiz config. So far so good.

Read a bunch and it looks like Intel Ironlake issues with unity are known, but low-priority bugs that I'm gonna hope get ironed out for 12.04.

---

### Post by mörgæs on 2012-02-08
Good. By the way, the best way of marking a thread solved is through 'thread tools'.

---

### Post by pete04 on 2012-02-08
> **mörgæs said:**
> Good. By the way, the best way of marking a thread solved is through 'thread tools'.

Thanks a bunch. Solved how to mark the thread as solved.

---

### Post by mörgæs on 2012-02-09
Then please mark the thread solved again :-)

If you want to give the cube a try later, this might help:
[http://ubuntuforums.org/showthread.php?t=1892851](http://ubuntuforums.org/showthread.php?t=1892851)

---

### Post by davidvandoren on 2012-03-01
Why was this thread marked solved?
After read through the whole thread, I did not see a single line saying that these crashes have disappeared.

I have exactly the same problem on an 
MSI H55M-E33 mother board

I3 CPU

On board graphics **Intel® Ironlake Desktop x86/MMX/SSE2 **

I am trying to fix this for almost a year now and the only halfway stable system runs on an IDE hard drive

I have tried all different versions of Ubuntu and fedora with no success. 
Memory testing 
Changing sata from IDE to AHCI mode 
Switching the sata cables from one port to another.
Changing the Graphic frequencies. etc. 

I am now un Ubuntu 11.10 on my sata drive and hardly manage to type this because firefox keeps crashing. ```
ssertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1662): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1662): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1662): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1662): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1662): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1662): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1662): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1662): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1662): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1662): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1662): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1662): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:1662): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
** (process:1789): DEBUG: desktop-launch-listener.vala:118: ran with uri: file:///home/david/.xsession-errors
** (process:1789): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events

** (process:1789): WARNING **: recent-manager-provider.vala:125: Desktop file for gnome-desktop-item-edit was not found
** (process:1789): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
```

   

My x session log

Anything else I can do?

---

