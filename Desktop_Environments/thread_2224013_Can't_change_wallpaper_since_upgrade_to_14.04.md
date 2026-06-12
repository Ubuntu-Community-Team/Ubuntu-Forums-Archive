---
title: "Can't change wallpaper since upgrade to 14.04"
date: 2014-05-14
forum: Desktop Environments
---

### Post by ken0542 on 2014-05-14
I'm running Xubuntu on my old Dell, and have had very few (non self inflicted) problems up till now, but I've found an issue since upgrading to 14.04. As per the  attached screenshot, there are no thumbnails of wallpapers showing in  the selector although the original wallpaper remains as do the panels  & icons. If I run the desktop manager via sudo, the thumbnails show  clearly, and can be selected, but the wallpaper can't be changed. I've tried  setting it via Ristretto, gThumb & the GIMP, all without success.

lsb_release  tells me I have Ubuntu 14.04 LTS and apt-cache policy provides:  4.11.6-1ubuntu1. I don't know whether there are issues there or not,  Google hasn't given me much at all.

Can anyone please advise? I'll be extremely grateful (which isn't as good as cash but is all I can manage)!!

[ATTACH=CONFIG]253148[/ATTACH]

---

### Post by kc1di on 2014-05-14
The wallpapers are found in /usr/share/xfce4/backdrops. Check to make sure the files are there. If you want to add other wallpapers copy and past them there.
you will have to be root to do that.   

Any wallpapers found in that file should be there. the selector even lets you do a slide shows, works great on my xubuntu install here.  

if the files are there and the settings manager does not see them. 
then try re installing xfce4

---

