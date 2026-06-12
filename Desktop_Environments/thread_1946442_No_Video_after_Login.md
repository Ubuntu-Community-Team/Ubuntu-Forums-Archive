---
title: "No Video after Login"
date: 2012-03-24
forum: Desktop Environments
---

### Post by Roach360 on 2012-03-24
After I select "Gnome Classic" for my session and login to ubuntu, my monitors shutoff since there's no video signal.

Though if I select the K environment, I boot just fine.

Suggestions?

---

### Post by Moozillaaa on 2012-03-24
Can you reboot into the recovery kernel, to get X-server in default mode?

---

### Post by Roach360 on 2012-03-25
There is no option to boot into the recovery kernel; all i see is bios, then kbuntu loading, then ubuntu login.

I just tried logging into a guest session of ubuntu, and that works fine...

---

### Post by drakemata on 2012-03-25
> **Roach360 said:**
> There is no option to boot into the recovery kernel; all i see is bios, then kbuntu loading, then ubuntu login.
 
Hold the SHIFT key after POST and you should see the grub menu so that you can choose the recovery kernel.

---

### Post by Roach360 on 2012-03-25
I got into the recovery kernel and ran disk check and repair, i figured it wouldn't hurt.

Then I ran this line in root prompt:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This doesn't seem to have done anything.

---

### Post by Moozillaaa on 2012-03-25
Instead of running that command, let's try to update here; get yourself a command prompt, by doing again as drakemata said - only this time, select 'Press 'c' for a command prompt.

It will then prompt YOU to log in by your username - like roach360@desktop, or something like that. Enter your username, 'Enter', then you'll be asked for your password. Enter it, and then do an update:
sudo apt-get install update (or updates)

---

### Post by Roach360 on 2012-03-25
When I hold "C" I get a command prompt that is "grub>"

I does not request login, or let me use the update command.

---

### Post by Roach360 on 2012-03-27
Suggestions on how I can get this working?

---

