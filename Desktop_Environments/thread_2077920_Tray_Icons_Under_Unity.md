---
title: "Tray Icons Under Unity"
date: 2012-10-29
forum: Desktop Environments
---

### Post by Brandon9000 on 2012-10-29
I have an application which people install on various Linux distributions including Ubuntu. The application creates a tray icon for itself. Recently, I have been told, and I have personally verified, that the icon doesn't display under Unity. What can I do about this? I have tried the whitelist thing about twenty times and it doesn't have any effect, even when I log out and back in.
 
Thanks in advance.
 
Brandon

---

### Post by grahammechanical on 2012-10-29
The icons that we see in the top panel are called app-indicators. If the developers of that application have not integrated the application into Unity by giving it an app-indicator that can go in the top panel, then there is little that you can do about it. In my opinion.

---

### Post by Brandon9000 on 2012-10-30
I'm the developer.  I want it to keep working on Ubuntu as it has in the past before Unity.  Are you saying that the only way to make the tray icon show is to do Unity specific programming?

---

### Post by markbl on 2012-10-30
> **Brandon9000 said:**
> I'm the developer.  I want it to keep working on Ubuntu as it has in the past before Unity.  Are you saying that the only way to make the tray icon show is to do Unity specific programming?
Yes. And believe it or not, if you want your icon to appear always in the gnome-shell panel (which is the other new linux new 3D desktop, e.g. on Fedora), then you have to code to a completely different api there also. Ridiculous isn't it, but that is what you get when young developers take over and do their own thing. Try finding some decent documentation on all this stuff btw!

---

### Post by Brandon9000 on 2012-10-31
I know what you mean.  If this is as complete and immutable as you say, it will soon be reversed.  I found countless Web pages claiming I could make my app appear by adding it to the whitelist, but changing it to 'all' didn't work.  Is there any documentation on this (albeit less than decent) that I could use as a starting point?

---

### Post by mosaic2s on 2012-10-31
try cinnamon. it will solve the issue.

---

### Post by kostkon on 2012-10-31
> **Brandon9000 said:**
> I know what you mean.  If this is as complete and immutable as you say, it will soon be reversed.  I found countless Web pages claiming I could make my app appear by adding it to the whitelist, but changing it to 'all' didn't work.  Is there any documentation on this (albeit less than decent) that I could use as a starting point?
You can start from [here]("http://developer.ubuntu.com/resources/technologies/application-indicators/").

---

### Post by markbl on 2012-10-31
<deleted>

---

### Post by karlstad on 2012-10-31
> **Brandon9000 said:**
> I have an application which people install on various Linux distributions including Ubuntu. The application creates a tray icon for itself. Recently, I have been told, and I have personally verified, that the icon doesn't display under Unity. What can I do about this? I have tried the whitelist thing about twenty times and it doesn't have any effect, even when I log out and back in.
 
Thanks in advance.
 
Brandon

From what I recall, you can whitelist apps for the "systray" in Unity with gsettings. Try

```
gsettings get com.canonical.Unity.Panel systray-whitelist
```

and possibly try adding your binary to the list, e.g.

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'Update-notifier', 'yourapp']"
```

You probably need to log in and out again to see if it works.

---

### Post by Brandon9000 on 2012-11-01
> **karlstad said:**
> From what I recall, you can whitelist apps for the "systray" in Unity with gsettings. Try
 
```
gsettings get com.canonical.Unity.Panel systray-whitelist
```
 
and possibly try adding your binary to the list, e.g.
 
```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'Update-notifier', 'yourapp']"
```
 
You probably need to log in and out again to see if it works.
 
Modifying the whitelist the first thing I tried and I tried it no less than ten times. It has no effect.
 
However:
 
[root.linux systray]# gsettings get com.canonical.Unity.Panel systray-whitelist
No such schema 'com.canonical.Unity.Panel'
[root.linux systray]#

---

