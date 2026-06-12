---
title: "Modem Monitor Applet requires password for every login"
date: 2005-04-10
forum: Desktop Environments
---

### Post by lrseubert on 2005-04-10
I am helping a friend set up Ubuntu on his computer.

Internet access is fully functional via his hardware modem. Firefox and Evolution work completely. Had to use sudo pppconfig to get everything set up just right.

He installed the Modem Monitor Applet in the Taskbar. However, it won't go online when he selects the <Activate> choice from the pulldown menu. Instead, he has to enter his user password, and only then will the applet fire up the modem and connect.

Obviously, it is very annoying to have to enter a password every time one needs to use the modem.

The user permissions have been set up to allow his user account full access privileges to the modem device and accessing the internet via modem.

How can one configure the Modem Monitor applet to work correctly, and not require a password to do its job?

Thanks for any advice you might have.

Cheers,
Luke Seubert

---

### Post by pchachte on 2005-04-27
As I wrote in a previous post:

you can add your user to group tty;

sudo adduser charles tty

and now I don't have to type in a password.  

I'm not sure whether this puts you at risk,  however, so be careful.

---

