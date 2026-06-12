---
title: "Error: Your session lasted less than 10 seconds. Many distros sharing home dir"
date: 2009-01-31
forum: Desktop Environments
---

### Post by Schuenemann on 2009-01-31
Hi, I'm getting this error message frequently when I log in:

> Your session lasted less than 10 seconds. If you didn't finish a session, this could mean there is a problem in the installation or your could have few disk space. Try to start a security session to check if you can fix the problem.

I suspect this happens because I have multiple distros sharing the same home directory. One of them is probably messing something in my home dir, making gnome confused.

The first time this happened, I deleted ~/.gnome2/ and it was fixed.
The second, ~/.ICEauthority did not belong to me. I changed owner and it went ok.
The third, I had to changed my UID and GID (the other distro probably assigned different IDs for the user).

Now, none of these methods worked. I've searched the web, but found nothing about this error message involving multiple distros sharing the home dir.


How can I get that problem solved?


Thanks

---

### Post by taurus on 2009-01-31
Check the disk space first.  While at the GUI login screen, press <Ctrl><Alt>F2 and log in with your username and password.  Then, post the output of this command.

```
df -h
```

p.s.  And yes.  Ubuntu assigns the first user with UID 1000 while most other distros use 500.

---

### Post by Schuenemann on 2009-01-31
Hi, thanks for your answer.
The partition has over 5GB free. That isn't the problem.

Yeah, I had to change the IDs to 500 in order to match the other distro.


What else could cause that problem?

---

### Post by taurus on 2009-01-31
If you changed the UID of your $HOME to 500, did you remember to change it in /etc/passwd also?

```
more /etc/passwd
```

p.s.  I am not talking about free disk on /home.  I am talking about the disk space on /, specifically /tmp.

---

### Post by Schuenemann on 2009-01-31
The UID of $HOME was already 500 (the other distro did it). I changed my UID and GID in /etc/passwd and /etc/group.

---

### Post by Schuenemann on 2009-01-31
Didn't see your PS.

This is the output from df -h
```

/dev/sda6             9.9G  4.1G  5.4G  44% /
tmpfs                 496M     0  496M   0% /lib/init/rw
varrun                496M  212K  496M   1% /var/run
varlock               496M     0  496M   0% /var/lock
udev                  496M  2.9M  494M   1% /dev
tmpfs                 496M  176K  496M   1% /dev/shm
lrm                   496M  2.4M  494M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda3              47G 1005M   44G   3% /home
tmpfs                 496M  2.4M  494M   1% /lib/modules/2.6.27-11-generic/volatile
```

---

### Post by taurus on 2009-01-31
I would look in $HOME again to make sure all the files/directories, including the hidden ones, have all the right ownership and permissions.

```
ls -la ~
```
And if it's more than one screen, you can pipe it through more.

```
ls -la ~ | more
```
Hit the Space key for the next 24 lines or q to exit at the current screen.

---

