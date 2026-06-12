---
title: "Some Icons Huge"
date: 2015-03-28
forum: Desktop Environments
---

### Post by penguin7009 on 2015-03-28
Hi all and thank you for this great place to use and discuss Ubuntu.  I have just installed Ubuntu Mate 15 and it really looks great and works good too.  I have been using an Icon Theme called Win2-7 for several years.  Usually I just tar it and install it through the theme manager in Mate and it works great.  

However, when I do that in Ubuntu Mate 15, and copy and paste the file in the root icon folder and the /usr/share/folders as usual, they become huge in all the sudo programs.  I tried to change the sizes, add a folder named "scalable" with svg icons in it but haven't been able to understand why this doesn't work.

Can anyone assist?

Thanks, Ralph

---

### Post by bapoumba on 2015-03-29
What do you mean by "sudo programs" ? Graphical applications you run with admin rights with sudo ?

---

### Post by penguin7009 on 2015-03-29
> **bapoumba said:**
> What do you mean by "sudo programs" ? Graphical applications you run with admin rights with sudo ?

Thank you for your reply, bapoumba, yes any program which requires a root login, such as the wireless app or the software manager.  Its seems that all the user programs are fine.  They work as usual.  I've done some more digging and it may be due to the fact that Ubuntu 15 has gone to all .css stuff in the themes and icons?

I don't know how to fix it.  It looks like its not just Ubuntu, but any Linux going to all GTK3 stuff.  Do you or anyone have a clue as to how to fix this if one is not a .css programmer?

Thanks, penguin

---

