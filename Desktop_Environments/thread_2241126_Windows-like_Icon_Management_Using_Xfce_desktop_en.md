---
title: "Windows-like Icon Management Using Xfce desktop environment"
date: 2014-08-24
forum: Desktop Environments
---

### Post by lobonca3 on 2014-08-24
I am new to Linux and am using the XFce desktop environment. One thing I have not found out how to do is assign icons that are meaningful to me to various folders and files. In Windows this is easy. I do not see any way to do this in Linux other than the VERY limited Emblems available.

Can someone enlighten me?

---

### Post by vasa1 on 2014-08-24
That is largely true but IIRC Nautilus offers (or offered) something like what you want. Thunar, the default file manager for XFCE doesn't offer that, AFAIK.

However, if you're going to want all the features you've enjoyed in Windows or on a Mac, that may not be possible.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by bug67 on 2014-08-25
You can change icons system wide by applying a theme.  For Xubuntu, this is done in Settings Manager, Appearance, Icons.  This is assuming there is already a favorable theme to choose from installed.

If, on the other hand, you want to change one particular icon (I'll use the trash can icon in my example here) it gets a bit more complicated.  I'll do my best to explain it:

1.  Navigate to usr/share/icons.  You'll need to access the icons folder as root.
2.  Next, you'll need to navigate to the folder that is *being used for your system icon theme*.  For Xubuntu, the default icon theme is elementary-xfce so, I'm going to use that as the basis from here on.  Inside the elementary-xfce folder are folders labled various things.  The trash can icons will be located in the "places" folder for the empty trash can icon and be labled "user-trash.png."  The full trash can icon is in a different folder labeled "status."  Inside both of those folders are various *sizes*; 12, 16, 22, 24, etc.
3.  What you have to do is change each individual icon in each individual size.  So, if I want to change my empty trash can icon, I have to swap the one I want with the one in the /usr/share/icons/elementary-xfce/places/12, 16, 22, 24, etc.  Then, do the same for the *full* trash can icon in the  /usr/share/icons/elementary-xfce/status/12, 16, 22, 24, etc. folders.  Confused yet?

It is very confusing!  Time consuming as well and one of those few things that Windows and Macs do much, much better.  Really helped me get to know my file structure though.  Hope this helps a little.  Let us know how you get on.

P.S.  _Make sure you back up_ the icons you will be changing in case something goes wrong.  I usually leave the original icon in its respective folder and change its name to something like user-trash-orig.png.

---

### Post by Kirkx on 2014-08-26
You don't actually have to change icons in all "size" folders, just the sizes that you actually use. On the screenshot below the left pane has icons size 16x16 and the right pane has icons size 22x22. You will quickly figure out the most common icon sizes you use and change only those.

[http://i.imgur.com/hSMGn4W.png](http://i.imgur.com/hSMGn4W.png)

I actually never replace any icons in an existing official icon theme. Using "elementary-xfce" as an example, I would copy the whole folder, rename it to "elementary-xfce-2" or something similar, select it in Appearance, and then start playing around replacing the icons.

You can find more tips here:

[http://web.archive.org/web/20100305220150/http://live.gnome.org/GnomeArt/Tutorials/IconThemes](http://web.archive.org/web/20100305220150/http://live.gnome.org/GnomeArt/Tutorials/IconThemes)

---

### Post by vasa1 on 2014-08-26
> **lobonca3 said:**
> I am new to Linux and am using the XFce desktop environment. One thing I have not found out how to do is assign icons that are meaningful to me to various folders and files. In Windows this is easy. I do not see any way to do this in Linux other than the VERY limited Emblems available.

Can someone enlighten me?

Just in case you ever come back to this thread ;)

As I posted earlier, Nautilus may offer you what you want but Nautilus may want to take over managing your desktop as well. The default in XFCE is that Thunar, besides being the file manager, also handles the desktop. So that's something you need to know. 

And check out [Folder Color: Easily Change Folder Icon Colors In Nautilus or Nemo]("http://www.webupd8.org/2014/04/folder-color-easily-change-folder-icon.html")

---

### Post by Rob Sayer on 2014-08-26
Linux isn't Windows.  No amount of making it look like Windows will make it work like Windows.

For example, linux newbies coming from Windows often expect to find their file manager/system based on their hard drive (C:).  This doesn't happen in linux.  All drives are just another folder in linux, though some have special status obviously.

I agree with wanting something other than Thunar.  I'm an Xubuntu user (on my netbook anyway) and I really dislike the Xfce file manager.  It's better than the Lxde one though.  I use dolphin as a file manager, which comes from KDE, and while it installs a rather disturbing amount of KDE dependencies it's never given me any problems in Xfce.  That may be because it's based on a different code library than the other 3 official ubuntu DEs.

None of the file managers in the 4 Ubuntu DE versions will work like Windows.  There is a linux distro that mimics windows 7 but it doesn't work that well ... it's not really possible anyway ... and the tech support is *awful*.

---

