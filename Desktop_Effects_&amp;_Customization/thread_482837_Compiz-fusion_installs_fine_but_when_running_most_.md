---
title: "Compiz-fusion installs fine but when running most commands don't work"
date: 2007-06-24
forum: Desktop Effects &amp; Customization
---

### Post by Yes_It's_Me on 2007-06-24
Hi guys, i installed compiz-fusion from the above stickied thread and it seemed to install fine (i was running beryl perfectly beforehand and am while i attempt to fix this). When i start it up the pretty fade effects and transparencies and wobbly windows and all that works but i am unable to rotate the cube by pressing ctrl+alt+left click like i was in beryl, i can only switch workspaces by clicking on the icon in the taskbar. Something that may or may not have something to do with it is that when i first installed it, there was only one workspace in the task bar instead of 4 under beryl, i changed that manually via gconf-editor but the cube still doesn't work :(.

Also, when i zoom in by pressing super+scroll, i am not able to move the zoomed part of the screen like in beryl, like if i wanted to view a different part of the screen i have to zoom out then zoom in again.

Is there any way to fix this? Thanks in advance.

---

### Post by rax_m on 2007-06-24
For the first issue, do you have to possibly enable the "rotate cube" plugin from the Compiz Configurator? System->Preferences->CompizConfig Settings Manager

As for the second issue I  see what you mean.. haven't been able to figure out how to make it work like Beryl yet.. sorry.

---

### Post by llamakc on 2007-06-24
I too had issues with the cube not working. Instead, it would just slide left and right, but not spin. I went into ccsm and made sure that the cube and cube rotate plugins were enabled, and also viewport mouse switch. I t still would not work. 

Logging out and back in did the trick for me.

---

### Post by ivesjd on 2007-06-24
You need to adjust the horizontal size, not the number of desktops.

---

### Post by cjsimmons on 2007-06-24
> **ivesjd said:**
> You need to adjust the horizontal size, not the number of desktops.

Thanks for this, I've been trying to work this out for just over a day now. Very new to Ubuntu and Compiz.:D

---

### Post by Yes_It's_Me on 2007-06-25
Thanks for the replies guys!

what should i change the horizontal to? should i change it to 4 and put the number of desktops back to one?

and yeah, when i go into the settings for fusion the cube is said to be running and all that, i am in gutsy at the moment attempting to install it so i will reboot into feisty in a minute and have a look.

---

### Post by Yes_It's_Me on 2007-06-25
> **Yes_It's_Me said:**
> Thanks for the replies guys!

what should i change the horizontal to? should i change it to 4 and put the number of desktops back to one?

and yeah, when i go into the settings for fusion the cube is said to be running and all that, i am in gutsy at the moment attempting to install it so i will reboot into feisty in a minute and have a look.

EDIT: ok, i'm in feisty now after successfully getting it to work in gutsy (except the title bars), my hsize in gconf already says 4, as well as my number of desktops, all the right plugins are enabled in CCSM and all that. Yet it still doesn't work, also, when using the expo plugin it only zooms out a little bit to show my one desktop instead of 4.

OK! guys! I got it working, thanks for the help! I did some fiddling and found out i had to type compiz --replace instead of using the beryl-manager app to launch it, i then had to use the flat-file config backend. Now it's running flawlessly from a system point of view and quite stable :)

---

### Post by Franz1234 on 2007-06-25
Hey!

There is a update available. I installed this trough the update manager and now everything is running perfect!!

Good luck!

---

### Post by jeff419 on 2007-07-03
> **cjsimmons said:**
> Thanks for this, I've been trying to work this out for just over a day now. Very new to Ubuntu and Compiz.:D

Why would you set the default setting for a cube this way?  Shouldn't the default for the cube BE A CUBE?

Anyways, I'm glad I found this  :D

---