### Post by Schuenemann on 2009-01-31
```
drwx--x--x 47 otto otto     4096 2009-01-31 21:43 .
drwxr-xr-x  5 root root     4096 2008-10-20 09:27 ..
drwx------  3 otto otto     4096 2009-01-24 20:02 .adobe
-rw-------  1 otto otto     5862 2009-01-31 21:40 .bash_history
-rw-r--r--  1 otto otto      220 2009-01-11 14:57 .bash_logout
-rw-r--r--  1 otto otto      414 2009-01-11 14:57 .bash_profile
-rw-r--r--  1 otto otto     2227 2009-01-11 14:57 .bashrc
drwxr-xr-x  5 otto otto     4096 2009-01-25 12:32 .blender
drwxr-xr-x  6 otto otto     4096 2009-01-31 19:02 .cache
drwx------  3 otto otto     4096 2009-01-14 18:44 .compiz
drwxr-xr-x 10 otto otto     4096 2009-01-31 19:02 .config
drwx------  3 otto otto     4096 2009-01-14 17:59 .dbus
drwxr-xr-x  2 otto otto     4096 2009-01-31 21:37 Desktop
drwx------  2 otto otto     4096 2009-01-31 19:43 .dillo
-rw-------  1 otto otto       67 2009-01-31 21:37 .dmrc
drwxr-xr-x  2 otto otto     4096 2009-01-24 19:48 Documents
drwxr-xr-x  2 otto otto     4096 2009-01-31 21:37 downloads
-rw-------  1 otto otto       16 2009-01-14 17:59 .esd_auth
drwxr-xr-x  7 otto otto     4096 2009-01-31 19:45 .evolution
drwxr-xr-x  5 otto users    4096 2009-01-31 20:49 .fluxbox
drwxr-xr-x  2 otto otto     4096 2009-01-31 12:05 .fontconfig
drwx------  5 otto otto     4096 2009-01-31 21:37 .gconf
drwx------  2 otto otto     4096 2009-01-31 21:42 .gconfd
-rw-r-----  1 otto otto        0 2009-01-31 21:04 .gksu.lock
drwx------ 10 otto otto     4096 2009-01-31 21:28 .gnome2
drwx------  2 otto otto     4096 2009-01-14 17:59 .gnome2_private
drwx------  2 otto otto     4096 2009-01-14 17:59 .gnupg
drwxr-xr-x  2 otto otto     4096 2009-01-14 22:06 .gstreamer-0.10
-rw-r--r--  1 otto otto      104 2009-01-31 21:37 .gtk-bookmarks
dr-x------  2 otto otto        0 2009-01-31 21:37 .gvfs
-rw-------  1 otto otto     5814 2009-01-31 21:37 .ICEauthority
drwxr-xr-x  2 otto otto     4096 2009-01-14 18:11 .icons
drwx------  2 otto otto     4096 2009-01-31 19:38 .links2
drwx------  3 otto otto     4096 2009-01-14 17:59 .local
drwx------  3 otto otto     4096 2009-01-24 20:02 .macromedia
drwx------  4 otto otto     4096 2009-01-24 14:14 .mozilla
drwxr-xr-x  2 otto otto     4096 2009-01-25 20:21 .mplayer
drwxr-xr-x  2 otto otto     4096 2009-01-24 19:48 Music
drwxr-xr-x  3 otto otto     4096 2009-01-31 21:28 .nautilus
drwx------  3 otto otto     4096 2009-01-24 15:19 .openoffice.org2
drwx------  9 otto otto     4096 2009-01-31 21:10 .opera
drwxr-xr-x  2 otto otto     4096 2009-01-24 19:48 Pictures
drwxr-xr-x  2 otto otto     4096 2009-01-24 19:48 Public
drwx------  2 otto otto     4096 2009-01-14 22:07 .pulse
-rw-------  1 otto otto      256 2009-01-14 17:59 .pulse-cookie
drwx------  6 otto otto     4096 2009-01-31 19:43 .purple
drwxr-xr-x  2 otto otto     4096 2009-01-31 21:10 .qt
-rw-r--r--  1 otto otto  5658784 2009-01-25 12:39 Rattling_Bones_preview.mov
-rw-------  1 otto otto    97138 2009-01-31 21:27 .recently-used.xbel
-rw-r--r--  1 otto users    3729 2009-01-31 20:39 .screenrc
drwxr-xr-x  2 otto otto     4096 2009-01-25 20:18 .solarwolf
-rw-r--r--  1 otto otto        0 2009-01-14 18:02 .sudo_as_admin_successful
drwxr-xr-x  2 otto otto     4096 2009-01-24 19:48 Templates
drwxr-xr-x  2 otto otto     4096 2009-01-14 18:11 .themes
drwx------  4 otto otto     4096 2009-01-14 18:23 .thumbnails
drwxr-xr-x  2 otto otto     4096 2009-01-24 14:55 .update-manager-core
drwx------  2 otto otto     4096 2009-01-14 18:52 .update-notifier
drwxr-xr-x  2 otto otto     4096 2009-01-24 19:48 Videos
-rw-------  1 otto otto      120 2009-01-31 21:37 .Xauthority
drwx------  4 otto otto     4096 2009-01-31 19:42 .xchat2
drwxr-xr-x  2 otto users    4096 2009-01-31 20:46 .xine
-rw-r--r--  1 otto otto      129 2009-01-25 11:16 .xscreensaver-getimage.cache
-rw-r--r--  1 otto users     779 2009-01-31 20:39 .xsession
-rw-r--r--  1 otto otto      185 2009-01-31 21:36 .xsession-errors
-rw-r--r--  1 otto otto   170212 2009-01-25 20:28 .xsession-errors.old
drwxr-xr-x  2 otto otto     4096 2009-01-25 09:52 .zsnes
```

