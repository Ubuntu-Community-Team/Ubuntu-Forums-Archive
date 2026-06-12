---
title: "Skype trayicon is gone since upgrade to 11.04"
date: 2011-05-10
forum: Desktop Environments
---

### Post by FMaz008 on 2011-05-10
Hi, 

I've upgraded to Ubuntu 11.04, and I still using the old-style Gnome interface (not the notebook style).

When I start skype, the tray icon is not added in the top-bar. And skype is not present in the notification applet.

What I've tried:
- I've tried to reinstall skype
- I've installed dconf-tools and ran dconf-editor, then watched in desktop->unity->panel, Skype is in the systray-whitelist.

Any idea how to get my skype tray icon back ?

---

### Post by Sathish 2011 on 2011-05-10
> **FMaz008 said:**
> Hi, 

I've upgraded to Ubuntu 11.04, and I still using the old-style Gnome interface (not the notebook style).

When I start skype, the tray icon is not added in the top-bar. And skype is not present in the notification applet.

What I've tried:
- I've tried to reinstall skype
- I've installed dconf-tools and ran dconf-editor, then watched in desktop->unity->panel, Skype is in the systray-whitelist.

Any idea how to get my skype tray icon back ?


[COLOR="Blue"]Hi

I am newbie to Ubuntu (11.04). I like Ubuntu it very much. 

I too face the same problem with Skype! 

I am not able to open Skype (even though it runs in the background). So I could not see my contact list and make calls. I am only able to receive calls from my contacts (as it popups up).  

Also it is not allowing to open another (fresh) Skype window. And shows a message "Another Skype instance may exist.."

Can anyone please help us to come out of this issue. 

Thanks in advance.  
[/COLOR]

---

### Post by Tart on 2011-05-11
Same here, using "classic ubuntu." When skype disapears, I kill it in system monitor and start a new one. Tray icon is missing would love to get it back. Any ideas?

Thanks

Update: found this post [http://ubuntuforums.org/showpost.php?p=10794204&postcount=27]("http://ubuntuforums.org/showpost.php?p=10794204&postcount=27")  it helped me - now skype icon is showing.

---

### Post by ilantal on 2011-05-12
I am using Unity and the skype tray icon is a bit flaky. I just had a series of cases where it failed to appear.
I got it back again by trying to activate skype again. There was a grey icon in the tray and it told me that I have another instance running (yes, the one which fails to appear in the tray of course).
With the grey icon I restarted the computer and now it asks me to log in. I give it the password and tell it to log in automatically at start up. Now the green icon is back and working.
Sound like magic? It is and I don't know why it should work.

---

### Post by didaka on 2011-05-13
Hi there,
I got the same problem with upgrade to 11.04 on Ubuntu Classic. I noticed that the **skype icon is actually there**. The problem is that it is only **1px large dot**. If you manage to click it skype will open. I think the problem is in the skype icon itself. 
The solution from **Tart's post  			#[[B]3**]("http://ubuntuforums.org/showpost.php?p=10803886&postcount=3") worked for me[/B]. Thank Tart ;).
Cheers,
Daniel

---

### Post by kmarzi on 2011-05-21
I have this problem since upgrading to 11.04. I use the Classic View too and I've tried everything suggested here; however, the skype icon remains a tiny, 1-pixel image on in the tray...

Any other ideas on to how to get it back?

Thanks,
kmarzi

---

### Post by kmarzi on 2011-05-21
Um, I don't quite know why, but the Skype icon has now strangely appeared... (and I've done nothing new, not even a reboot, which I'd already done numerous times after following the instructions in this thread). Odd...

---

### Post by kmarzi on 2011-05-22
> **kmarzi said:**
> Um, I don't quite know why, but the Skype icon has now strangely appeared... (and I've done nothing new, not even a reboot, which I'd already done numerous times after following the instructions in this thread). Odd...
 
I spoke too soon. The icon comes and goes as it pleases, both when using Unity or Ubuntu Classic. Any ideas how to fix this?

Ta,
Kmarzi

---

### Post by Flaxis on 2011-07-07
Sorry for bumping an old topic, but...
To fix the missing Skype icon in Unity, press alt + f2 and enter "compiz --replace" or "unity --replace". In both commands, a new Unity session will start and the Skype icon will re-appear.

Now I'm trying to get the amsn icon to work properly! :@

---

### Post by James_said_lol on 2011-07-16
Ok guys, for those old school folks, who use the Ubuntu Classic after clean install 11.04:
Skype tray icon is not there because we (the old school folks) prefer to delete everything but volume, wireless, date, and shut down - at least I do it. And u know that these indicators are getting more and more connected with each other with every next distro release, so may be I deleted the area for skype too (or may be its not there by default)

Just start skype and add Notification Area...If u had already started skype the icon should be there. (I was looking like 30min here and there until I realized its not an indicator, but notification icon :oops:)


I dont know if thats a wrong place to post it - just wanted to help if someone is facing this..you marked gnome-panel --replace for a solution.. well I post it here in case someone cant get it done by replacing the panel

---

