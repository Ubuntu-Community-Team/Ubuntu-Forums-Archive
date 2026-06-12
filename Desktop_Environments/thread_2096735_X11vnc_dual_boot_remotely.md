---
title: "X11vnc dual boot remotely"
date: 2012-12-20
forum: Desktop Environments
---

### Post by Shobuz99 on 2012-12-20
I have a question about X11vnc and connecting to a dual boot machine. I have x11vnc setup on my desktop and my laptop.
My desktop is setup as a dual boot with separate drives, one with Ubuntu 10.04 LTS and the other with WinXP and WinVNC server.

Is it possible to reboot the desktop, remotely from my laptop using ssl/ssh vncviewer, and select which side (win or ubuntu) I want to boot? Do I have to have remote control over the GRUB?
I'm not looking for anything fancy; just the ability to choose which OS on my desktop I want to connect to remotely.

Thank you for any ideas you may have.

Shobuz99

---

### Post by Cheesehead on 2012-12-20
Are you booting Grub1 or Grub2?

For example, if you are using Grub1, see the 'default' line in /boot/grub/menu.list, which implements precisely the functionality you seek. Simply change the number to indicate which system you want to boot next time.

---

### Post by Shobuz99 on 2012-12-22
> **Cheesehead said:**
> Are you booting Grub1 or Grub2?

For example, if you are using Grub1, see the 'default' line in /boot/grub/menu.list, which implements precisely the functionality you seek. Simply change the number to indicate which system you want to boot next time.

Doh! I use Grub1 on my dual boot desktop machine.
Thanks Cheesehead. I didn't think of that. How simple. :oops:
I do still have one more issue, though. #-o :confused:
When I boot WinXP from GRUB1, Windows loads, but stops at the "login" screen where I have to choose either "Administrator" or my other login that doesn't require a password. 
"Administrator" DOES require a password and therefore I can't select which one I want to login to, using X11vnc. 
WinVnc server cannot be loaded, until after a Windows login is chosen. 
I forgot to mention that in my original post. Sorry.
I guess I could disable the login screen all together, 
and just auto-login and auto-password (if I can remember how!)
at "Administrator' level; but then my security would be lessened, wouldn't it?

[COLOR="Blue"]Update: I changed the Default num from 0 to 5 and it worked. Thank you.
I have the Windows boot commands at the last position in the /boot/grub/menu.lst.
I also changed the settings in Windows so that it would auto-login to Administrator.
[/COLOR] 
Thank you again.
Shobuz99

---

