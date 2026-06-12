---
title: "Workaround For Keyring When Auto-Login is Enabled?"
date: 2011-04-08
forum: Desktop Environments
---

### Post by skiesbleed on 2011-04-08
Hello all,

I'm trying to find a workaround for the keyring requirement when auto-login is enabled.

Here's my setup:

I'm primarily using my Linux computer as a server, for Git, FUPPES, OpenVPN, etc. Because of this, I do everything remotely from another computer (Windows 7). Most tasks I need to do I perform through SSH, but sometimes I use VNC to see the desktop, since some things are just easier with a GUI.

My problem is this: I have auto-login enabled, because of how I use the device. However, when it first boots up, I'm unable to connect with VNC unless I physically go to the computer and type my password into the keyring pop-up.

Does anyone know of a way around this? Is there a way for me to input my password into the keyring through SSH, by invoking libpam-gnome-keyring somehow? I've tried to locate this application, but I haven't had much luck.

Thanks in advance.

---

### Post by Copper Bezel on 2011-04-08
If the machine is set to auto-login anyway, do you need to have a password on the keyring at all? Or am I missing something? The keyring password is separate from your login password and set the first time the keyring is accessed.

---

### Post by Krytarik on 2011-04-08
Please see this earlier thread about the same matter:
[http://ubuntuforums.org/showthread.php?t=1676084](http://ubuntuforums.org/showthread.php?t=1676084)

Greetings.

---

### Post by skiesbleed on 2011-04-08
Copper Bezel, I don't want to use a blank keyring password, because then it will expose all of my saved passwords without any sort of protection.

Krytarik, thanks for link to the other thread. I'm going to try out x11vnc as a startup script and see if I can get it to work as desired.

Thank you both for your quick replies!

---

