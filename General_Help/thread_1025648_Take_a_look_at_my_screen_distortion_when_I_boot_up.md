---
title: "Take a look at my screen distortion when I boot up..."
date: 2008-12-30
forum: General Help
---

### Post by PsychedelicWonders on 2008-12-30
Here are a few various screen shots of my computer when I boot up.

It doesnt do this often, but does from time to time.

What is it?

Why does it do this?

And how do I fix it?

[IMG]http://i208.photobucket.com/albums/bb38/PsychedelicWonders/ubuntu.jpg[/IMG]

Notice the snow...

[IMG]http://i208.photobucket.com/albums/bb38/PsychedelicWonders/Ubuntu2.jpg[/IMG]

[IMG]http://i208.photobucket.com/albums/bb38/PsychedelicWonders/Ubuntu3.jpg[/IMG]

---

### Post by eBoxNet on 2008-12-30
it looks like the vga for some reason can't get good color depths (like it works on 256colors or something)

does it make that on first boot or only after hours of working and rebooting?

---

### Post by PsychedelicWonders on 2009-01-20
Hey this only seems to happen on first boot.

And now as of lately, I cant even get the Ubuntu login screen.

It doesnt go past a snowy Nvidia screen?

Windows seems to work fine.

What can i do to force the computer to log into Ubuntu and fix this overall issue?

I've rebooted a dozen times, let the computer sit off for a few days at a time and still no login screen?

---

### Post by icanfly0307 on 2009-01-20
Hmmm. Seems to be an Nvidia issue. Are you using the drivers from the Resticted Hardware Section or the general drivers provided by Ubuntu?

---

### Post by cariboo on 2009-01-20
To get back to a default desktop, restart in recovery mode and select xfix from the menu. Once it is finished choose resume to continue on to the desktop. It looks like you monitor is not being detected properly,

Jim

---

### Post by PsychedelicWonders on 2009-01-22
I dont know which kernal I used, but I eventually tried one of the 3's recovery mode.

i dont know if I went to xfix... 

but everything is working now?

Is there any way for me to double check what the problem was to make sure it is fixed?

Icanfly:

> Are you using the drivers from the Resticted Hardware Section or the general drivers provided by Ubuntu?

I'm not sure... how do I find out?

Is one way better than the other?

---

### Post by jimv on 2009-01-22
Here's some codez for u 2 run (this will make sure you have right Nvidia driver):

Press control+alt+F1 to get to a terminal

Type:

sudo apt-get install envyng-gtk
envyng -t
1
1
y

This should install the new driver, then all you need to do is reboot.

---

### Post by PsychedelicWonders on 2009-01-23
My internet is down for probably another week... so once it is, I will run this code and get back to you... thanks for the help and hoepfully you see this post again with my results in about a week.

---

### Post by PsychedelicWonders on 2009-01-26
I have 3 kernals with recoverys

Now it seems its the latest kernal that always gives me a problem...

i load the recovery mode of the oldest kernal I have and it runs its check and then asks me

Boot in normal mode
Fix problems (not sure if there were any)
and then there is a 3rd thing...

I just end up going with "boot in normal mode"

should I be doing somethign different to fix this?

What code can I run to see what the real issue is?

thanks.

---

