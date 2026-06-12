---
title: "Cant access desktop(white screen)"
date: 2007-04-21
forum: Desktop Environments
---

### Post by sleepyenglish on 2007-04-21
I'm running feisty and had the nvidia driver installed via the restricted driver manager, i removed it because it was taking a while to load my desktop with it enabled. I then restarted and typed my user name and password in which then leads to a  white screen and it never goes, can anybody help as i cant access my desktop to do anything to attempt to fix it?

Thanks

---

### Post by nickle on 2007-04-21
I get the white screen from my install. I had the beta installed and it worked fine. I then decided to to a fresh install linking my old home partition but now I get this white screen... Any ideas or help would be much appreciated...

---

### Post by sleepyenglish on 2007-04-21
If i was to reinstall feisty and create a new account when setting up the new install via the livecd, is there a way i could copy my files from the previous account to the new one?

Edit: Prior to removing the driver and without restarting in between i also removed what i thought was uninstalled application files and folders, would this cause my problem?

Thanks

---

### Post by nickle on 2007-04-21
Ok the install work if I create a new home directory. However, when I try to use my old /home I get the white screen. Obviously there is something in my old config files in my old /home that is causing the problem.... 

Any ideas?

---

### Post by sleepyenglish on 2007-04-22
Nickle ive got exactly the same situation, using the livecd i have managed to back up most of my data however i cant access the hidden folder's which hold the programs settings to back those up. In terms of program setting i only really need the .mozilla folder(firefox bookmarks, passwords etc).

Have you had any more luck or can anyone else help? Thanks.

---

### Post by nickle on 2007-04-22
No luck here I am afraid and I don't have the knowledge to move further. The only information I need in terms of old config files is my firefox browser and my evolution email mail client. I do not think of the rest of my extensive GB in home plays any role.
Luckily I still have my intact Dapper installation (with its /home) which I am using now and a back up copy.  The problem arises when I try to include this /home in the update; I guess there must be some info in one or other of the config files which is causing the problem.
I guess I could delete all the config files (except for the browser and email) and try again. However, this would be a big step since it might risk breaking my intact Dapper system. I was hoping from some suggestions from somebody  who might be able to help us...

---

### Post by sleepyenglish on 2007-04-22
I have now created a fresh install of feisty accompanied by a new user account, is there a sudo command or any thing else i can do to get full privileges to my previous account?

Thank

---

### Post by shae on 2007-04-22
Did you try reconfiguring xorg?  It sounds like a problem with x.  Did you happen to have enabled desktop effects?

---

### Post by ghostofcain on 2007-04-22
I also had the** White Screen Of Death** after I had enabled 'desktop effects' I reconfigured X, tried to kill/remove etc Compiz and nothing the only solution I found that worked was a reinstall overwriting my Home folder which was annoying in the extreme

---

### Post by cessna_89702 on 2007-04-23
I had the same problem when I clicked Desktop Effects.

The screen went white and I hit escape to fix it but it seems like a lot of people are having this problem

---

### Post by sleepyenglish on 2007-04-23
Desktop effects were enabled at the time yes, i guess that's the problem then desktop effects are not disabling automatically upon removal of the drivers. Does this mean my data(or at least what i couldn't copy to a usb because it was locked) is lost?

Thanks

---

### Post by sleepyenglish on 2007-04-23
I've found a work around to back up my data, using the live there for running from the cd i.e. no messed up settings, i created a user account with the same name and password as the of which i cant access. I then logged in and i now have full access to all files/folder on my home partition which means i can back them up, which is great.

---

