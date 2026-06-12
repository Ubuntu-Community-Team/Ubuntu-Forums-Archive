---
title: "No right context menu for Firefox menus under Unity."
date: 2011-05-01
forum: Desktop Environments
---

### Post by MindRiot on 2011-05-01
When Unity is disabled, you can delete a bookmark from Firefox by right-clicking on the bookmark, under the bookmark menu, on the Firefox menu bar.

When Unity is enabled, you cannot delete a bookmark from Firefox by right-clicking on the bookmark, since a right-click behaves the same way a left-click does. In other words, there doesn't appear to be any context menus.

I reverted to the so-called "Classic desktop."  There are other aspects about Unity I take issue with, but I will not go into them here.

If the Unity desktop is to be the default desktop for Ubuntu, then it must retain, at a minimum, mind you, the same functionality that was provided by the prior desktop.  Access to an application's context menus is one functionality I see no good reason to forgo.

---

### Post by lovinglinux on 2011-05-01
Is not a Unity issue, but an issue with the *firefox-globalmenu*. You should report the problem to the developers.

Instead of disabling Unity you can simply remove the *firefox-globalmenu* package and you will regain that functionality.

```
sudo apt-get remove firefox-globalmenu
```

Alternatively, you can use the Bookmarks button (the one with an arrow). You can delete bookmarks from it, even with the global menu installed. However, you cannot see this icon unless you move it from the navigation toolbar to another toolbar. to do that, right-click on the toolbar, select "customize". You will see it on the right-corner of the navigation toolbar. Move it to the tabs bar, the add-ons bar or the bookmarks bar.

---

### Post by MindRiot on 2011-05-01
I've discovered that clicking on "Show all Bookmarks" opens the bookmark library from which bookmarks can be deleted from a right-click context menu.

As far as Unity is concerned, I simply don't like it.  Or, I don't like the way its currently implemented. The issue with Firefox is only one of several. Gnome 3 is a better approach, but that's still too buggy to use. Whatever. I'm not going to discuss the merits or shortcomings of Unity with anyone here. To put it bluntly, I don't care what anyone else thinks. I don't allow others to think for me.

Thanks lovinglinux for replying.

BTW, I noticed you're the one who created Flash Aid.  I hoped using your add-on would resolve the white screens I've been experiencing. Unfortunately, it has not done so.  Of course, that's not the fault of your add-on, it just means that flash playback isn't the culprit.  In any event, thank you for creating the add-on.

---

### Post by lovinglinux on 2011-05-01
> **MindRiot said:**
> I've discovered that clicking on "Show all Bookmarks" opens the bookmark library from which bookmarks can be deleted from a right-click context menu.

You can also open the bookmarks tree on the sidebar.

> **MindRiot said:**
> 
As far as Unity is concerned, I simply don't like it.  Or, I don't like the way its currently implemented. The issue with Firefox is only one of several. Gnome 3 is a better approach, but that's still too buggy to use. Whatever. I'm not going to discuss the merits or shortcomings of Unity with anyone here. To put it bluntly, I don't care what anyone else thinks. I don't allow others to think for me.

Well, I moved to KDE when they release the first gnome-shell preview. I couldn't be happier. KDE is awesome and Kubuntu 11.04 is gorgeous. 


> **MindRiot said:**
> 
Thanks lovinglinux for replying.

BTW, I noticed you're the one who created Flash Aid.  I hoped using your add-on would resolve the white screens I've been experiencing. Unfortunately, it has not done so.  Of course, that's not the fault of your add-on, it just means that flash playback isn't the culprit.  In any event, thank you for creating the add-on.

You are welcome. Does this white screens happens on any video or just on YouTube?

---

### Post by MindRiot on 2011-05-01
> **lovinglinux said:**
> 
Well, I moved to KDE when they release the first gnome-shell preview. I couldn't be happier. KDE is awesome and Kubuntu 11.04 is gorgeous. 

I've had issues running KDE in the past, so I didn't consider it an alternative.  Instead, I've installed Linux Mint 10.  So far, though admittedly that has been a very short period of time indeed, I like what I see and have not encountered any white or black screens. If my system remains stable, I see no reason to go back to Ubuntu. 


> **lovinglinux said:**
> 
Does this white screens happens on any video or just on YouTube?

They occur most often when a webpage contains embedded flash content.  Whether this is an ad, YouTube video, or any other website playing flash video.  Now, I say it occurs most often, especially white screens, but I have experienced black screens when Firefox hadn't been started or was not running.  Whether the problem is with flash, Ubuntu, or my graphics hardware it is difficult to say.  The fact that I'm not experiencing this problem with Linux Mint is suggestive, since I experienced these same issues in Ubuntu 10.10, which Linux Mint 10 is based on.  It will be interesting to see if the problem occurs with the next version of Linux Mint.  If it does not, then the problem must be with Ubuntu, or with an app configured for Ubuntu, such as compiz.  I don't know.  Since I no longer have Ubuntu 11.04 installed, it is difficult to troubleshoot the problem any further.

Again, thanks for taking time to reply.

---

### Post by lovinglinux on 2011-05-01
> **MindRiot said:**
> I've had issues running KDE in the past, so I didn't consider it an alternative.  Instead, I've installed Linux Mint 10.  So far, though admittedly that has been a very short period of time indeed, I like what I see and have not encountered any white or black screens. If my system remains stable, I see no reason to go back to Ubuntu. 

They occur most often when a webpage contains embedded flash content.  Whether this is an ad, YouTube video, or any other website playing flash video.  Now, I say it occurs most often, especially white screens, but I have experienced black screens when Firefox hadn't been started or was not running.  Whether the problem is with flash, Ubuntu, or my graphics hardware it is difficult to say.  The fact that I'm not experiencing this problem with Linux Mint is suggestive, since I experienced these same issues in Ubuntu 10.10, which Linux Mint 10 is based on.  It will be interesting to see if the problem occurs with the next version of Linux Mint.  If it does not, then the problem must be with Ubuntu, or with an app configured for Ubuntu, such as compiz.  I don't know.  Since I no longer have Ubuntu 11.04 installed, it is difficult to troubleshoot the problem any further.

Again, thanks for taking time to reply.

I tried Linux Mint KDE a couple of weeks ago, before installing Natty.

It works really nice. However, it comes with so many repositories, including backports, that I soon got into problems after updates. Initially I though the problem was because I didn't use the Mint update tool, which you can configure to update only with tested packages. But after a second install and some updates, the problems started to show up again. I went back to Kubuntu.

---

### Post by undisclosedname on 2011-05-13
I'm having the same problem, and it's not related to the global menu in Unity. Any right click action will not work in Firefox. I've observed the problem in previous versions of Ubuntu, but it generally only happed after returning from screensaver, as reported here [https://support.mozilla.com/en-US/questions/790613](https://support.mozilla.com/en-US/questions/790613)

With Unity, the problem occurs very often. Not only does it happen after returning from  screensaver, but upon switching between workspaces as well.

Anyway, I've started a thread about this issue here:
[http://ubuntuforums.org/showthread.php?t=1739239](http://ubuntuforums.org/showthread.php?t=1739239)

---

### Post by VitasLoWang on 2012-11-09
Is there any progress with this? This bug is terribly annoying. I have Ubuntu 12.04 and FireFox 16 and it is still happening! No right click anywhere is working. And I cannot even show the overflown bookmarks from the bookmark toolbar (show more bookmarks), because the button does nothing. Reopening FireFox seems to help for some time...

---

