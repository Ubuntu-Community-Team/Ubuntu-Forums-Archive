---
title: "KDE file associations on a Unity desktop"
date: 2017-04-22
forum: Desktop Environments
---

### Post by Deanobats on 2017-04-22
Hi all,
I have a perplexing problem. I'm using Tellico (A KDE collections manager) to manage a load of video files from wildlife cams. I'm using it in folder mode to keep track of files, file sizes and add notes and add to the database as new files are added to a set of directories. So far so good. When Tellico shows me the link to the file, I could click on it an it would launch the video with the default 'Video' app. (Totem Movie player). This is the default behaviour as specified in the System Settings>Default Applications dialogue. However, I recently installed MediaInfo to get extra information about the video resolution and so on, and now when I click on the file link within Tellico it launches MediaInfo and not a video player, even though this works fine outside of Tellico for all video files.

I guess my question is that when you install a KDE application under Ubuntu 16.04, is there a separate KDE mimetype settings file that I can find and manage that causes this behaviour? I'd like to alter it back so that when I click on the file link it launches a video player and not mediainfo. I can find it in any Tellico configurations settings.

---

### Post by deadflowr on 2017-04-22
Right click one of the files >> go to properties.
go to open with and find Videos, highlight and click on the set as default.
Close the properties dialog and click one of the files.
See what happens next.

---

### Post by Deanobats on 2017-04-22
Thanks for that. Sadly right clicking on a file link within Tellico doesn't do anything as no dialogue is opened. Right clicking on any video file in any Unity file manager does the usual expected things. I'm suspecting that there is some KDE mimetypes file I can't find. .mkv files open in Xine for example, all other videos within mediainfo. Outside of Tellico all the file associations are fine.

---

### Post by deadflowr on 2017-04-22
Check what settings are listed in the tellicorc file at
~/.kde/share/config/tellicorc

---

### Post by Deanobats on 2017-04-22
Aha, didn't know that file existed, I'll have a look....

---

### Post by Deanobats on 2017-04-24
Well there is nothing to mention video files in that file, there is an

[EditImage]
editor=Gwenview

Entry for image files which seems to work properly (i.e. I click on an image file and it opesn in Gwenview.)

There is also a tellicorc file at:
/usr/share/KDE4/config but all that has in it is;

[KDE Action Restrictions]
shell_access=false
run_desktop_files=false;

There is a line in /usr/share/applications/mimeinfo.cache that reads:

video/x-matroska=ghb.desktop;mediainfo-gui.desktop;vlc.desktop;xine.desktop;org.gnome.Totem.desktop;

Now if I click on an mkv video file, under Files, Thunar etc, it will open the file in Totem Video Player, but Tellico opens it in Xine, which is odd as handbrake is the first one in that list.

Similarly, there is a line:

video/x-ms-wmv=mediainfo-gui.desktop;vlc.desktop;xine.desktop;org.gnome.Totem.desktop;

Again, if I click a file under Files or Thunar the file opens in Totem Video player, but within Tellico it opens in Mediainfo.

I can't find any relevant entries in any mimeapps file other than the default settings for example 

video/x-msvideo=org.gnome.Totem.desktop;

I wonder if what is happening is that normally the mimeapps file overrules the mimeinfo.cache settings (whatever they are!) but from Tellico (or other KDE application?) then they don't. Still doesn't explain the strange preference order within the mimeonfo.cache file though.

---

### Post by Deanobats on 2017-04-24
I found this;
> 
The mimeinfo.cache is basically a raw reverse cache for the .desktop  information. There is no way to define priorities in it. To be able to  specify default applications, a mimeapps.list file (previously named  defaults.list up to debian 5) must be created. It can be system-wide (in  /usr/share/applications or a subdirectory) or user-specific (in  $HOME/.local/share/applications).  A heuristic is used by glib (FIXME:  what about KDE?) to use the appropriate mimeapps.list file according to  the user environment (Gnome evince vs. KDE Okular for PDF files for  instance). The mimeapps.list file follows the same syntax as  mimeinfo.cache ...


Source: [https://wiki.debian.org/MIME](https://wiki.debian.org/MIME)

---

### Post by Deanobats on 2017-04-24
Sorted, I hope!

I ran "kcmshell4 filetypes" from a terminal which opened up a KDE Control Module GUI. I changed the preference order for the applications associated with all the video file types listed and that did it. Tellico now opens the right files in the right applications. I just hope it hasn't spoiled anything else!

I guess there must be some config file somewhere that records and manages all this but I have no idea where it it.

---

### Post by robby.stephenson on 2017-04-26
> **Deanobats said:**
> I guess there must be some config file somewhere that records and manages all this but I have no idea where it it.
As the previous post noted, once upon a time, user-specific ordering was in *~/.local/share/applications/defaults.list*. It might be *mimeapps.list* in the same folder, though I'm not sure where the default was coming from. As you experienced, Tellico uses whatever app has been set through the KDE configuration.

---

