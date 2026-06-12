---
title: "GDM - Automatic login asking for password"
date: 2006-06-16
forum: Desktop Environments
---

### Post by niitsu on 2006-06-16
Hello there.
I've switched completely to Dapper a month ago, and as my parents are not accostumated typing an user and a password in the start of the session, I've configured my GDM for automatic login with a commom user.
Everything was going fine til yesterday's update. After that my Ubuntu shows a little windows in the beginning of the session written something like: "Automatic Session Start (niitsu)", and asking for the password.
How can I get rid of it, leaving my automatic login really automatic?

Best regards!
Jeff

---

### Post by reztho on 2006-06-16
Glad to know I'm not the only one. As I stated here: [http://www.ubuntuforums.org/showpost.php?p=1144871&postcount=23](http://www.ubuntuforums.org/showpost.php?p=1144871&postcount=23) ...I'm having the same problem like you.

---

### Post by frodon on 2006-06-16
You're not alone with this problem and it seems to be related to the latest update, the bug has been reported and a fix will surely be available really soon in the repositories.

---

### Post by soonindallas on 2006-06-16
[QUOTE=niitsu]Everything was going fine til tomorrow's update.[/QUOTE]

yikes! I'll make a note to self to skip tomorrow's update ;)

if it's any consolation there are others with the same problem and at least 2 bugs have been filed:

[https://launchpad.net/distros/ubuntu/+source/shadow/+bug/49976](https://launchpad.net/distros/ubuntu/+source/shadow/+bug/49976)
[https://launchpad.net/distros/ubuntu/+source/gnome-desktop/+bug/49973](https://launchpad.net/distros/ubuntu/+source/gnome-desktop/+bug/49973)

keep an eye on the threads, an answer will come soon.

---

### Post by niitsu on 2006-06-16
**soonindallas**: Wow, gotta go back to my english school asap. :D 
Thanks for the correction, I've fixed it in my original post.

Regards!

---

### Post by reztho on 2006-06-16
Wow... It was really fast:

[https://launchpad.net/distros/ubuntu/+source/gnome-desktop/+bug/49940](https://launchpad.net/distros/ubuntu/+source/gnome-desktop/+bug/49940)

Fixed!

Now I'm waiting for my local ubuntu repository mirror to get the fix.

---

### Post by BobBlum on 2006-06-16
I'm having the same problem:  autologon is now requiring a password.  How can I download the patch that fixes this problem?

Thanks in advance for any help on this.

---

### Post by BobBlum on 2006-06-16
Work-around is posted on Launchpad, at [https://launchpad.net/distros/ubuntu/+source/gnome-desktop/+bug/49940](https://launchpad.net/distros/ubuntu/+source/gnome-desktop/+bug/49940).

It entails reverting back to the previous version of gdm (version 2.14.6-0ubuntu2.
Go to Synaptic Package manager.
Search for gdm.
Click on gdm.
On the top-line menu of Synaptic, click on Package.
Select Force Version...
From the drop-down menu, select 2.14.6

---

### Post by BobBlum on 2006-06-16
Correction:

In Synaptic Package Manager, better to force the version 2.14.6-0ubuntu2.1 of gdm, rather than version 2.14.6.  Sorry for any inconvenience caused by my previous post.

---

