---
title: "Automatically start up with Cinnamon (3) within/upon Ubuntu (16.04 LTS)"
date: 2017-05-23
forum: Desktop Environments
---

### Post by xinuzi on 2017-05-23
Maybe you prefer sth different from the Ubuntu/Xenial/Unity default desktop.
The hardly configurable top menu can be a nag for some for one.

Cinnamon can be the solution. After installation you can select it in the startup sessions screen. 
Automatically logging into it at startup could be confusing.
Below links/explanations concerning installing the cinnamon desktop and about lightdm, the startup manager.

I had some trouble with it myself.
The solution was **NOT TO USE CAPITAL LETTERS**.

**Call/open:**

```

gksudo gedit /etc/lightdm/lightdm.conf

```

**Set:**

[Seat:*]
user-session=cinnamon
autologin-user=yourusername

The 'user-session'-name can be found in '**/usr/share/xsessions**'. So, even if it says 'Cinnamon' there, set 'cinnamon' in lightdm.conf. 
The same for autologin-user=yourusername (all in lowercase letters).

Of course 'user-session' could be sth else or could be left out (for starting up with default ubuntu). Leaving autologin-user empty should let you startup with the login-screen again.

At least this is how I've understood the session-autologinthing and this is what is working for me.

P.S.: Cinnamon can seem to be slow at first. Go to Settings/Effects and put off all effects.

**Links**:

[https://www.unixmen.com/install-cinnamon-3-0-ubuntu-16-04-lts/](https://www.unixmen.com/install-cinnamon-3-0-ubuntu-16-04-lts/)
[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)
[URL="https://wiki.debian.org/LightDM"]https://wiki.debian.org/LightDM


[/URL]

---

### Post by deadflowr on 2017-05-23
I use an easier method, no editing required.
simply login as usual, then logout.
At the login screen switch desktop sessions.
Login.
Then reboot or shutdown and the next login will auto-login to whichever session was last set.
easy peasy

---

### Post by xinuzi on 2017-05-25
> **deadflowr said:**
> I use an easier method, no editing required.
simply login as usual, then logout.
At the login screen switch desktop sessions.
Login.
Then reboot or shutdown and the next login will auto-login to whichever session was last set.
easy peasy

I'm sorry, deadflowr, but automatically logging into the last used xsession didn't work here that way. 

Normally, without autologin selected in Ubuntu Unity, the Unity Greeter opens with the different manual login possibilities.
In the case of the installed cinnamon (3) 'skin'/session, I select 'Cinnamon' and enter password.
Within Cinnamon there is nothing gui-matic to select autologin at next startup (Linux Mint Cinnamon e.g., also running upon Ubuntu, does have a graphical way for automatically logging in next time, into Mint that is).

When I start up with Ubuntu Xenial Unity after having selected autologin in user settings, it won't (of course) suddenly open the Cinnamon session at next system startup, but Ubuntu Default.

Editing lightdm works fine. On condition that the use of capital letters in user and xsession name is avoided!

---

