---
title: "&quot;Open folder&quot; opens terminal instead of nautilus"
date: 2011-04-29
forum: Desktop Environments
---

### Post by libb on 2011-04-29
Hi,
I just upgraded from Maverick 10.10 to 11.04 64-bit and I have the following problem: every program that provides an "open file or folder" function such as synapse -> open folder, firefox downloads open folder, deluge open, instead of opening nautilus in the desired folder(default behavior of 10.10), it just opens a gnome-terminal.

Does anyone have an idea how to solve this ?

---

### Post by Krytarik on 2011-04-29
It seems like it's related to the common inadvertently setting of another app then Nautilus as the default application to handle folders.

Open the file "~/.local/share/applications/mimeapps.list" and lookup the entry for "inode/directory", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```Here is a good explanation of what may have caused it and how to prevent that in future:
[http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

Greetings.

---

### Post by mc4man on 2011-04-29
> It seems like it's related to the common inadvertently setting of another app then Nautilus as the default application to handle folders.
If it was that then for future use - the option (remember ...), when used on folders, has  finally been  removed in natty and just recently applied in updates for lucid and maverick also

It will remain an option for files and for some reason has been left enabled by default (though not as big a deal as it was for folders

---

### Post by Krytarik on 2011-04-29
> **mc4man said:**
> If it was that then for future use - the option (remember ...), when used on folders, has  finally been  removed in natty and just recently applied in updates for lucid and maverick also
At least for Lucid, which I am running, I cannot confirm that, and it's fully updated, I just yet checked it. But good to know that at least in Natty it is 'fixed', I assume you are running those and checked it.

---

### Post by libb on 2011-04-29
Thank you for your answers but unfortunately I didn't manage to solve it yet.
My ~/.local/share/applications/mimeapps.list looks like this:

```

[Added Associations]
x-content/blank-cd=brasero-copy-medium.desktop;nautilus-cd-burner.desktop;brasero-nautilus.desktop;
application/x-cd-image=nautilus-cd-burner-open-iso.desktop;brasero.desktop;mount-archive.desktop;file-roller.desktop;vlc.desktop;
application/x-wine-extension-inf=userapp-gedit-72137U.desktop;
video/x-flv=totem.desktop;avidemux-qt.desktop;avidemux-gtk.desktop;gnome-mplayer.desktop;vlc.desktop;
text/x-sql=gedit.desktop;wine-extension-txt.desktop;openoffice.org-writer.desktop;gvim.desktop;
application/x-php=gedit.desktop;wine-extension-txt.desktop;openoffice.org-writer.desktop;gvim.desktop;
video/x-matroska=totem.desktop;gnome-mplayer.desktop;vlc.desktop;userapp-xine-3BJKTV.desktop;
application/x-linguist=vlc.desktop;
x-scheme-handler/file=exo-file-manager.desktop;
x-scheme-handler/trash=exo-file-manager.desktop;
inode/directory=nautilus-browser.desktop;

[Default Applications]
video/x-flv=vlc.desktop
inode/directory=nautilus-folder-handler.desktop
x-directory/normal=nautilus-folder-handler.desktop
video/3gpp=totem.desktop
video/dv=totem.desktop
video/fli=totem.desktop
video/flv=totem.desktop
video/mp4=totem.desktop
video/mp4v-es=totem.desktop
video/mpeg=totem.desktop
video/msvideo=totem.desktop
video/ogg=totem.desktop
video/quicktime=totem.desktop
video/vivo=totem.desktop
video/vnd.divx=totem.desktop
video/vnd.rn-realvideo=totem.desktop
video/vnd.vivo=totem.desktop
video/x-anim=totem.desktop
video/x-avi=totem.desktop
video/x-flc=totem.desktop
video/x-fli=totem.desktop

```

There exists a file /usr/share/applications/nautilus-folder-handler.desktop . However now when I try to open a folder from within a program, a terminal opens and when I close it I get the message "**Failed to execute default File Manager. Input/output error**". Is there any log file where I can see more information about the error ?

Thank you

---

### Post by Krytarik on 2011-04-29
Try removing the line I marked:
```

[Added Associations]
x-content/blank-cd=brasero-copy-medium.desktop;nautilus-cd-burner.desktop;brasero-nautilus.desktop;
application/x-cd-image=nautilus-cd-burner-open-iso.desktop;brasero.desktop;mount-archive.desktop;file-roller.desktop;vlc.desktop;
application/x-wine-extension-inf=userapp-gedit-72137U.desktop;
video/x-flv=totem.desktop;avidemux-qt.desktop;avidemux-gtk.desktop;gnome-mplayer.desktop;vlc.desktop;
text/x-sql=gedit.desktop;wine-extension-txt.desktop;openoffice.org-writer.desktop;gvim.desktop;
application/x-php=gedit.desktop;wine-extension-txt.desktop;openoffice.org-writer.desktop;gvim.desktop;
video/x-matroska=totem.desktop;gnome-mplayer.desktop;vlc.desktop;userapp-xine-3BJKTV.desktop;
application/x-linguist=vlc.desktop;
x-scheme-handler/file=exo-file-manager.desktop;
x-scheme-handler/trash=exo-file-manager.desktop;[COLOR=Red][B]
inode/directory=nautilus-browser.desktop;
[/B][/COLOR] 
[Default Applications]
video/x-flv=vlc.desktop
inode/directory=nautilus-folder-handler.desktop
x-directory/normal=nautilus-folder-handler.desktop
video/3gpp=totem.desktop
video/dv=totem.desktop
video/fli=totem.desktop
video/flv=totem.desktop
video/mp4=totem.desktop
video/mp4v-es=totem.desktop
video/mpeg=totem.desktop
video/msvideo=totem.desktop
video/ogg=totem.desktop
video/quicktime=totem.desktop
video/vivo=totem.desktop
video/vnd.divx=totem.desktop
video/vnd.rn-realvideo=totem.desktop
video/vnd.vivo=totem.desktop
video/x-anim=totem.desktop
video/x-avi=totem.desktop
video/x-flc=totem.desktop
video/x-fli=totem.desktop

```Although that doesn't really explain why the terminal is getting launched.

You may also try removing "~/.local/share/mime/mime.cache", make a backup before.

As for a log, I don't think so, you may check "~/.xsession-errors" though.

---

### Post by mc4man on 2011-04-29
> **libb said:**
> Thank you for your answers but unfortunately I didn't manage to solve it yet.

Not really sure - I'd think it would be 
x-directory/normal=
Maybe try deleting that line ( or move the complete file to a backup, log out/in and start creating a new mimeapps.list 
(there is also a mimeinfo.cache file

_On a fresh install there is nothing in ./local/share/applications, you could just start fresh and see_ (remove to backup or delete all the files in the folder
> 
At least for Lucid, which I am running, I cannot confirm that,...

Got an email the other day, maybe not in repos yet?
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194)

---

### Post by Krytarik on 2011-04-29
> **mc4man said:**
> 
there is also a mimeinfo.cache file
Yeah, now I even found it! It seems like I somehow overlooked it the last time I searched for it.
> **mc4man said:**
> 
Got an email the other day, maybe not in repos yet?
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/662194)
Ah, it's gone now! After checking the version numbers, and the release date, I noticed that I didn't reboot/relogin or restart Nautilus since then, I got the update at the 28th. Thanks!

---

