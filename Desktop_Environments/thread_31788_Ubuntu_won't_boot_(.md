---
title: "Ubuntu won't boot :("
date: 2005-05-04
forum: Desktop Environments
---

### Post by Manc on 2005-05-04
Having used the Os for a few weeks I was asked to update certain components of via the update manager. I downloaded all  the available updates. At this point and I don't know why but also  decided to download the Nvidia drivers  as well!

Anyways As per normal the PC goes through the boot sequence with everything saying ok, however just as the login screen is supposed to appear the screen now goes black and the monitor powers off!

Is there anything I can do to return my system to its pre-update state or is just a case of reinstalling the OS  :-? 

Need a little bit of help - thx in advance  ;-)

---

### Post by panzer77 on 2005-05-04
Mans  I'm not the expert, but if you have an extra monitor, switch the monitor and reboot.  I think its just the refresh rates, so it may get you back in so you can reset or uninstall.  Had the same problem and suspected this might be the issue.

---

### Post by alastair on 2005-05-04
I assume you were using the open-source "nv" driver, rather than "nvidia" before?

You could try booting to "recovery mode" (which is technically "single-user" mode) - you can choose "recovery mode" at the GRUB menu.

No X/GDM should start.

Then, login as normal and :

cd /etc/X11
cp -p xorg.conf xorg.conf.broken

Edit xorg.conf (using "vi", "pico" or "nano" or something) and replace the "Driver nvidia" with "Driver nv". Save/quit the editor.

You should then be able to switch to the default "run level" (rather than "single" user - run level 1) e.g.

init 2

Hopefully this gets X back for you.

---

### Post by professor_chaos on 2005-05-04
Im sorta a newbee, but as this problem is affecting me I had something to offer as a workaround but probably doesnt solve the problem completely.

When booting and X server starts, my monitor immeditly goes into power save. I press press ctrl+alt+F1 and see the end of the output from boot and see a powersave warning regarding AMD processors. So, I disable all powersave features and still this seems to plague my system (AMD 3200 hp). 

Anyway, I simply reboot the X server when this happens by pressing ctrl+alt+backspace and magically I'm rockin and rollin. Hope this helps. Maybe some guru here can offer up more of a solution.

---

### Post by dolson on 2005-05-05
[QUOTE=Manc]Having used the Os for a few weeks I was asked to update certain components of via the update manager. I downloaded all  the available updates. At this point and I don't know why but also  decided to download the Nvidia drivers  as well!

Anyways As per normal the PC goes through the boot sequence with everything saying ok, however just as the login screen is supposed to appear the screen now goes black and the monitor powers off!

Is there anything I can do to return my system to its pre-update state or is just a case of reinstalling the OS  :-? 

Need a little bit of help - thx in advance  ;-)[/QUOTE]


Wow man, that sounds exactly like what happened to me today, although for me, changing the video card seemed to solve it... Check my other post for details about what all I did (it doesn't appear to be an Ubuntu or driver issue, in my case).

---

### Post by Manc on 2005-05-05
I was thinking refresh rates myself!

Anyway I posted on the forum via Windows and rebooted, for some strange Ubuntu worked with no tinkering! - I thanked my lucky stars and went to bed :)

However I don't think this is the end of the problem - but atleast I've got a few ideas to try if it happens again

Thanks for the help :wink:

---

