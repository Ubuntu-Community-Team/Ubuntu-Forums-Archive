---
title: "Unable to login with my original account"
date: 2017-03-25
forum: Desktop Environments
---

### Post by rrdnt on 2017-03-25
I use ubuntu 16.04. I accidentally added line ibus-daemon -drx to my .profile. Now I can't login with my account (ubuntu will repeatedly return back to login ui even my password is correct). Now I am using guess session which doesn't allow perform, etc. so I can't switch to my original account to remove that. How can I fix this problem so I can login with my original account again?

---

### Post by ajgreeny on 2017-03-25
Use either a live session from a USB, mount your installed disk/partition, and edit the .profile file from that with **sudo nano**

Or from the grub menu boot to recovery mode, which is usually the second boot option in grub, wait for all the boot-up processes to finish and you'll be presented with a few options. In this case, you want the **Drop to root shell prompt** option so press the Down arrow to get to that option, and then press Enter to select it.

The root account is the ultimate administrator and can do anything to the Ubuntu installation (including erase it), so please be careful with what commands you enter in the root terminal.

In recent versions of Ubuntu, the filesystem is mounted as read-only, so you need to enter the follow command to get it to remount as read-write, which will allow you to make changes:
```
mount -o rw,remount /
```
Now reverse the changes you made to .profile using nano (no need for sudo or anything as you're in recovery mode, ie already root) and finally reboot.

---

### Post by deadflowr on 2017-03-25
Can you login through a console mode?
(Press ctrl +alt + F1, or F2, F3,F4,F5,or F6)
It should ask for a login name and then your password (password field will be blank)
Then edit the file you need to edit and run
```
sudo systemctl restart lightdm
```
that will reset you back to the login screen.
and then you can try again.

---

