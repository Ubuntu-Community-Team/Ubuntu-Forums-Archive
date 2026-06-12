---
title: "Unity Faulty After Gnome Install/Deinstall"
date: 2013-06-18
forum: Desktop Environments
---

### Post by buzzingrobot on 2013-06-18
Unity on 13.04 here has gone a bit wonky after installing, and deinstalling, Gnome from the PPA. That experience included a spontaneous logout during the install.

Here's the list:

1. The default blue Gnome wallpaper remains.

2. The top System Settings panel is missing. 

3. The words "Ubuntu Desktop" do not appear at the left of the panel.

4. Global menus are not working correctly. E.g., when I open Terminal, the word "Terminal" appears twice at the left of the panel, and the traditional menu appears on the Terminal window.

5. Right-click on the desktop is ignored.

I've tried several suggestions, resetting compiz, unity, reinstalling  unity and ubuntu-desktop, etc., etc.  None of these changes result in any visible change.

Advice kindly solicited.

[EDIT:  After my last logout, lightdm won't let me log in. Plus, this system is set for auto login, yet on a reboot I am prompted for the password.  Guest session does not work.  I can open a console and log in there.]

---

### Post by hamishmb on 2013-06-18
This should cover global menus: 
sudo apt-get install --reinstall appmenu-gtk appmenu-gtk3 appmenu-qt
To bring right-click back I'd use ubuntu-tweak. If you have that installed, open it and go to "desktop icons" in the tweaks tab, and make sure "show desktop icons" is on. 

Hope this helps.

---

### Post by stinkeye on 2013-06-18
> **buzzingrobot said:**
> Unity on 13.04 here has gone a bit wonky after installing, and deinstalling, Gnome from the PPA. That experience included a spontaneous logout during the install.


When you say "deinstalling", did you purge the pppa or just uninstall packages and disable the ppa?

---

### Post by buzzingrobot on 2013-06-19
> **stinkeye said:**
> When you say "deinstalling", did you purge the pppa or just uninstall packages and disable the ppa?

Purge.

Things are in something of a mess.  I don't suppose that involuntary logout during the install helped matters.  As it is, lightdm won't log me in, but I can log in on a console. 

I did get Unity back, of sorts. (2D?) All the wrong colors, a black background, anything I clicked went out of focus and became blurry. Ran CCSM and found that the Unity plugin was disabled and the option to enable it was grayed out.

Going to reinstall.  It's on a Macbook, so that complicates matters.

---

