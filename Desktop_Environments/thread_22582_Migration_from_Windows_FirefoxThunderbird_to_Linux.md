---
title: "Migration from Windows Firefox/Thunderbird to Linux Firefox/Thunderbird"
date: 2005-03-28
forum: Desktop Environments
---

### Post by jrc on 2005-03-28
How do I export my Firefox User Profile and bookmarks from my Windows version of Firefox to my Linux (Ubuntu) version of Firefox?  Also, is there some way of copying my Thunderbird address book and email messages from the Windows version to the Linux version?

I have one computer with two hard drives:  the original hard drive is running Windows ME and my brand new "slave" drive is now running Warty Warthog as of yesterday.  The installation went smoothly largely because of the HUGE amount of documentation available via these forums.  I still have a few issues to resolve, though, so I thought I'd start out with something that I hope is easy to resolve and then move on to the dreaded sound card issue.

---

### Post by PMO6022 on 2005-03-28
I can help you out with your firefox profile, I don't use Thunderbird, so I can't help you there.

First, see [http://kb.mozillazine.org/Firefox_:_Tips_:_Profile#What_is_in_my_profile.3F](http://kb.mozillazine.org/Firefox_:_Tips_:_Profile#What_is_in_my_profile.3F) to determine what you want to save out of your profile.

In windows, the profile is located in  
```
C:\Documents and Settings\<Windows login/user name>\Application Data\Mozilla\Firefox\Profiles\<Profile name>\%APPDATA%\Mozilla\Firefox\Profiles\<Profile name>\
```
Application data is a hidden folder so make sure to enable viewing of hidden folders to find it.  

Just save whatever files out of your profile you want - I typically save bookmarks.html, cookies.txt, hostperm.1, key3.db, prefs.js, and signons.txt.

Then, on Linux, copy the files into your profile, located at:
```
 ~/.mozilla/firefox/<Profile name>/
```
Note: profile name is a random string of numbers and letters.

This will not copy over your themes/extensions.  I've found it better to install those manually, especially when transferring between Windows and Linux.

Hope this helps!

---

### Post by mattack on 2005-03-28
[QUOTE=jrc]How do I export my Firefox User Profile and bookmarks from my Windows version of Firefox to my Linux (Ubuntu) version of Firefox?  Also, is there some way of copying my Thunderbird address book and email messages from the Windows version to the Linux version?

I have one computer with two hard drives:  the original hard drive is running Windows ME and my brand new "slave" drive is now running Warty Warthog as of yesterday.  The installation went smoothly largely because of the HUGE amount of documentation available via these forums.  I still have a few issues to resolve, though, so I thought I'd start out with something that I hope is easy to resolve and then move on to the dreaded sound card issue.[/QUOTE]
 I found that uninstalling extensions and themes in Thunderbird before transferring your profile helps a lot. I ran into problems with extensions (I only use the default theme) not transferring correctly. I also remember having to edit a pathname on the linux side once I copied the profile over. I don't remember what file it was in though, sorry....
my head is a little clouded right now.

---

### Post by Davepet on 2005-03-29
Both your FF  bookmarks & TB addressbook can be first exported (in windoze) & then imported (In Ubuntu). It's been a while, so I'm not gonna try to post a how to, just dig in the menus a bit & the export /import fnctions will turn up.

I don't save email's so can't help with that. I also prefer to reset settings & extensions manually...the windoze & Linux versions of FF & TB don't seem to be that identical to me.

Dave

---

### Post by jrc on 2005-04-03
Thanks to all of you for your advice.  I was able to import my bookmarks to Linux Firefox from my Windows Firefox once I figured out how to mount my Windows disk drive (with the help of these forums, of course).  Executing commands in a shell is a strange new world for me, so I'm taking things slowly.

---

### Post by PMO6022 on 2005-04-03
Great!  Glad you were able to get all your data moved over.  Don't worry...you'll soon be so used to the shell that you'll wonder how you ever got by without it!

---

