---
title: "desktop is not displaying files"
date: 2011-07-04
forum: Desktop Environments
---

### Post by wolfv6 on 2011-07-04
My desktop is not displaying files that I put on the desktop days ago.  I checked all four workspaces.
All the files are still accessible from Nautilus > Desktop.
When I drag a file icon (from Nautilus to the empty desktop) and release, the icon does not drop on the desktop, the icon quickly moves back to the folder where it came from.
The top and bottom panels of the desktop still operate normally.
I am running Ubuntu 11.04 64-bit with classic-Ubuntu desktop.
I also noticed that Startup Applications is missing "chrome" that I added this morning.
I am the only user on this system.  The system is a duel boot Ubuntu - win7.  The Ubuntu partition is formated ext4 and there is a separate NTFS-formated partition named &#8220;storage&#8221; for folders that are accessible from both Ubuntu and win7.  That should not be an issue because the desktop folder is on the Ubuntu partition, /home/[user]/Desktop.  I have not booted win7 in the last few days.

The desktop first appeared empty after I did two things:
1) installed CryptKeeper from Ubuntu Software Center
2) Enable Automatic Login

After I clicked Applications > System > CryptKeeper, the desktop did not respond to mouse clicks.  I did not find any CryptKeeper instructions.  I don't know how to use CryptKeeper.
 
The login screen  still asked for credentials after I rebooted.

So I uninstalled CryptKeeper, disable Automatic Login, and rebooted. But the desktop is still not displaying the files.

Could CryptKeeper have changed something in my profile?
Does Ubuntu have a log file to see exactly what I did?
What else can I try to restore my desktop and enable Automatic Login?
I appreciate your suggestions.

Thanks for reading such a long post.

---

### Post by Krytarik on 2011-07-04
First, make sure the key "/apps/nautilus/preferences/show_desktop" is enabled in "gconf-editor".

If that doesn't help, check the file "~/.config/user-dirs.dirs", and make sure it has the following entry in it:
```
XDG_DESKTOP_DIR="$HOME/Desktop"
```
If you need to modify it, relogin thereafter.

Greetings.

---

### Post by wolfv6 on 2011-07-05
Thanks for your suggestions Krytarik.  But I didn't find anything unusual.

> **Krytarik said:**
> First, make sure the key "/apps/nautilus/preferences/show_desktop" is enabled in "gconf-editor".(press Alt+F2 and type gconf-editor "gconf-editor")
The gconf-editor shows "/apps/nautilus/preferences/show_desktop" checked (Nautilus will draw the icons on the desktop). 


> **Krytarik said:**
> check the file "~/.config/user-dirs.dirs", and make sure it has the following entry in it:
```
XDG_DESKTOP_DIR="$HOME/Desktop"
```XDG_DESKTOP_DIR="$HOME/Desktop" is on the first line.

---

### Post by Krytarik on 2011-07-05
Please check if your home directory is (still) encrypted. Therefore, log in as another user, gain root rights and see if you can access the files/dirs in your home directory. If you 'enabled' the root account, you can log in with those as well.

Also, try restarting Nautilus after being logged in an making sure that the Desktop directory is accessible:
```
killall nautilus
```
And, it might be that we can't fix it all right now, since there are a number of issues regarding Nautilus' handling of the desktop in Natty 11.04.

---

### Post by wolfv6 on 2011-07-05
> **Krytarik said:**
> Please check if your home directory is (still) encrypted. Therefore, log in as another user, gain root rights and see if you can access the files/dirs in your home directory. If you 'enabled' the root account, you can log in with those as well.I created admin account "test1" and added him to sudoers.  Then logged in as test1.   Nautilus displayed my desktop files.  But Nautilus could not open my Documents folder, it had an "x" on the folder icon. Similar results from terminal; I could view the desktop folder, but Documents folder was "permission denied".

> **Krytarik said:**
> Also, try restarting Nautilus after being logged in an making sure that the Desktop directory is accessible:
```
killall nautilus
```I did this as "wolf" and "test1" and got the same results.

Krytarik, I am not sure what all this means.  I look forward to your comments.

