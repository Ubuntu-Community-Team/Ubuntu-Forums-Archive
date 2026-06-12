---
title: "Icons theme issue"
date: 2008-03-21
forum: Desktop Environments
---

### Post by lepban on 2008-03-21
Hey fellow ubuntu...ers

I am trying to make ubuntu pretty, but when i try to apply an icon theme from Gnome-look the iconset doesnt show up on the gnome panel.  Instead of my nice new icons, the panel displays the default-gnome ones.  

Btw. The human theme icons show up on the panel.  But i tried with 2 other downloaded icon themes and neither worked on the gnome-panel

Can anyone hazard a guess?  I'd much appreciate it.

Thanks.

---

### Post by DJ_Peng on 2008-03-21
You may want to go into your Appearances window and use the **Customize...** button to make sure the right icon set is selected on the Icons tab.

---

### Post by lepban on 2008-03-21
Do you know how the icons are read by the system when they are placed into ~/.icons folder?

I think the issue may be that some icons or folders in the iconset are mis-labeled and are being ignored by ubuntu.

---

### Post by BandD on 2008-03-22
They are read by file name.  Gnome looks for certain names in the selected Icon set, and if it doesn't find the right file name, then it uses the default system icons.  If you look through the folders inside /usr/share/icons you'll see how the file names work.  They are sorted by size and inside each size by 'type'.

What Icon sets are you trying to install?  It might help us know if the file names are labeled correctly or not.

---

### Post by dulbirakan on 2008-04-26
I have the same problem, will check out file names...

---

### Post by dulbirakan on 2008-04-26
File names seem to be ok....

I have tried various icon packs btw, one of which is gartoon.

---

### Post by BandD on 2008-04-26
Can you give the exact steps you are taking to install and apply the desired icon theme?

---

### Post by dulbirakan on 2008-04-27
Thanks for your reply

I used gnome art manager at first then I noticed the problem and tested with other icon packs (around 10) but it did not work. 

Then I used gnome appearance properties tool to remove the ones I installed and downloaded the icon packs. Installed them through the gnome appearance properties tool by clicking on install and then selecting customize and icons... It worked for the first couple of the icon themes but then again it stopped working after I installed a few more.

When all failed I untared and copied the contents to /usr/share/icons and chowned to root and set the priv to 755. Still no change...

Some icons are changed, but the folder icons and icons in places tab are unchanged. This only happens for the newly installed icon packs.

I see two Crystal SVG icon themes in the customize menu BTW none of which I installed.

---