Weird .. belongs to root. But I changed owner and group to otto, same error happened.
Any idea?

---

### Post by taurus on 2009-01-31
Look in ~/.xsession-errors to see what does it say.

```
more .xsession-errors
```

Also, maybe it doesn't like some of the settings that you perhaps configured/used while you ran the other distro.

---

### Post by Schuenemann on 2009-01-31
Nothing important I think.
```
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
```

---

### Post by taurus on 2009-01-31
What if you rename those config files,  now see if you are able to log in to Gnome again?

```
mv .config .config_bak
mv .gconf .gconf_bak
mv .gconfd .gconfd_bak
mv .gnome2 .gnome2_bak
mv .gnome2_private .gnome2_private_bak
```

---

### Post by Schuenemann on 2009-01-31
Nope. I just lost my theme preferences :)

---

### Post by taurus on 2009-01-31
You just move them back.

```

mv .config_bak .config
mv .gconf_bak .gconf
mv .gconfd_bak .gconfd
mv .gnome2_bak .gnome2
mv .gnome2_private_bak .gnome2_private

```

---

### Post by Schuenemann on 2009-02-01
Any other suggestion?

---

### Post by IntuitiveNipple on 2009-02-02
Since you've altered UID and GID the user home directory should have all its files updated too.

First, check for any files *not* having the expected settings:
```

whoami
cd ~
find . ! -user otto -o ! -group otto

```
This will search the home directory and all sub-directories for any entry that does **not** have ownership set to user "otto" or group "otto"

Examine the list for any unexpected ownerships, especiall files in 'hidden' sub-directories, e.g. in ~/.config/ or ~/.local/

To fix them, you can use find again:
```

cd ~
sudo find . ! -user otto -exec chown otto: {} \;

```
This will execute the command "chown otto: <filename>" for each file not currently owned by "otto". Note it runs using sudo because otherwise files not currently owned by otto probably couldn't have their ownership changed.

---

### Post by Schuenemann on 2009-02-02
```
otto@flaweiros:~$ find . ! -user otto -o ! -group otto
      ./.fluxbox
      ./.fluxbox/startup
      ./.fluxbox/styles
      ./.fluxbox/init
      ./.fluxbox/slitlist
      ./.fluxbox/menu
      ./.fluxbox/pixmaps
      ./.fluxbox/fbrun_history
      ./.fluxbox/backgrounds
      ./.fluxbox/keys
      ./.xsession
      ./.screenrc
      ./.mozilla/firefox/5n0cp936.default/history.dat
      ./.mozilla/firefox/5n0cp936.default/bookmarkbackups/bookmarks-2009-01-31.html
      ./.mozilla/firefox/5n0cp936.default/urlclassifier2.sqlite
      ./.mozilla/firefox/5n0cp936.default/bookmarks.bak
      ./.mozilla/firefox/5n0cp936.default/bookmarks.html
      ./.xine
      ./.xine/keymap
      ./.xine/xine-ui_old_playlist.tox
      ./.xine/config
      ./.xine/catalog.cache
```

Since fluxbox is only used in Slackware, I think the only reasonable ones are ./.xsession ./.screenrc (their group is users), but I changed the group for both and I still have the same problem.

I would like to clarify that the only session type that has this problem is "1. Execute script Xclient". "2. GNOME" works ok.


Any more suggestions are appreciated.
Thanks

---

