---
title: "login loop + no .Xauthority + unable to access /home"
date: 2016-02-16
forum: Desktop Environments
---

### Post by salviablue2 on 2016-02-16
Hi guys,
At my wits end.
Ive been goin round in circles trying to login. 

I had 10.04. decided to upgrade, but couldnt becuase i was too late.
So, I repartitioned my HD, Installed 14.04 LTS, but keeping my /home intact.
The first install failed due to some bug or other (cant remember, something to do with being unable to write to .dconf).
I redid the partitioning again (again keeping my /home).
The second install went swimmingly apart from two things.

1) The option to select whether or not to encrypt was greyed out but selected (i hadnt selected it previously)
2) the install took around 2 hours, mostly it was downloading packages (i selected for it NOT to update packages, but to install the proprietary driver and whatnot)

So, after it installed, I rebooted, changed the boot order to boot from the HD, and was brought to the login screen

I type my password.....the screen goes blank, then comes back to the login screen
I then typed in a wrong password to see what it would say if it was a wrong passweoprd and it told me so.
SO, I know i havent gotten the password wrong, it just wont boot into the desktop gui.

I search around ont net and find many others with the same issue.

one of the first hits suggested deleting my .Xauthority file.
So i did (from the guest login, which allows me intot he desktop, but with no su)

rebooted, same thing login loop.

so i went to tty and tried to delete .Xauthority, it didnt say file not found or anything, so i presumed it to be deleted.

reboot, login loop.

I tried some other suggestions.

reinstalled ubuntu-desktop from recovery term

theres no such file as ~/.xsession-errors for me to look in

i cant see anything in dmesg

ls -lah shows:
drwxrwxrwt  5 root         root         4.0K Feb 16 19:54 ..


chown hrafnblod:hrafnblod .Xauthority
gives cannot access no such file or directory

when i ls i get access_your_private_data.desktop

tried logging in through gdm, it hangs after login on the pink (?) screen

ecrypt-mount-private
encrypted private directory is not setup properly

ecrypt-recover-private
finds 2 encrypted volumes the old /home (jascas) and the new one (hrafnblod). I enter the passwords and it says it successfully recovers then and inserts the passkey intot he keyring and they get mounted to /tmp. yet when i cd there, i get a load of error msgs like 
could not find keywith description blah blah - error attempting to find auth tok for fnek something or other

ive tried many other things and nothing seems to work....

any help?

---

