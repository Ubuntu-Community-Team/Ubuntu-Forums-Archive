---
title: "Openbox won't start"
date: 2008-03-29
forum: Desktop Effects &amp; Customization
---

### Post by Masteroc on 2008-03-29
I used the mini version of the ubuntu install to install a base "cli" system. From there i uncommented the repos that i wanted, did an update/upgrade and then did a "sudo apt-get install openbox openbox-themes" along with some other apps (pypanel, feh, thunar, etc.). But when i type "exec openbox" i get this error:

"Openbox-Message: Failed to open the display from the DISPLAY environment variable."

What does this mean??

Thanks

---

### Post by dbbolton on 2008-03-29
> **Masteroc said:**
> I used the mini version of the ubuntu install to install a base "cli" system. From there i uncommented the repos that i wanted, did an update/upgrade and then did a "sudo apt-get install openbox openbox-themes" along with some other apps (pypanel, feh, thunar, etc.). But when i type "exec openbox" i get this error:

"Openbox-Message: Failed to open the display from the DISPLAY environment variable."

What does this mean??

Thanks
Do you have X up and running?

---

### Post by kerry_s on 2008-03-29
people always forget to install X

[B]sudo apt-get install xorg openbox openbox-themes
startx
[/B]
if you don't install " X " there's no gui to run gui programs.

---

### Post by Ariccanfly on 2008-03-30
I have x installed and XFCE4 works.

but im getting the same error trying to exec openbox-session or fluxbox or matchbox.

boo-urns..

trying to solve presently.

its an olpc btw, and the install is on a usb, and its a mini.iso install...

k peace

---

### Post by Ariccanfly on 2008-03-30
Installed slim a session manager and IT can log into open-box.

it seems that XFCE4 is leaving a residual x with cursor when i log out..
 :(

more research needed

---

### Post by Masteroc on 2008-03-31
I did have x installed. I will reinstall the whole system and try again.

---

