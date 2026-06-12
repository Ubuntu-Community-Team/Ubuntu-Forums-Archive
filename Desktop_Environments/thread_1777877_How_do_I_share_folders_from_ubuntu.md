---
title: "How do I share folders from ubuntu"
date: 2011-06-08
forum: Desktop Environments
---

### Post by bobdobbs on 2011-06-08
Hi all.

I'm running ubuntu 10.04, 64bit.

I'd like to be able share a folder, so my windows machine can access it.

At the moment, I can right-click on a folder and access 'sharing options'. But, when I try to set them, I get an error:

> 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Permission denied
You do not have permission to create a usershare. Ask your administrator to grant you permissions to create a share.

Googling, I can see that some people have been able to fix this, but I haven't been able to work it out.

In fact, I've never actually been able to get samba sharing to work on ubuntu at all ever. It weirds me out... a lot of people online seem to say that samba is easy to use and easy to set up. But I've spent many hours trying over many years, and I've always found samba to be a fruitless pain.

If someone could help me to get it working, I would be very pleased.

---

### Post by arubislander on 2011-06-08
Hi bobdobbs,

Could you go to:  System->Administration->Users and Groups in the menu?  You'll get the User Settings dialog.

Once there, select your user and click on Advanced Settings. You'll be asked for your password. If you are an administrator type it in. Then on the tab User Privileges make sure the checkbox in front of Share files with the local network is checked. You should now be able to share folders via samba...

---

