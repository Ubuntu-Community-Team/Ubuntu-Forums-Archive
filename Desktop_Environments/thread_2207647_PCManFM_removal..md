---
title: "PCManFM removal."
date: 2014-02-24
forum: Desktop Environments
---

### Post by MM360 on 2014-02-24
Hello, does anybody know if removing the PCManFM would cause any trouble to the system? I'd like to switch completely to Thunar, but I don't know if removing the default Lubuntu file manager would be a good idea. Thank you.

---

### Post by Rex Bouwense on 2014-02-24
Since LXDE is composed of mostly components that are meant to run with little interface (or at least as little as possible) with others, it probably will not cause any trouble with the system.  However, unless you are in a hurt for space on your hard drive, it doesn't hurt to leave it on either.  You never know, you may want to return to it sometime.  Thundar may bring additional required libraries.

---

### Post by Lars Noodén on 2014-02-24
The only place you might have to check could be in Preferences->Default Applications for LXSession

If you remove PCManFM, it will say that the following packages will be removed:  lubuntu-core, lubuntu-default-session, lubuntu-default-settings, lubuntu-desktop and pcmanfm.  However, most of those are just meta packages which won't actually take anything away when they go.  

In worst case you can put them back if you find that something did go wrong.

---

### Post by MM360 on 2014-02-24
You're right, I should probably keep both, I don't have any space problem (500GB). Do you know any way to make Thunar the default file manager for the usb devices? I'm handling a lot of files on usb sticks and I constantly have to close PCManFM and run Thunar. Thank you.

---

### Post by MM360 on 2014-02-24
> **Lars Noodén said:**
> The only place you might have to check could be in Preferences->Default Applications for LXSession

If you remove PCManFM, it will say that the following packages will be removed:  lubuntu-core, lubuntu-default-session, lubuntu-default-settings, lubuntu-desktop and pcmanfm.  However, most of those are just meta packages which won't actually take anything away when they go.  

That sounds scary as hell. I don't think I'm ready to mess with this kind of things, I have no idea about what those packages are. Thank you, that was a very informative description of what I should expect if I tried.

---

### Post by Lars Noodén on 2014-02-24
It's not as bad as it sounds but on the more practical side it would only free up 2084 kB of disk space which is not much at all.  

I'd try the settings in LXDEmenu->Preferences->Default Applications for LXSession->Launching applications->File Manager and see if that has any effect on what gets opened when you plug in a USB stick.

---

### Post by MM360 on 2014-02-24
> **Lars Noodén said:**
> It's not as bad as it sounds but on the more practical side it would only free up 2084 kB of disk space which is not much at all.  

I'd try the settings in LXDEmenu->Preferences->Default Applications for LXSession->Launching applications->File Manager and see if that has any effect on what gets opened when you plug in a USB stick.

I found the File Manager under the Running Applications menu, not the Launching one. I assume it does not make any difference. But I can choose three different File Managers from the list: pcmanfm, pcmanfm-qt and... nautilus. There's no Thunar, but apparently i have two other file managers that I never even installed. Now I'm really confused...

---