### Post by adohall on 2008-04-27
The Glass Icons set is a good example (download from [http://gnome-look.org/content/show.php/Glass+Icons+Theme?content=32146](http://gnome-look.org/content/show.php/Glass+Icons+Theme?content=32146))

The folder icon, among others, doesn't show up in Hardy, whereas it did in Gutsy and Feisty.

The problem may have something to do with the context being set to 'FileSystems' rather than 'Places' in the index.theme file for this (and other icon sets), according to a comment on that page I cited above.

The problem is - if that is the key, how do you find the right index.theme file and edit it? I can't even find a glass-icons file in usr/share/icons (or anywhere else, through Nautilus) despite having installed Glass icons through the Appearances applet.

---

### Post by adohall on 2008-04-27
Here are the steps I went through to install and apply Glass icons:

1. download glass icons set from [http://gnome-look.org/content/show.php/Glass+Icons+Theme?content=32146](http://gnome-look.org/content/show.php/Glass+Icons+Theme?content=32146)
2. open System/Preferences/Appearnce and click 'install' button;
3. direct applet (dialogue box) to the tar.gz file I just downloaded and click 'open';
4. click customise button, go to 'icons' tab and choose 'glass icons' from list;
5. save theme as Human-glass (or whatever)

Some icons are applied, some aren't. The noticeable absentee is the folder icon in Nautilus.

---

### Post by BandD on 2008-04-27
I'm working on Gutsy still.  I probably won't install Hardy for a little bit still (waiting for download speeds to improve and intial bugs to be taken care of).

But I still wonder if the naming structure is to blame. From what I udnerstand (I'm no expert) Gnome looks for a certain file name in the icon directory that you tell it to look at in the apperances dialogue box, if it doesn't find the right file name then it will use whatever you have the default icon theme set to (which is usually stated in your chosen icon theme's index.theme file as 'inherits from:_______' or something like that).  

I don't really think this will work, but to you get the same results if you just drag the tar file into the Apperance dialogue box?


You could also try taking the index.theme file from an icon set that works and putting that in place of the index.theme for the set that doesn't work.  Just make sure to backup the original, just in case.

As a very ugly fix, you could choose a theme that works system wide and go through and replace all the icons that you want.  I did this for myslef under Gutsy taking icons from several different themes to create a custom icon set.

---

### Post by Niniel on 2008-04-28
Ah, no real solution yet, what a shame.
I have the same issue. Upgraded from 7.10 to 8.04, and now the icons are gone (I had the Iris iconset). I too have 2 seemingly identical "Chrystal SVG" themes in my list of icon packages now.
All the default (undeleteable) themes are working.
Something's clearly broken/changed, but what?

---

### Post by Neo¹ on 2008-04-28
Hi,

I think I have similar problem.
It seems that the new Gnome accept only SVG icons for the file system. 
I have tried several themes and always if the folder icons are SVG it works fine. But if You try to use PNG files gnome use the default icons.

Regards,
Neo

---

### Post by Niniel on 2008-04-28
I don't think that's it. I mean, why would just the folder/device icons be affected? Application icons are shown (zip, text...).

---

### Post by dulbirakan on 2008-04-28
I think it is not because of svg thing because gartoon icon pack is svg based. I will try index.theme thing when I get back home...

---

### Post by autocrosser on 2008-04-28
The reason is that the naming of icons has changed in the new Gnome 2.22--Icon makers need to update their sets.

> **Neo¹ said:**
> Hi,

I think I have similar problem.
It seems that the new Gnome accept only SVG icons for the file system. 
I have tried several themes and always if the folder icons are SVG it works fine. But if You try to use PNG files gnome use the default icons.

Regards,
Neo

---

### Post by Neo¹ on 2008-04-28
Hmmmm

My theme
```

-rw-r--r-- 1 radek radek 15040 2007-02-28 01:39 computer.png
lrwxrwxrwx 1 radek radek    14 2008-04-25 14:14 emptytrash.png -> user-trash.png
-rw-r--r-- 1 radek radek 15040 2007-02-28 01:39 gnome-dev-computer.png
-rw-r--r-- 1 radek radek 11550 2007-03-05 02:01 gnome-fs-blockdev.png
-rw-r--r-- 1 radek radek 14755 2007-03-01 09:52 gnome-fs-bookmark-missing.png
-rw-r--r-- 1 radek radek 14781 2007-03-01 03:02 gnome-fs-bookmark.png
-rw-r--r-- 1 radek radek  6765 2005-07-31 17:06 gnome-fs-chardev.png
-rw-r--r-- 1 radek radek 15040 2007-02-28 01:39 gnome-fs-client.png
-rw-r--r-- 1 radek radek 23688 2007-03-05 10:04 gnome-fs-desktop.png
-rw-r--r-- 1 radek radek    51 2007-04-12 11:20 gnome-fs-directory-accept.icon
-rw-r--r-- 1 radek radek 11810 2007-03-01 11:05 gnome-fs-directory-accept.png
-rw-r--r-- 1 radek radek 14914 2007-03-01 03:02 gnome-fs-directory-docs.png
-rw-r--r-- 1 radek radek 10175 2007-03-01 13:34 gnome-fs-directory-hidden.png
-rw-r--r-- 1 radek radek    51 2007-04-12 11:20 gnome-fs-directory.icon
-rw-r--r-- 1 radek radek 12426 2007-03-01 10:58 gnome-fs-directory.png
-rw-r--r-- 1 radek radek    51 2007-04-12 11:20 gnome-fs-directory-visiting.icon
-rw-r--r-- 1 radek radek 11810 2007-03-01 11:06 gnome-fs-directory-visiting.png
-rw-r--r-- 1 radek radek  9796 2007-03-05 02:01 gnome-fs-executable.png
-rw-r--r-- 1 radek radek 14268 2007-03-21 00:27 gnome-fs-fifo.png
-rw-r--r-- 1 radek radek 17346 2007-03-01 11:47 gnome-fs-ftp.png
-rw-r--r-- 1 radek radek 15011 2007-03-01 02:38 gnome-fs-home.png
-rw-r--r-- 1 radek radek 24204 2007-03-01 02:38 gnome-fs-loading-icon.png
-rw-r--r-- 1 radek radek 23216 2007-03-17 03:27 gnome-fs-net-template.png
-rw-r--r-- 1 radek radek 23153 2007-03-01 02:38 gnome-fs-network.png
-rw-r--r-- 1 radek radek 17436 2007-03-04 02:04 gnome-fs-nfs.png
-rw-r--r-- 1 radek radek    44 2005-06-23 11:41 gnome-fs-regular.icon
-rw-r--r-- 1 radek radek  9704 2005-08-01 00:49 gnome-fs-regular.png
-rw-r--r-- 1 radek radek 23724 2007-03-01 02:38 gnome-fs-server.png
-rw-r--r-- 1 radek radek 14640 2007-03-17 03:19 gnome-fs-share.png
-rw-r--r-- 1 radek radek 19062 2007-03-04 02:15 gnome-fs-smb.png
-rw-r--r-- 1 radek radek  8288 2007-04-02 02:16 gnome-fs-socket.png
-rw-r--r-- 1 radek radek 17811 2007-03-04 02:20 gnome-fs-ssh.png
-rw-r--r-- 1 radek radek 16844 2005-10-31 22:51 gnome-fs-trash-empty-accept.png
lrwxrwxrwx 1 radek radek    14 2008-04-25 14:14 gnome-fs-trash-empty.png -> user-trash.png
-rw-r--r-- 1 radek radek 22236 2007-02-28 01:39 gnome-fs-trash-full.png
-rw-r--r-- 1 radek radek 20943 2007-03-01 02:38 gnome-fs-web.png
lrwxrwxrwx 1 radek radek    14 2008-04-25 14:14 gnome-stock-trash.png -> user-trash.png
-rw-r--r-- 1 radek radek 15391 2005-10-31 22:51 trashcan_empty.png
-rw-r--r-- 1 radek radek 16844 2005-10-31 22:51 trashcan_full.png
-rw-r--r-- 1 radek radek 17051 2007-02-28 01:39 user-trash.png
lrwxrwxrwx 1 radek radek    14 2008-04-25 14:14 xfce-trash_empty.png -> user-trash.png

```

Default theme:

```

lrwxrwxrwx 1 root root     23 2008-04-28 10:45 application-x-gnome-saved-search.svg -> folder-saved-search.svg
lrwxrwxrwx 1 root root     16 2008-04-28 10:45 desktop.svg -> user-desktop.svg
lrwxrwxrwx 1 root root     14 2008-04-28 10:45 distributor-logo.svg -> start-here.svg
lrwxrwxrwx 1 root root     14 2008-04-28 10:45 emptytrash.svg -> user-trash.svg
lrwxrwxrwx 1 root root     13 2008-04-28 10:45 folder_home.svg -> user-home.svg
-rw-r--r-- 1 root root     55 2008-04-01 16:46 folder.icon
-rw-r--r-- 1 root root     53 2008-04-01 16:46 folder-remote.icon
-rw-r--r-- 1 root root  25326 2008-04-01 16:46 folder-remote.svg
-rw-r--r-- 1 root root  17456 2008-04-01 16:46 folder-saved-search.svg
-rw-r--r-- 1 root root  15653 2008-04-01 16:46 folder.svg
lrwxrwxrwx 1 root root     16 2008-04-28 10:45 gnome-fs-desktop.svg -> user-desktop.svg
lrwxrwxrwx 1 root root     11 2008-04-28 10:45 gnome-fs-directory.icon -> folder.icon
lrwxrwxrwx 1 root root     10 2008-04-28 10:45 gnome-fs-directory.svg -> folder.svg
lrwxrwxrwx 1 root root     18 2008-04-28 10:45 gnome-fs-ftp.icon -> folder-remote.icon
lrwxrwxrwx 1 root root     17 2008-04-28 10:45 gnome-fs-ftp.svg -> folder-remote.svg
lrwxrwxrwx 1 root root     13 2008-04-28 10:45 gnome-fs-home.svg -> user-home.svg
lrwxrwxrwx 1 root root     21 2008-04-28 10:45 gnome-fs-network.svg -> network-workgroup.svg
lrwxrwxrwx 1 root root     18 2008-04-28 10:45 gnome-fs-nfs.icon -> folder-remote.icon
lrwxrwxrwx 1 root root     17 2008-04-28 10:45 gnome-fs-nfs.svg -> folder-remote.svg
lrwxrwxrwx 1 root root     18 2008-04-28 10:45 gnome-fs-server.svg -> network-server.svg
lrwxrwxrwx 1 root root     18 2008-04-28 10:45 gnome-fs-share.icon -> folder-remote.icon
lrwxrwxrwx 1 root root     17 2008-04-28 10:45 gnome-fs-share.svg -> folder-remote.svg
lrwxrwxrwx 1 root root     18 2008-04-28 10:45 gnome-fs-smb.icon -> folder-remote.icon
lrwxrwxrwx 1 root root     17 2008-04-28 10:45 gnome-fs-smb.svg -> folder-remote.svg
lrwxrwxrwx 1 root root     18 2008-04-28 10:45 gnome-fs-ssh.icon -> folder-remote.icon
lrwxrwxrwx 1 root root     17 2008-04-28 10:45 gnome-fs-ssh.svg -> folder-remote.svg
lrwxrwxrwx 1 root root     14 2008-04-28 10:45 gnome-fs-trash-empty.svg -> user-trash.svg
lrwxrwxrwx 1 root root     14 2008-04-28 10:45 gnome-main-menu.svg -> start-here.svg
lrwxrwxrwx 1 root root     18 2008-04-28 10:45 gnome-mime-x-directory-nfs-server.svg -> network-server.svg
lrwxrwxrwx 1 root root     18 2008-04-28 10:45 gnome-mime-x-directory-smb-server.svg -> network-server.svg
lrwxrwxrwx 1 root root     18 2008-04-28 10:45 gnome-mime-x-directory-smb-share.icon -> folder-remote.icon
lrwxrwxrwx 1 root root     17 2008-04-28 10:45 gnome-mime-x-directory-smb-share.svg -> folder-remote.svg
lrwxrwxrwx 1 root root     21 2008-04-28 10:45 gnome-mime-x-directory-smb-workgroup.svg -> network-workgroup.svg
lrwxrwxrwx 1 root root     14 2008-04-28 10:45 gnome-stock-trash.svg -> user-trash.svg
lrwxrwxrwx 1 root root     11 2008-04-28 10:45 gtk-directory.icon -> folder.icon
lrwxrwxrwx 1 root root     10 2008-04-28 10:45 gtk-directory.svg -> folder.svg
lrwxrwxrwx 1 root root     21 2008-04-28 10:45 gtk-network.svg -> network-workgroup.svg
lrwxrwxrwx 1 root root     18 2008-04-28 10:45 network.icon -> folder-remote.icon
lrwxrwxrwx 1 root root     21 2008-04-28 10:45 network_local.svg -> network-workgroup.svg
-rw-r--r-- 1 root root  26216 2008-04-01 16:46 network-server.svg
lrwxrwxrwx 1 root root     17 2008-04-28 10:45 network.svg -> folder-remote.svg
-rw-r--r-- 1 root root 101327 2008-04-01 16:46 network-workgroup.svg
lrwxrwxrwx 1 root root     14 2008-04-28 10:45 novell-button.svg -> start-here.svg
lrwxrwxrwx 1 root root     18 2008-04-28 10:45 redhat-network-server.svg -> network-server.svg
lrwxrwxrwx 1 root root     18 2008-04-28 10:45 server.svg -> network-server.svg
-rw-r--r-- 1 root root  24816 2008-04-01 16:46 start-here.svg
lrwxrwxrwx 1 root root     11 2008-04-28 10:45 stock_folder.icon -> folder.icon
lrwxrwxrwx 1 root root     10 2008-04-28 10:45 stock_folder.svg -> folder.svg
lrwxrwxrwx 1 root root     14 2008-04-28 10:45 trashcan_empty.svg -> user-trash.svg
-rw-r--r-- 1 root root  29930 2008-04-01 16:46 user-desktop.svg
-rw-r--r-- 1 root root  16099 2008-04-01 16:46 user-home.svg
-rw-r--r-- 1 root root  12366 2008-04-01 16:46 user-trash.svg
lrwxrwxrwx 1 root root     14 2008-04-28 10:45 xfce-trash_empty.svg -> user-trash.svg

```

The only difference I see is the filetype (png/svg)

> **dulbirakan said:**
> I think it is not because of svg thing because gartoon icon pack is svg based. I will try index.theme thing when I get back home...

gartoon works for me fine :(

Regards,
Neo

---

### Post by uantuzri on 2008-04-28
I have the same issue here. For some reason the only theme that is displayed correctly is 'Dropline neu' [http://art.gnome.org/themes/icon/1100]("http://art.gnome.org/themes/icon/1100").

It has both png's and svg's...

---

### Post by dulbirakan on 2008-04-28
> **Neo¹ said:**
> gartoon works for me fine :(

Regards,
Neo

Lucky you :)

And I noticed Dropline Neu is working fine for me as well. Curious...

---

### Post by Niniel on 2008-04-28
> **autocrosser said:**
> The reason is that the naming of icons has changed in the new Gnome 2.22--Icon makers need to update their sets.
Yeah, great, except that some very nice icon sets are no longer being developed. 
If they change things like this they need to throw in a guide on how to update existing sets... or better yet, a tool to help doing that. :(

---

### Post by stansford on 2008-04-28
> **Niniel said:**
> Yeah, great, except that some very nice icon sets are no longer being developed. 
If they change things like this they need to throw in a guide on how to update existing sets... or better yet, a tool to help doing that. :(

Guys,
I've fixed this issue - at least for me.
I'll share it and see if it does the same for you:

I've done a clean Hardy install and then installed my two fav icon sets "dropline-etiquette" and CrystalforGnome-Kids.
Neither of these display the full set of icons anymore (they did in Gutsy). Some show the default Gnome grey icon set which is very annoying and so naff.

The icons I really wanted to change were the folder icons shown in Nautilus under tree view, but I guess once you get the principle right, and find out what the icons are called it will probably work for whatever icons you want to change. OK here's what I did:

1. Compare the folder structure of standard icon sets that come with Hardy as installed in /usr/share/icons/ with your favourite sets installed probably in /home/.icons/<fav icons set name>. I looked at the default set called "Gnome" and another set called "Crux" both of which work but have different structures.

You need to do this to find out what the differences are between the folder structure in the sets that work and yours that don't work.

I discovered that in the "dropline-etiquette" (art.gnome.org) set, the difference was that the default Gnome set under the folder "scalable" there was a "places" folder. My set didn't have this places folder, instead it had a "filesystems" folder.

So the first thing I did was rename the folder called "filesystems" to "places" under /home/angus/.icons/dlg-etiquette/scalable.

2. The next thing to do is edit the "index.theme" file found in /home/angus/.icons/dlg-etiquette folder and using find and replace change all occurrences of "filesystems" to "places".

3. The last thing to do is to go back to the /home/angus/.icons/dlg-etiquette/scalable/places folder and make sure there is an icon called "folder.svg" or "folder.png" depending on which type of icons your icon set uses. 

For me this last point was key. Obviously if you can find the name of the icon you want to replace then you can make sure your set has one with the right name in the right place. For me I needed an icon called "folder.svg" in the places folder.

Then reload the icon set and bingo - the old grey default folder icons in Nautilus were gone.

Now there is one other scenario worth covering and that is what to do if there is no "scalable" folder in your icon set.

My "kids" icon set was like this and that is where the "Crux" defualt theme I mentioned earlier comes in. It too has no scalable folder so if your set is like that and just has a number of folders with the different sizes of icons on eg 16x16, 32x32 etc then below each of these folders you should still find your hierarchy of folders with names like "places", "apps" etc. Again all I had to do was follow the steps above and replace the folders called "filesystems" with ones called "places". 

Unfortunately, I didn't know which sized icons were being used, so I just changed them all. It seems sense to do this, but it's more work though!

Then reload the set again and you should see the icons you want.

So there you are! Hope this works for you like it worked for me.

---

### Post by adohall on 2008-04-28
Here's an alternate solution. A couple of very helpful Ubuntu users provided this over at gnome-look.org:

1. Open Nautilus with root permission (terminal - sudo nautilus)
2. Extract the theme tar.gz file (e.g. Glass Icons) into /usr/share/icons folder.
3. Go to /usr/share/icons/glass-icons/scalable/filesystems/ and right click the gnome-fs-directory.svg file and select the Make Link option. This will create a link and you rename that link folder.svg.
4. Do the same with these other files:
- gnome-fs-trash-full.svg -> user-trash-full.svg
- gnome-fs-trash-empty.svg -> user-trash.svg
- gnome-fs-home.svg -> user-home.svg
- gnome-fs-client.svg -> computer.svg
- gnome-fs-web.svg -> applications-internet.svg
- gnome-fs-desktop.svg -> user-desktop.svg
- gnome-fs-server.svg -> network-workgroup.svg
- devices/gnome-dev-harddisk.svg -> drive-harddisk.svg
- devices/gnome-dev-dvdrw.svg -> drive-optical.svg
- devices/gnome-dev-removable.svg -> drive-removable-media.svg
5. Customize a theme by choosing Glass Icons;
6. Reboot (or change icon theme and then change back)

---

### Post by BandD on 2008-04-28
adohall,

Did they give you a reason why the naming sturcure suddenly changed so?  This seems more like a bug or an oversite to me.  It doesn't make sense to change the naming structure of the icon themes in gnome in the middle of version 2.xx.  I could see, MAYBE, doing this when they get to 3.xx, but it really doesn't make any sense to me.  I wonder how wide-spread this problem is.  I guess I'll see what happens in another week or two when I install Hardy...

---

### Post by stansford on 2008-04-29
> **adohall said:**
> Here's an alternate solution. A couple of very helpful Ubuntu users provided this over at gnome-look.org:

1. Open Nautilus with root permission (terminal - sudo nautilus)
2. Extract the theme tar.gz file (e.g. Glass Icons) into /usr/share/icons folder.
3. Go to /usr/share/icons/glass-icons/scalable/filesystems/ and right click the gnome-fs-directory.svg file and select the Make Link option. This will create a link and you rename that link folder.svg.
4. Do the same with these other files:
- gnome-fs-trash-full.svg -> user-trash-full.svg
- gnome-fs-trash-empty.svg -> user-trash.svg
- gnome-fs-home.svg -> user-home.svg
- gnome-fs-client.svg -> computer.svg
- gnome-fs-web.svg -> applications-internet.svg
- gnome-fs-desktop.svg -> user-desktop.svg
- gnome-fs-server.svg -> network-workgroup.svg
- devices/gnome-dev-harddisk.svg -> drive-harddisk.svg
- devices/gnome-dev-dvdrw.svg -> drive-optical.svg
- devices/gnome-dev-removable.svg -> drive-removable-media.svg
5. Customize a theme by choosing Glass Icons;
6. Reboot (or change icon theme and then change back)


adohall - this is only really an alternative if you ALSO rename the "filesystems" folder to "places" under the "scalable" folder and edit the index.theme file changing each occurrences of the word "filesystems" to "places". 

The icon naming spec and theme specs are here if anyones interested: 
[http://standards.freedesktop.org/icon-naming-spec/icon-naming-spec-latest.html](http://standards.freedesktop.org/icon-naming-spec/icon-naming-spec-latest.html)
[http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html](http://standards.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html)

Hope that helps

---

### Post by adohall on 2008-04-29
It's worked for me without renaming the folder or tinkering with index.theme.

---

### Post by stansford on 2008-04-30
> **adohall said:**
> It's worked for me without renaming the folder or tinkering with index.theme.

fair enough then...although I'm just thinking of the future and what will happen when you reinstall/upgrade next time. 

With the link method you'll presumably have to create the links each time from the original icon set that is still "wrong".

Alternatively, if you amend the folders, index.theme etc and then create a new tar.bz2 archive, you could just reinstall the amended set after the upgrade. It might be more work now, but it would produces a permanent fix.

.or can you store links in a tar.bz2 file??

---

### Post by Niniel on 2008-05-01
All right, renaming the icons worked, mostly anyway. Some still don't work, like the open folder icon. I'm also not sure how to name CD-ROM vs. DVD. But anyway, it's a lot better. Thank you.

---

### Post by BandD on 2008-05-05
If you are having trouble finding the right name to call an icon, I think I've found the motherload.  

Navitage to /usr/share/icons/gnome/scalable.  That's basically where all icons known to gnome are stored.  

I had to fiddle a bit with a custom set I put together in Gutsy, but everything is working perfectly for me...well sort of.  Firefox doens't use the right home icon and nautilus in 'browse for file' mode doens't use all the right icons either--though in just plain Nautilus mode everything is perfect!

---

### Post by rogerdodd on 2008-05-21
I found a slightly easier solution that doesn't require editing the index.theme file. Simply create a soft link as follows when you are in the scalable directory:

```
 ln -s filesystems/ places 
```

Then you just have to change the names of the required icons or create links to the old ones with the new correct names

---

### Post by granny6989 on 2008-05-29
This is something that I have been trying to figure out since the change to Hardy. Thanks for all the help so far... I have found that it doesn't matter so much about the folder and theme.index setup, but that the icon names must be exactly what the gnome environment is looking for. I have been going through and trying to get all my icons squared away, since (as mentioned above), I use gartoon also. Maybe at some point when I have them all working I will repackage and share what I've gotten straightened out. I have been updating and adding to the collection as well. 

As far as the post relating to gartoon and the firefox icon, I got that to show up on my desktop by opening and resaving the icon as a .png (maybe not neccesary?), and then moving (or copying) the file to the /usr/share/pixmaps directory. Then right click on the  firefox logo on the upper task bar, choose properties, and click on the icon to change it. The updated icon should be there. 
    Hope this helps someone, I found this to be extremely frustrating, after having a not so pleasurable experience upgrading last time, and wanting my desktop back......... The problem is posted back a page or so, and has to do with gnome changing all the icon names it seems.



If ti ain't broke, don't fix it...
S*

---

