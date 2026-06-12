---
title: "Encrypt only the home folder"
date: 2006-08-18
forum: Desktop Environments
---

### Post by leaded on 2006-08-18
I've been reading the wiki and these forums for a couple of days and have not really found the answer I'm looking for. What's the best way to have an encrypted home folder? I'm not concerned with encrypting the entire drive- just my home folder contents. I'm used to OS X, where the home folder is an encrypted sparseimage file until I login. I imagine in Ubuntu I will need to create a separate /home partition and have it encrypted, but can it decrypt at the gdm login instead of boot? If I can only decrypt it at boot, what is still the best way to go about doing this without encrypted every other folder (except /boot, of course)?

Thanks!

---

### Post by waldorf on 2006-10-31
Excellent question! I'd love to hear from someone who knows - anyone?

---

### Post by RichJacot on 2006-11-06
Me also.  /home on edgy.

---

### Post by lorre on 2006-11-11
Me too, not necessary \home  but I am interested in a encrypted directory that get's decrypted on GDM logon.

---

### Post by mat_london on 2006-12-07
Me Too

This would be nice too ....

[http://blog.fubar.dk/?p=64]("http://blog.fubar.dk/?p=64")

---

### Post by bobpaul on 2008-04-15
I'll add my name to the list and bump this topic back up. I use full disk encryption on my desktop (started with [one of these howtos]("https://help.ubuntu.com/community/FeistyEncryptedRootWithInstaller?action=fullsearch&context=180&value=encrypted+filesystem&titlesearch=Titles"), I forget which one. Peruse them and see what suites your needs), but on my Laptop I really only need to secure the contents of ~. 

I suppose I could encrypt the entire /home partition, and then any users that I don't want encrypted define their home folders as /home-unsecure/{username} or similar. I think I've seen howtos that use a pam module to allow your account password to also unlock the HD. Since dmcrypt allows multiple keys to unlock a partition, you could have a "backup password" or key saved on a thumb drive or similar, and then also assign each of your users passwords to be acceptable to unlock the partition as well.

If I find anything, I'll get back. Until then... *bump*

**Edit:** Here's an explanation [using pam similar to how I explained above]("http://gentoo-wiki.com/HOWTO_Encrypt_Your_Home_Directory_Using_LUKS_and_pam_mount"). It's for Gentoo, but most of the stuff is pretty general. (You should be able to ignore the kernel stuff, for example). Would still rather avoid using a partition, as I'd like my encrypted space to freely grow and shrink.

**Edit2:** [I found some more info]("http://www.mepis.org/node/11434")... Mepis is Ubuntu based, and I see encfs is in apt, so this should work well. [According to the Gentoo Wiki article on EncFS]("http://gentoo-wiki.com/TIP_EncFS") "The major advantages of this method, for instance when compared to dmcrypt, is that the space doesn't have to be allocated previously and the filesystem grows as new files are added. A clear disadvantage is that the number and size of the encrypted files are shown in clear." So it's more flexible, but someone can find the size of each file stored within and the number of total files. Also, apparently file meta-data isn't encrypted. So it will secure your tax returns, but someone might be able to figure out it's a PDF or even that it is your tax returns, but at least they won't be able to read them...

---

### Post by bobpaul on 2008-04-17
Ok, I got it and described the steps necessary on this wiki howto.

[https://wiki.ubuntu.com/EncryptedHomeFolder](https://wiki.ubuntu.com/EncryptedHomeFolder)

---

### Post by jbrice on 2008-06-07
> **bobpaul said:**
> Ok, I got it and described the steps necessary on this wiki howto.

[https://wiki.ubuntu.com/EncryptedHomeFolder](https://wiki.ubuntu.com/EncryptedHomeFolder)

Thanks for putting this together - the wiki procedure looks exactly what I need for a laptop. (It really is something that should be a core part of of the system if Ubuntu wants to be taken seriously as an OS for business use.)

HOWEVER you don't specify which version of Ubuntu this is written for, and on trying it with Hardy, I have run into a number of problems. Not least is that this step
> and append "use_first_pass" to each line following pam_encfs.so. 
locks me out of the PC as it causes an authorisation error message to appear after entering the user ID on logging back in to the system.

James B.

---

### Post by bobpaul on 2008-06-25
> **jbrice said:**
> 
HOWEVER you don't specify which version of Ubuntu this is written for, and on trying it with Hardy, I have run into a number of problems. Not least is that this step

locks me out of the PC as it causes an authorisation error message to appear after entering the user ID on logging back in to the system.

James B.

I was using pre-release Hardy on my laptop when I wrote it and have run the daily updates without problems. 

Please post your common-auth, pam_encfs.conf, and the text of the error message and I'll see if I can duplicate it and find a solution for you.

**Edit:** I suspect you had not yet configured pam_encfs.conf. Ensure you have the following *before* you attempt to login.
```
#Same for fuse, note that allow_root (or allow_other, or --public in encfs) is needed to run gdm/X.
fuse_default allow_root,nonempty
``` I just tried changing nonempty to the default "allow_other" and was unable to login.

---

### Post by heatblazer on 2008-06-25
Good article. I was reading with great interest. Take a look here:
Tips
Encrypt your swap partition.

Without an encrypted swap partition, its possible for unencrypted file parts, passwords, or even the encfs key to be written to your swap partition. If swap is not encrypted, this can all be read by an attacker. Downside of this is that hibernate will no longer function. {{explain setting up encrypted swap with dmcrypt/luks}}
Change your password

First, change your account password like normal. Then log out of Gnome/KDE and hit Ctrl+Alt+F1 to go to a virtual terminal. (Alternatively, log into any another user account, open a terminal window and issue 'su testuser')

You need to unmount your home folder: 

I took thish from the link in ubuntu tutorials

[https://wiki.ubuntu.com/EncryptedHomeFolder](https://wiki.ubuntu.com/EncryptedHomeFolder)

---

### Post by heatblazer on 2008-06-25
> **bobpaul said:**
> Ok, I got it and described the steps necessary on this wiki howto.

[https://wiki.ubuntu.com/EncryptedHomeFolder](https://wiki.ubuntu.com/EncryptedHomeFolder)


GREAT JOB, HERE! :popcorn:

---

### Post by bobpaul on 2008-06-25
> **heatblazer said:**
> Good article. I was reading with great interest. Take a look here:
[snip]
I took thish from the link in ubuntu tutorials

[https://wiki.ubuntu.com/EncryptedHomeFolder](https://wiki.ubuntu.com/EncryptedHomeFolder)

Yeah, I guess I never got around to writing the part about encrypting the swap partition. That probably deserves an article on it's own, as it can be done either with a random password--and thus prevent hibernation--or with a constant password--and thus require a password be entered everytime the computer boots up.

---

