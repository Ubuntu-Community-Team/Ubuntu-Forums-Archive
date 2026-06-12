---
title: "Xfce4-session-logout is different in same operating system"
date: 2016-09-29
forum: Desktop Environments
---

### Post by ineuw on 2016-09-29
On an Xubuntu 16.04 32bit desktop, on clicking on 'logout' three options appear on a single display, (Log Out, Restart, Shutdown) without a the requirement to confirm. On re-login, and no password was required on initial boot, one can log back in without a password.

On an Xubuntu 16.04 64bit laptop with the same desktop software, when selecting logout, there are no menu choices. One logs off directly and sees the login screen. There one can select Restart or Shutdown from the Xfce4 panel, and either selection prompts for confirmation. On re-login, while no password was required on initial boot, one must type the password.

How can I change the laptop menu to have the same Logout options as the desktop? Both use the same 'Xfce4-session-logout' command.

---

### Post by ajgreeny on 2016-09-30
Are you using the Action Buttons panel applet in your 32bit 16.04, and if not how are you logging out or shutting down?

I'm pretty sure that gives you the options that I think you need, but I'm just about to boot to a VM in virtualbox to check I'm right about that.

Yes; I have booted the VM and using the Action Buttons applet which I always configure to show buttons, not menu items, and I have Shutdown, Reboot, Suspend and Logout, all of which ask for confirmation before anything happens.  However, I thought I had the 32bit system but find it is 64bit, so this may not help you in any way.

---

### Post by ineuw on 2016-09-30
> **ajgreeny said:**
> Are you using the Action Buttons panel applet in your 32bit 16.04, and if not how are you logging out or shutting down?
I'm pretty sure that gives you the options that I think you need, but I'm just about to boot to a VM in virtualbox to check I'm right about that.
Yes; I have booted the VM and using the Action Buttons applet which I always configure to show buttons, not menu items, and I have Shutdown, Reboot, Suspend and Logout, all of which ask for confirmation before anything happens.  However, I thought I had the 32bit system but find it is 64bit, so this may not help you in any way.

ajgreeny, thanks for the info and it's much appreciated. Until now, I never paid attention to Action buttons, but now I tried them. My objection is the prompt and the 30 second delay, plus the additional space this takes up on my crowded Xfce4 panel of a 13.3" display. I am using the identical Menulibre 2.1.3 interface on both computers, and this gave me the desktop layout style with Xubuntu 14.04 on the laptop. Here are the images of the current 16.04 menus. The desktop menu is my preference, everything is together without a prompt or delay. 

[[IMG]http://www16.picfront.org/picture/OKhj65334VW/thb/desktoplogoutxu16-04.jpg[/IMG]](http://www.picfront.org/d/9snP)

[[IMG]http://www16.picfront.org/picture/Bdjcu5dF/thb/laptoplogoutxu16-04.jpg[/IMG]](http://www.picfront.org/d/9snQ)

It also occurred to me the issue of 32 and 64bit OS, but I figured it's worth a try. This post is cross posted on the Xfce4 forum, but without the images, which I will add now. Thanks again.

---

### Post by ajgreeny on 2016-09-30
If what you want is an immediate shutdown, reboot, or suspend you could add a launcher to the panel and make that point to logout from a right click, but edit the command from 
xfce4-session-logout 
to
xfce4-session-logout --halt
xfce4-session-logout --reboot
xfce4-session-logout --suspend 
and rename each edited applet accordingly, depending on which ones you need.

You could also add shortcuts to your desktop if that suits you better using the same commands.

They should all carry out that command without any confirmation delay, so make sure you do not click them inadvertently or you could lose unsaved work.

---

### Post by ineuw on 2016-10-01
ajgreeny, much thanks for your solutions. I like them both, :-) So, for now, I have them all on the panel and decide later. But then, that is life.

---

### Post by ajgreeny on 2016-10-01
Great! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by rosk333 on 2017-03-31
Which logout method you get - Either a 3 button Logout/Restart/ShutDown panel - OR immediate logout and then a login panel - is SELECTED by:
Settings - Session and Startup - General - Logout Settings - Prompt on Logout
If ticked you get the 3 button panel. If not you are logged out and then get the login panel.

---