### Post by slickymaster on 2014-05-14
If by any chance, you don't find/have the Xubuntu community wallpapers in the path kc1di mentioned, you can always install it now:```
sudo apt-get update
sudo apt-get install xubuntu-artwork
```

---

### Post by Toz on 2014-05-14
> **ken0542 said:**
> IIf I run the desktop manager via sudo, the thumbnails show  clearly, and can be selected, but the wallpaper can't be changed. 

You really shouldn't run user configuration utilities with sudo, there is a good chance that the permissions on the configuration files get changed and owned by root. This may be the cause of the problem. 

Can you open a terminal window, type in the following commands, and post back the results:
```
ls -l $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/
```
...and:
```
ls -l $HOME/.cache/sessions
```

---

### Post by ken0542 on 2014-05-15
**kc1di**

Seems to have all the files there. All the permissions appear ok, but it still hates me for some reason. I'll have a look at a few other things first, but as a last resort I just might have to reinstall :(

Thanks for your assistance, it's much appreciated.

---

### Post by ken0542 on 2014-05-15
**slickymaster**

If only it were that simple. Unfortunately (or fortunately - I'm unsure which is appropriate) the files are all in that folder.

Thanks for helping. I do appreciate it.

---

### Post by ken0542 on 2014-05-15
**Toz**

> **Toz said:**
> You really shouldn't run user configuration utilities with sudo, there is a good chance that the permissions on the configuration files get changed and owned by root. This may be the cause of the problem. 


Can you open a terminal window, type in the following commands, and post back the results:
```
ls -l $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/
```
...and:
```
ls -l $HOME/.cache/sessions
```



[COLOR=#0000ff]I don't run it as root in the normal course of events. I only did it  this time to see if it would work after I couldn't run it successfully  as a normal user.[/COLOR]

[COLOR=#0000ff]
-----[SNIP]-----

ken@cernunnos:~$ ls -l $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/
total 96
-rw-rw-r-- 1 ken  ken   757 Dec  3  2011 displays.xml
-rw-rw-r-- 1 ken  ken   203 Mar 25  2013 keyboards.xml
-rw-rw-r-- 1 ken  ken  1045 May 15 21:30 parole.xml
-rw-rw-r-- 1 ken  ken   779 May 14 15:40 ristretto.xml
-rw-r--r-- 1 ken  ken  1768 Nov 15  2011 thunar-volman.xml
-rw-rw-r-- 1 ken  ken  2882 May 15 11:40 thunar.xml
-rw-rw-r-- 1 ken  ken  1931 Mar 25  2013 xfce4-appfinder.xml
-rw-r--r-- 1 root root 5836 May 14 18:22 xfce4-desktop.xml
-rw-rw-r-- 1 ken  ken  9414 Nov  2  2011 xfce4-keyboard-shortcuts.xml
-rw-rw-r-- 1 ken  ken  1256 Apr 22 17:02 xfce4-mixer.xml
-rw-rw-r-- 1 ken  ken   329 Apr 22 11:36 xfce4-notifyd.xml
-rw-rw-r-- 1 ken  ken  9384 May 16 09:08 xfce4-panel.xml
-rw-rw-r-- 1 ken  ken  2078 Apr 22 11:31 xfce4-session.xml
-rw-rw-r-- 1 ken  ken   512 Jun  6  2013 xfce4-settings-editor.xml
-rw-rw-r-- 1 ken  ken   391 May 14 18:07 xfce4-settings-manager.xml
-rw-rw-r-- 1 ken  ken   262 May 28  2012 xfprint.xml
-rw-rw-r-- 1 ken  ken  4963 Apr 22 11:37 xfwm4.xml
-rw-r--r-- 1 ken  ken  2323 Feb 23 12:20 xsettings.xml


and


ken@cernunnos:~$ ls -l $HOME/.cache/sessions
total 40
drwx------ 2 ken ken 4096 Feb  9 22:09 thumbs-cernunnos:0
drwx------ 2 ken ken 4096 Apr 20 12:48 thumbs-cernunnos:10
-rw-rw-r-- 1 ken ken 2338 May 15 22:33 xfce4-session-cernunnos:0
-rw-rw-r-- 1 ken ken 2338 May 13 22:30 xfce4-session-cernunnos:0.bak
-rw-rw-r-- 1 ken ken 2170 Apr 20 12:48 xfce4-session-cernunnos:10
-rw-r--r-- 1 ken ken 1134 Feb 21 15:09 xfwm4-200cd3f3e-42ff-460a-a42a-d4a49ee2ae68.state
-rw-r--r-- 1 ken ken 1156 Feb 11 14:05 xfwm4-20f258394-fac6-43c8-9eaa-ca3065dca5c7.state
-rw-r--r-- 1 ken ken 1473 Feb 11 13:01 xfwm4-243699c46-9883-4821-ad3d-93d598cc6d8b.state
-rw-rw-r-- 1 ken ken  402 Apr 20 12:48 xfwm4-2d94ffbd0-a519-43b3-bd00-a631e1aef90f.state
-rw-r--r-- 1 ken ken  735 Apr 18 12:11 xfwm4-2fdf0755c-9820-4c67-9318-3e0598e256e1.state


...there it is as requested. I'll leave the interpretation up to you :)

Thankyou very much for offering your assistance. I might use Linux exclusively nowadays, but I've still got a lot to learn and any help is greatly appreciated.[/COLOR]

---

### Post by Toz on 2014-05-15
> -rw-r--r-- 1 **[COLOR="#FF0000"]root root[/COLOR]** 5836 May 14 18:22 xfce4-desktop.xml
This file should not be owned by root, but rather by you. Try changing the ownership:
```
chown ken:ken $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-desktop.xml
```

I would also clear out your sessions cache in case something in there is amiss. To clear the sessions cache: Settings Manager >> Session and Startup >> Session >> "Clear saved sessions".

Then log out and back in again and test to see.

---

### Post by ken0542 on 2014-05-22
> **Toz said:**
> This file should not be owned by root, but rather by you. Try changing the ownership:
```
chown ken:ken $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-desktop.xml
```

I would also clear out your sessions cache in case something in there is amiss. To clear the sessions cache: Settings Manager >> Session and Startup >> Session >> "Clear saved sessions".

Then log out and back in again and test to see.

Bingo!! Thanks very much. Didn't need to clear the session, just changing ownership of that file has saved the day. Glad you knew where to look, as I certainly didn't. Not only fixed it but I've learned something too. 

Thanks again.
See ya
Ken

---

