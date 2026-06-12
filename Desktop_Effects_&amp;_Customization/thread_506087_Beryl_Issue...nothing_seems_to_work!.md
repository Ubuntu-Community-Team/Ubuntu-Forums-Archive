---
title: "Beryl Issue...nothing seems to work!"
date: 2007-07-21
forum: Desktop Effects &amp; Customization
---

### Post by ukulele_ninja on 2007-07-21
Im so excited to try and get Beryl up and running, but it seems like I keep hitting brick walls!

My issue is that When I run Beryl, It removes my window frames and wont let me type in any text boxes. How do you fix this?

I have:

Compaq R4000 with ATI Radeon Xpress 200M

Dont know how to get this up and running, any help would be great!

---

### Post by AlexenderReez on 2007-07-21
have you enable your graphic card support...?is it aixgl or xgl?please start beryl using terminal with > beryl-manager 

post the output here:)

---

### Post by Kingsley on 2007-07-21
I have the same ATI on my desktop and it's complete crap for beryl. You need to install the fglrx drivers to get direct rendering and then you have to use XGL to get Beryl working. Beryl can work but is very slow with an Xpress 200 card.

---

### Post by ukulele_ninja on 2007-07-21
> **Kingsley said:**
> I have the same ATI on my desktop and it's complete crap for beryl. You need to install the fglrx drivers to get direct rendering and then you have to use XGL to get Beryl working. Beryl can work but is very slow with an Xpress 200 card.

Can u post how to do that?

---

### Post by ukulele_ninja on 2007-07-21
> **AlexenderReez said:**
> have you enable your graphic card support...?is it aixgl or xgl?please start beryl using terminal with  

post the output here:)

Ok, heres what I got, I had to restart because it cut off my borders and I couldnt type again! More stuff happened after this but it didnt save when I told it too.

Error: BadDevice, invalid or uninitialized input device 169
major opcode: 148
Minor opcode: 3
Failed to open device
Resource ID:0X0
X Error: BadDevice, invalid or unititalized input device 169
Major opcode: 148
Minor Opcode: 3
Resource ID: 0X0
Failed to open deivce

(beryl-manager:11744): Gtk-CRITICAL **: gtk_check_menu_item_set_active: assertio
n 'GTK_IS_CHECK_MENU_ITEM (check menu_item)' failed

Then It repeated the Bad Device errors.... more stuff happened after that but I couldnt get it.

---

### Post by 3rdalbum on 2007-07-21
The [Beryl Project wiki]("http://wiki.beryl-project.org/") has a good HOWTO about that - I used it about a week ago to set up Beryl on my computer with an ATI Radeon Xpress.

Unfortunately, the wiki was getting defaced apparantly, so it's down at the moment.

Using any other guides could bork your system, so I suggest waiting until the wiki is back up and then using their guide for Ubuntu.

But first you need to set up your ATI proprietry driver. Go into System > Adminsitration > Restricted Drivers Manager. Enable the ATI driver. Reboot, and you will have 3D acceleration.

XGL is more complicated to set up, so wait until the wiki is back up.

---

### Post by ukulele_ninja on 2007-07-21
> **3rdalbum said:**
> The [Beryl Project wiki]("http://wiki.beryl-project.org/") has a good HOWTO about that - I used it about a week ago to set up Beryl on my computer with an ATI Radeon Xpress.

Unfortunately, the wiki was getting defaced apparantly, so it's down at the moment.

Using any other guides could bork your system, so I suggest waiting until the wiki is back up and then using their guide for Ubuntu.

But first you need to set up your ATI proprietry driver. Go into System > Adminsitration > Restricted Drivers Manager. Enable the ATI driver. Reboot, and you will have 3D acceleration.

XGL is more complicated to set up, so wait until the wiki is back up.


I have Kubuntu, how do I get to the administrator menu?

---

### Post by ukulele_ninja on 2007-07-21
> **Kingsley said:**
> I have the same ATI on my desktop and it's complete crap for beryl. You need to install the fglrx drivers to get direct rendering and then you have to use XGL to get Beryl working. Beryl can work but is very slow with an Xpress 200 card.

From what I read, If set up correctly, there should be no problem running beryl with the 200M.

---

### Post by DDRFreak21 on 2007-07-21
Lol, this problem seems to be going around a lot, try my post here:

[http://ubuntuforums.org/showthread.php?t=423861&page=3](http://ubuntuforums.org/showthread.php?t=423861&page=3)

---

### Post by ukulele_ninja on 2007-07-22
I tried that but when it opens my editor, there is nothing in the xorg.conf file

---