### Post by bapoumba on 2015-03-29
I take icons work normally with one of the default themes.
Is that the theme you are talking about ? [http://gnome-look.org/content/show.php/Win2-7+Icons+and+sounds+for+Gnomenu?content=114284](http://gnome-look.org/content/show.php/Win2-7+Icons+and+sounds+for+Gnomenu?content=114284)

---

### Post by penguin7009 on 2015-03-29
> **bapoumba said:**
> I take icons work normally with one of the default themes.
Is that the theme you are talking about ? [http://gnome-look.org/content/show.php/Win2-7+Icons+and+sounds+for+Gnomenu?content=114284](http://gnome-look.org/content/show.php/Win2-7+Icons+and+sounds+for+Gnomenu?content=114284)

Its this theme:    
[http://gnome-look.org/content/show.php/Win2-7+Pack?content=113264](http://gnome-look.org/content/show.php/Win2-7+Pack?content=113264)

I originally found out about it on these forums several years ago and have been using it since.  I just tried it with Mate Laguna Theme, which is installed by default and it does the same thing.  Only some of the programs do it.

For instance, if I click on the Network icon on the taskbar its huge.  When I use the software manager, the front page where we look up programs is normal but if while installing a program I click on the progress Icon on the top panel to see how far along the install is, its huge, I would say at least 512 pxls or more.

It started with version 15.04.  I just tried Ubuntu-Mono-Dark and its fine. 

Its got me stumped.

penguin

---

### Post by bapoumba on 2015-03-29
OK thanks. To note, I do not see this on an unmodified Ubuntu-Mate 15.04. I'll install the theme and will report back. but not tonight :)

---

### Post by penguin7009 on 2015-03-29
> **bapoumba said:**
> OK thanks. To note, I do not see this on an unmodified Ubuntu-Mate 15.04. I'll install the theme and will report back. but not tonight :)

Wow, that is "super".  I also do not see that until I install the win2-7 icon package.  I will also keep working on this and see if I can understand what is happening.  Thanks for your help, penguin.

---

### Post by penguin7009 on 2015-03-29
> **penguin7009 said:**
> Wow, that is "super".  I also do not see that until I install the win2-7 icon package.  I will also keep working on this and see if I can understand what is happening.  Thanks for your help, penguin.


I forgot to mention,  this icon package will not install as a complete theme anymore.  I had to go into the "files" folder and copy and paste the win2-7 tar file and extract it into the icons folders.
Thanks, penguin

---

### Post by CantankRus on 2015-03-30
**@penguin7009**,
FYI I installed the folder Win2-7 to /usr/share/icons and don't see any unusually large icons.
Ubuntu Mate 14.04
Maybe a pic and a specific example.

---

### Post by penguin7009 on 2015-03-30
> **CantankRus said:**
> **@penguin7009**,
FYI I installed the folder Win2-7 to /usr/share/icons and don't see any unusually large icons.
Ubuntu Mate 14.04
Maybe a pic and a specific example.

Thank you for your reply, CantankRus.  That is right  I started having this problem on Ubuntu Mate 15.04.  I'm going to re-install the B2 version again today and see if it happens again.

penguin

---

### Post by penguin7009 on 2015-03-30
Hi all, OK,  I re-installed Ubuntu Mate 15.04 B2 and then installed win2-7 icon package through the theme manager on the desktop.  I logged out and back in and clicked on the network manager icon in the taskbar and had 512 sized icons.

I started Ubuntu Software Manager and started installing Gparted.  The icons on the left of the category list became huge.  It appears that this icon package is no longer compatable with the 15.04 version of Ubuntu, at least the Mate version.

I would like to find out why because Ubuntu Mate is beautiful and really fast.  If anyone has any ideas let me know and I will be glad to help troubleshoot the problem.

Also I had a crash just after installation and had to ctrl-alt-backspace to reload, I think it had something to do with GCC and several other packages but didn't get the logs.  I will keep trying to get to the bottom of this problem.

I could use Ubuntu Mate just as it is and I think it would be fine.  However, what if someone else decides to use a different icon package or the same one?  There must be something causing this problem and it would be good if we could catch it in the Beta stage.

As always, thanks to all who have responded,
penguin

---

### Post by penguin7009 on 2015-03-30
OK, I did the system upgrade through the Update Manager.  I still have the same problem.  When I change the icons to any Icon Package from the original install they all work perfectly.  I don't know anything else to try.

So far I have:

1  Copied all the icons from win2-7 to the "shiney" theme which didn't work.
2  Resized all the icons to 64x64 which made all the icons small.
3  Copied the theme ini from shiney to win2-7 which didn't work.
4  Copied the theme ini from win2-7 to shiney which didn't work.
5  Renamed the win2-7 Icon package to shiney and copied the theme ini to that which didn't work.

And several other attempts which I can't remember.

I'm out of ideas.  If some one has other ideas let me know.

Thanks
penguin

---

### Post by bapoumba on 2015-03-30
I'm not quite sure. i installed the win icon theme and this is what I get for ex. I see no big icon on clicking network-manager but Software Center gives me big pics when I look for gparted. Is that what you mean ?
Otherwise, Caja, Plank, Libreoffice or other apps look ok to me even after I start them up.

---

### Post by penguin7009 on 2015-03-30
> **bapoumba said:**
> I'm not quite sure. i installed the win icon theme and this is what I get for ex. I see no big icon on clicking network-manager but Software Center gives me big pics when I look for gparted. Is that what you mean ?
Otherwise, Caja, Plank, Libreoffice or other apps look ok to me even after I start them up.

Yep, thats what I got too.  All the user account stuff is fine with the exception of right clicking on the net work icon in the taskbar gives large icons.  And Software Manager has huge icons on the side pane and if I click on the progress icon while installing a software package.

I have a habit of pasting the user theme in the root .theme folder and in the /usr/share/theme folder so there is a uniform theme throughout the desktop even in the root mode.  That has not been a problem until Ubuntu Mate 15.  If I do that now I get huge top bar and icons on Synaptic.

I suppose that would not normally be a problem because most folks probably don't do it. Do you think there is any way to access what is causing the problem and stop it?  If so could you let me know?

Thanks for taking the time to look at the problem.

penguin

---

### Post by penguin7009 on 2015-03-30
> **bapoumba said:**
> I'm not quite sure. i installed the win icon theme and this is what I get for ex. I see no big icon on clicking network-manager but Software Center gives me big pics when I look for gparted. Is that what you mean ?
Otherwise, Caja, Plank, Libreoffice or other apps look ok to me even after I start them up.

Yep, thats what I got too.  All the user account stuff is fine with the exception of right clicking on the net work icon in the taskbar gives large icons.  And Software Manager has huge icons on the side pane and if I click on the progress icon while installing a software package.

I have a habit of pasting the user theme in the root .theme folder and in the /usr/share/theme folder so there is a uniform theme throughout the desktop even in the root mode.  That has not been a problem until Ubuntu Mate 15.  If I do that now I get huge top bar and icons on Synaptic.

I suppose that would not normally be a problem because most folks probably don't do it. Do you think there is any way to access what is causing the problem and stop it?  If so could you let me know?

Thanks for taking the time to look at the problem.

penguin

---

### Post by penguin7009 on 2015-03-30
> **bapoumba said:**
> I'm not quite sure. i installed the win icon theme and this is what I get for ex. I see no big icon on clicking network-manager but Software Center gives me big pics when I look for gparted. Is that what you mean ?
Otherwise, Caja, Plank, Libreoffice or other apps look ok to me even after I start them up.

Yep, thats what I got too.  All the user account stuff is fine with the exception of right clicking on the net work icon in the taskbar gives large icons.  And Software Manager has huge icons on the side pane and if I click on the progress icon while installing a software package.

I have a habit of pasting the user theme in the root .theme folder .icon folder and in the /usr/share/theme folder so there is a uniform theme throughout the desktop even in the root mode.  That has not been a problem until Ubuntu Mate 15.  If I do that now I get huge top bar and icons on Synaptic.

I suppose that would not normally be a problem because most folks probably don't do it. Do you think there is any way to access what is causing the problem and stop it?  If so could you let me know?

Thanks for taking the time to look at the problem.

penguin

---

### Post by bapoumba on 2015-03-31
I usually do not run a root desktop (I should say I never do it) and very rarely run graphical applications as root. Installed Synaptic to test. Do not mind the lines in the screenshot, I'm using ubuntu in a VM and these are due to the restricted video driver i'm using, they sometimes appear moving the mouse around (not investigated).

---

### Post by penguin7009 on 2015-03-31
> **bapoumba said:**
> I usually do not run a root desktop (I should say I never do it) and very rarely run graphical applications as root. Installed Synaptic to test. Do not mind the lines in the screenshot, I'm using ubuntu in a VM and these are due to the restricted video driver i'm using, they sometimes appear moving the mouse around (not investigated).

I usually sudo to my root account, do whatever I need to do and then log back in to my user account.  This is what I get when I put the win2-7 icons in the sudo/root account .themes folder:

Would be interesting to know why it does that.  Also when I do that it makes other icons huge if they have anything to do with sudo.

penguin

---

### Post by bapoumba on 2015-03-31
Hmm. As the theme is from 2009, the way things are handled have changed since then. Not sure where to start looking though. 

Just so that I try to reproduce, what do you mean by "I sudo to my root account" ? That may not be very safe.. I hope you do not plain run graphical applications with sudo : [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by penguin7009 on 2015-03-31
> **bapoumba said:**
> Hmm. As the theme is from 2009, the way things are handled have changed since then. Not sure where to start looking though. 

Just so that I try to reproduce, what do you mean by "I sudo to my root account" ? That may not be very safe.. I hope you do not plain run graphical applications with sudo : 

url]https://help.ubuntu.com/community/RootSudo[/url]

Oh I could have phrased that better.  If I want to copy, say a theme to the root account, I goto file system and right click "open as administrator" on the root folder.  Add the file under /root/.theme and then close.  Probably not accepted by the Linux Community at large but has cause no lasting problems on any of my linux systems.  After that if for some reason I need to do something in any sudo account the theme I have chosen is also applied to the root account instead of that ugly Gnome theme.  I don't spend much time in that account because of the danger of changing something, shall we say unfortunate, lol.  I also add the icon theme the same way.

I usually do this if I want to use SystemBack to remaster the installed system.  

After looking at your last post I looked at the file structure of the win2-7 theme and compared that to the file structure of the theme located in the /usr/share/themes directory and you are correct.  In the new theme packages in UbuntuMate 15, there are folders for each size and within those folders are the Actions, Filesystem, etc.

In the Win2-7 icon theme there are folders for Actions, Filesystems etc and within each of those are contained the sizes, just the opposite.  So I guess that theme is to old to be used and I either need to just use the themes that come with UbuntuMate or maybe someone may upgrade the win2-7 theme package to work.

I spent several hours trying to reproduce the structure of the win2-7 theme like that of the new structured theme, but when I got done and tried to apply it, it gave me an error saying that it didn't appear to be a theme!!

So for now I will just enjoy UbuntuMate's goodness and press on with life, lol.

penguin

---

### Post by bapoumba on 2015-03-31
Ah OK, so you run Thunar as root. Not quite recommended indeed, it is easy to click on the wrong file, or delete or whatever and then mess up things in ways that may not be recovered. as long as you are aware and do not recommend it :)

I did not check the win theme against a current theme, that was the right thing to do. I have never made an icon theme, may be this ? [https://developer.gnome.org/icon-theme-spec/](https://developer.gnome.org/icon-theme-spec/)

---

### Post by penguin7009 on 2015-03-31
> **bapoumba said:**
> Ah OK, so you run Thunar as root. Not quite recommended indeed, it is easy to click on the wrong file, or delete or whatever and then mess up things in ways that may not be recovered. as long as you are aware and do not recommend it :)

I did not check the win theme against a current theme, that was the right thing to do. I have never made an icon theme, may be this ? [https://developer.gnome.org/icon-theme-spec/](https://developer.gnome.org/icon-theme-spec/)



Ok, bapoumba, got it sorted out:p  You where right about the file structure of the win2-7 icon package.  Here's what worked.  I remembered I had an icon package call YLMF icon package which was from a Chinese Linux called XP-YLMF.  In that operating system was the YLMF 2.0 Icon package which has the same file structure as the UbuntuMate15 icon packages.  That structure is a group of folders in the root of the icon package.  Each of the root folders is numbered starting with 16 through 48 pixels.  In each of the numbered root folders are the sub folders with the Action, places, filesystem, etc folders.  In those sub folders reside the different icons of each size.

I had copied and saved that icon theme on our server and was able to find it.  I used that icon theme and transferred each of the win2-7 icons by re-sizing the icons using the caja file manager re-sizing function and then pasted that into each size of the YLMF icon package.  That worked really good except for about six icons which I need to resize a little larger.  I just use the original YLMF ini folder to tell the operating system how to display the icons:guitar:

I then copied the /home/icon package to the root/home and /usr/share/icons  and Holy Cow we got icons matching throughout the operating system.

Thanks for your help and patience
penguin

---

### Post by bapoumba on 2015-04-01
Nice :)

Not sure how to do that because I never have, but may be consider contacting the theme authors to offer upgrading the theme package ? If they've gone MIA, release the icon theme on gnome-look (linking back and giving proper credits to the original authors) ?

In any case, you can mark the thread as solved (in Thread Tools), thanks !

---

