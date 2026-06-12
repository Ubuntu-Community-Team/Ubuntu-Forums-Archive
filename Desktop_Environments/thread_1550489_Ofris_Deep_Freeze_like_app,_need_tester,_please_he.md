---
title: "Ofris: Deep Freeze like app, need tester, please help"
date: 2010-08-11
forum: Desktop Environments
---

### Post by hok00age on 2010-08-11
I've created PPA for for Ofris: Deep Freeze like app for Linux. There are two versions, Indonesian and English:

Install:
sudo add-apt-repository ppa:tldm217/tahutek.net
sudo apt-get update

Indonesian:
sudo apt-get install ofris

English:
sudo apt-get install ofris-en

After installed, type "ofris" or "ofris-en" in terminal, and follow instruction on screen.

Important thing you have to know:
--- Notes ---
> This application is can't to be used to an usual User. So that, do this following steps to can be used :
- Login to the Administrator User

- Open the following menu : 'System' > 'Administration' > 'Users and Groups'

- In the User Settings window, click 'Unlock' button, and then insert the User Administator password

- Select the User that you will be, then click 'Properties' button

- Click tab 'User Privileges' and give check to the 'Administer the system' checkbox

- Click 'OK' and close the User Settings window

- This application is ready to be used to an usual User.

Thank's in advance.
Sorry for my bad English

---

### Post by hok00age on 2010-08-13
no feedback?

---

### Post by Bonster on 2010-08-27
Hey this is cool, works fine i just tested it

---

### Post by Rytron on 2010-08-27
Excellent program, hok00age. Well done.

---

### Post by hok00age on 2010-08-28
> **Bonster said:**
> Hey this is cool, works fine i just tested it

Thank you for testing and creating video of Ofris at Youtube...

---

### Post by hok00age on 2010-08-28
> **Rytron said:**
> Excellent program, hok00age. Well done.

Thank You for testing ...

---

### Post by Jason Cook on 2010-08-28
I will be testing this. What I have done for my guest account is create a guest.orig folder with all the settings and made a bash script to remove the and copy the original data on reboot. This is a space hogger and I am glad that there is a better method.

---

### Post by hok00age on 2010-08-28
> **Jason Cook said:**
> I will be testing this. What I have done for my guest account is create a guest.orig folder with all the settings and made a bash script to remove the and copy the original data on reboot. This is a space hogger and I am glad that there is a better method.

Please test it and don't forget to post the result

Regards

---

### Post by ethanay on 2010-09-01
hello,

i administer a computer lab and am excited to see this available for Linux.  does it just freeze the /home folder, or will it restore all administrative changes a user makes?

this is important for me to know, since it will affect how i set up my user accounts...

regardless, i will test it and post back!

much thanks

ethan

---

### Post by Jason Cook on 2010-09-01
> **hok00age said:**
> Please test it and don't forget to post the result

Regards

I works great!

> **ethanay said:**
> hello,

i administer a computer lab and am excited to see this available for Linux.  does it just freeze the /home folder, or will it restore all administrative changes a user makes?

this is important for me to know, since it will affect how i set up my user accounts...

regardless, i will test it and post back!

much thanks

ethan

He set it up to only freeze to home folder. I can hack it to do the entire system, but it requires having double the disk space as this makes a copy of the folder in /etc/.ofris/.

I will only hack if he releases ofris under an [OSI]("http://www.opensource.org/") comparable licence, preferably the [BSD Licence.]("http://www.opensource.org/licenses/bsd-license.html")

---

### Post by ethanay on 2010-09-08
Ok, that's what I thought -- much thanks!

---

### Post by Script Warlock on 2010-09-16
thanks for the nice software.. but what about the error that skips something like 

Please insert your choice number : 1

===== Freeze the System =====

Please wait...

rsync: readlink_stat("/home/scriptwarlock/.gvfs") failed: Permission denied (13)
IO error encountered -- skipping file deletion
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1060) [sender=3.0.7]
The system was successfully freezed, please restart your computer now...

[Press any key to exit...]

is this an rsync issue?
strange behaviour during login i can't hear a sound and the sound icon in the panel seems muted and also tried to delete or add some files after locking the system and still not working, im using an admin account in ubuntu 10.04.1.

ofris can be easily unfreezed by unauthorized guest so if possible add a password protect when launching ofris.

---

### Post by Rever75 on 2010-09-17
Great application works great and has been very useful already. Would love to see some improved features but works great as is so far. ):P

---

### Post by TheRem on 2010-12-05
Is there a way to use Ofris but with a specific directory or folder UNfreeze?

Or how do I save files if the system is freeze?

Thanks.

---