---

### Post by Krytarik on 2011-07-05
It seems like the permission of the files/dirs in your home directory have been somehow screw up. Make sure that both of the concerning directories have 755 set as permissions:
```
sudo chmod 755 /home/wolf/Desktop
sudo chmod 755 /home/wolf/Documents
```
And please check if there are any other files/dirs with unusual permissions, at least at the toplevel of your home directory.

If that still doesn't help, try deleting the content of the directory "~/.local/share/gvfs-metadata", but better make a backup before.

And, after logging in as "wolf", check the log file "~/.xsession-errors" for related error messages.

Also, please check if Nautilus' handling of the desktop works with the new user.

---

### Post by wolfv6 on 2011-07-05
Thanks for your quick response.
> **Krytarik said:**
> Make sure that both of the concerning directories have 755 set as permissions:
```
sudo chmod 755 /home/wolf/Desktop
sudo chmod 755 /home/wolf/Documents
```
And please check if there are any other files/dirs with unusual permissions, at least at the toplevel of your home directory.The Documents folder did not have the expected permissions, now it does.

> **Krytarik said:**
> After logging in as "wolf", check the log file "~/.xsession-errors" for related error messages.
The end of my ~/.xsession-errors file has:

```
(nautilus:4623): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OB
JECT (value)' failed
** (process:2983): DEBUG: desktop-launch-listener.vala:118: ran with uri: file:///media/storage/Documents

(nautilus:4623): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OB
JECT (value)' failed

(nautilus:4623): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OB
JECT (value)' failed
```

> **Krytarik said:**
> Also, please check if Nautilus' handling of the desktop works with the new user.This time admin test1 could get into my Documents folder, but the folder appears empty.  The next paragraph explains why.

storage is a separate NTFS-formated partition I created for folders that are accessible from both Ubuntu and win7.  Days ago I added a line to fstab to mount the storage partition to /media.  And changed  /home/wolf/.config/user-dirs.dirs:
```
XDG_DESKTOP_DIR="$HOME/Desktop" 
XDG_DOWNLOAD_DIR="/media/storage/Downloads" 
XDG_TEMPLATES_DIR="$HOME/Templates" 
XDG_PUBLICSHARE_DIR="/media/storage/Public" 
XDG_DOCUMENTS_DIR="/media/storage/Documents" 
XDG_MUSIC_DIR="/media/storage/Music" 
XDG_PICTURES_DIR="/media/storage/Pictures" 
XDG_VIDEOS_DIR="/media/storage/Videos"
```I suspect that test1 is not processing /home/wolf/.config/user-dirs.dirs and as a result, Nautilus is looking at the empty directory "/home/wolf/Documents" instead of the directory "/media/storage/Documents" that has files in it.

What else can I check?

---

### Post by Krytarik on 2011-07-05
First, with
> **Krytarik said:**
> 
Also, please check if Nautilus' handling of the desktop works with the new user.
I mean, if you are logged in as "test1", does the desktop show the content of its Desktop directory, "/home/test1/Desktop"!?

Second, the "~/.config/user-dirs.dirs" of your own user, "wolf", doesn't matter at all for any other users, neither does it matter if you open your directory "~/Documents" directly. With changing the paths in those file, you only affect the bindings of your personal directories, and as a result your Bookmarks.

Try re-setting those paths with Ubuntu Tweak, I had positive experience with it in that aspect. Maybe it will fix the Desktop binding this way.

---

### Post by wolfv6 on 2011-07-06
> **Krytarik said:**
> if you are logged in as "test1", does the desktop show the content of its Desktop directory, "/home/test1/Desktop"!?Yes, test1 always could see the content of its own Desktop directory.

> **Krytarik said:**
> Try re-setting those paths with Ubuntu Tweak, I had positive experience with it in that aspect. Maybe it will fix the Desktop binding this way.What "those paths"?

Ubuntu Tweak looks nice, but I don't see how to fix Desktop bindings.

Thanks for your help.  Maybe this will make more sense to me after I get some sleep.  I will be back tomorrow.

---

