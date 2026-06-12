---
title: "Passwords ALL GONE!!!! I can't get in HELP HELP"
date: 2006-03-04
forum: Desktop Environments
---

### Post by tamarku on 2006-03-04
Why oh why did I worry about security on my home PC???!!!  I changed my passwords for the root user and my user thomas.  Now no matter what I try I get told my password is invalid.  Is there a way to fix this?  I don't really want to re-install because I have my Ubuntu just right.  I tried to go into recovery mode but it asks for my root password.  when I put in what I thought it was it tells me that the password is needs to authenticated but I still can't get in.  I am running 5.10 Breezy.  I don't know how else to get past this and fix it.  

Thanks.

---

### Post by bluevoodoo1 on 2006-03-04
Hmm, maybe this link will be of some help. I haven't tested it, but it's worth a shot...

[http://ubuntuforums.org/showthread.php?t=133102&highlight=password](http://ubuntuforums.org/showthread.php?t=133102&highlight=password)

---

### Post by taurus on 2006-03-04
Yeah, you need to boot your machine into a recovery mode and change your password to something that you can remember next time!!!  Just so you know, lower case letters are NOT the same as upper case in Linux (or Unix)...

---

### Post by Xian on 2006-03-04
[QUOTE=tamarku]Why oh why did I worry about security on my home PC???!!!  I changed my passwords for the root user and my user thomas.  Now no matter what I try I get told my password is invalid.  Is there a way to fix this?  I don't really want to re-install because I have my Ubuntu just right.  I tried to go into recovery mode but it asks for my root password.[/QUOTE]

You can't use the recovery mode because you set a root password. If you had not done that, then it would automatically drop you into a shell with admin priviledges. Why did you set a root password in the first place?? Have you not been using the sudo command? To fix this you will need to work from another medium or partition.

Best bet would be to use a LiveCD (if you don't have a separate Linux install) to chroot into your Ubuntu installation and reset your root pasword using that method. Then you can boot in recovery mode, change your user pass if needed, and regain the proper access to your desktop.

---

### Post by tamarku on 2006-03-04
As always, the forums came through for me.  

I booted from a 5.10 install CD. 
Typed "rescue" 
then was able to set the Root passwd.  
***The I did this was for security.  But I tried to keep the root the same as the user.  When I changed them today for some reason everything got out of whack.  I know about the case sensitive part.  
Once I set the root passwd I did the steps to set the user passwd also.  

In the future is there a way to remove the root password?  Also, rather then going through the ->System --> Administration --> Users and Groups path is there another way to change these passwords?

Anyway, whew, I got through thanks to all the expertise here.  This is one reason I love Ubuntu. Can anyone point me to a good HOW-TO on how to take over the Hard Drive from Windows XP?

Thanks again.

---

### Post by Xian on 2006-03-04
[QUOTE=tamarku]In the future is there a way to remove the root password?[/quote]

$ sudo passwd -l root

> Also, rather then going through the ->System --> Administration --> Users and Groups path is there another way to change these passwords?


$ sudo passwd username

---

