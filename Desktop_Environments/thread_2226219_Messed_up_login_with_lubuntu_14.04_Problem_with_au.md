---
title: "Messed up login with lubuntu 14.04 Problem with autologon"
date: 2014-05-26
forum: Desktop Environments
---

### Post by peter112 on 2014-05-26
Hi all,

Apologies if the answer to this is posted elsewhere I did have a good look around prior to posting but most information seemed to be for older systems. The instructions I found for 14.04 used the GUI to configure (and I am locked out of the GUI.)

I am using lubuntu 14.04 (x86) on an Acer eee901. I was messing with the auto login options (using the GUI) with the intention of having the machine autologon to an account for the kids but still having my account require a password. The GUI seemed a bit reluctant to accept this and kept greying out options (yes in retrospect its not the best idea) eventually I thought I had it and rebooted.

Now on boot the GUI give me the error 'Failed to authenticate', after re-entering the password  the error text disappears but the login box remains and the password field shows 'enter your password' but will not accept any entry. I've rebooted into recovery and used passwd to set the password, so I know I am using the right one.

I have had a look at the .conf files in /etc/lightdm and in /etc/lxdm/ and the autologin line is still '# autologin=dgod'. So either I am doing the wrong thing, or am looking in the wrong place.

I only set up the system yesterday, so could just do a reinstall but I like to try to fix things.

Has anyone got any suggestions?

Thanks in advance

Pete

---

### Post by nknwn on 2014-05-26
**Change your password in the root shell**:

1 - Choose recovery mode at the boot menu
 2 - Drop to root shell prompt

[http://www.instructables.com/id/Resetting-your-password-in-Ubuntu/?ALLSTEPS](http://www.instructables.com/id/Resetting-your-password-in-Ubuntu/?ALLSTEPS)
In the newer versions of Ubuntu, the filesystem state has been defaulted to **read-only**. This means that we can only see the files on the computer from the **root shell prompt**, not edit them like we need to. If the filesystem state is set to read-only, then a simple set on commands can change that.

3 - If you need to change the filesystem state, then enter the following commands after the **root@ubuntu:~#**:

      ***mount -o rw,remount /***

Now, you have read/write filesystem privileges

4 - Now change your password thus:

***passwd **username*

Where '*username*' is replaced by your account name. If '*username*' is a valid account, then you will be prompted to enter a new password, and it will look like this:

       ***Enter new UNIX password:***

Now, to exit the root shell prompt, just type:

       ***exit***

and click enter. You will then return to the Recovery menu. This time, select:

      *** resume                       Resume normal boot***

---

