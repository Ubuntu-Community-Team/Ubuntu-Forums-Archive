---
title: "making nautilus --no-desktop the default for fluxbox"
date: 2008-07-06
forum: Desktop Environments
---

### Post by mwcrowley on 2008-07-06
I have searched, and googled, and failed.  

Default behaviour for nautilus is to take over the desktop, which is fine for Gnome, but bad for Fluxbox.  

editing  the Nautilus line in /etc/X11/fluxbox/fluxbox-menu
[exec] (Nautilus) {/usr/bin/nautilus} </usr/share/pixmaps/nautilus.xpm>
to  
[exec] (Nautilus) {/usr/bin/nautilus --no-desktop} </usr/share/pixmaps/nautilus.xpm>
works.
BUT
installing new apps writes to menu and this overwrites /etc/X11/fluxbox/fluxbox-menu  deleting changes and we are back to nautilus taking over the desktop everytime we install a new app.

The trick is to get nautilus to default to --no-desktop AND stay that way everytime the menu updates.

My question is, Can this be done?
Cheers, and thanks in advance.
Mr. Crowley.

---

### Post by p_quarles on 2008-07-07
Probably not without hacking the update-menus source code (in other words, I doubt this is even the doing of Fluxbox). 

Most Fluxbox users, I think, use a menu file in ~/.fluxbox/ rather than relying on the systemwide menu. If you *want* the systemwide menu, of course, you can always include it in your user's menu. E.g.:
```
[include] (/etc/X11/fluxbox/fluxbox-menu)
```
will add that menu to yours.

---

### Post by HandyAndy on 2008-07-07
Yep, that's just what I do.
I've got a simple, one-level menu of just the apps I use all the time, then an entry for the full fluxbox menu so that I can still get to the whole lot when I need to.

If you want a Nautilus-like file manager but faster, lighter and without all the baggage, try Thunar - it's in the repos.

I like Rox too, though it's got a completely different look and feel to Nautilus and Thunar. I find it does some things better, so I use both Thunar and Rox. I've set Rox to open with sudo, so its 'oddness' is a constant reminder that I'm root when I'm using it.

---

### Post by angry_johnnie on 2008-07-07
Try editing the menu file in your /home folder.

It used to be something like /home/you/.fluxbox/menu

Just add 

[exec] (Nautilus) {/usr/bin/nautilus --no-desktop} </usr/share/pixmaps/nautilus.xpm>

before this line:

[include] (/etc/X11/fluxbox/fluxbox-menu)

So your menu will have Nautilus, and then everything else.

---

### Post by stilus on 2009-03-13
I suddenly had problems with nautilus "connect to server" (under 'File'). Service Type would only list "Custom Location" and would not work with ssh:// or smb://, nor list these options. The fix was simple. First, I cleaned out ~/.nautilus (a lot of cruft there), only removing the files (also in the metafiles directory). Secondly, I changed my ~/.fluxbox/menu to read:

[exec]  (nautilus) {dbus-launch nautilus --no-desktop} <>

And my ~/.fluxbox/keys to read:

Mod1 Control N :ExecCommand dbus-launch nautilus --no-desktop ~/Documents

I logged out and in and now I can simply connect to ssh using the gvfs again!

Hope this helps someone...

---

### Post by sierd on 2009-07-31
Create a script called /usr/local/bin/filebrowser containing the following:

```
#!/bin/sh
nautilus2 --no-desktop
```

Do it like so:

open your xterm and than ```
sudo nano /usr/local/bin/filebrowser
```

This will open a text editor with root priviledges. Copy and paste the code above into the document and save it as filebrowser, in the /usr/local/bin/ directory.

Set the execute bit for filebrowser like so:

Open a terminal and run

```
chmod +x /usr/local/bin/filebrowser
```


Recreate the symlink /usr/bin/nautilus pointing it to /usr/local/bin/filebrowser

Do it like so:

In a terminal move the current symlink:

```
sudo mv /usr/bin/nautilus /usr/bin/nautilus2
```

And replace it like so:

```
sudo mv /usr/local/bin/filebrowser /usr/bin/nautilus
```

---

