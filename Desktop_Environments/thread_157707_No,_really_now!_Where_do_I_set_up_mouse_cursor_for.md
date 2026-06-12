---
title: "No, really now! Where do I set up mouse cursor for login screen?"
date: 2006-04-09
forum: Desktop Environments
---

### Post by louis_nichols on 2006-04-09
Hi folks? I experienced a crash about a week ago and it left my installation a little crippled. I managed to sort out almost everything else, except this thing:

The GDM login screen only displays the plain-old-n-ugly black X cursor theme. I've been googling and reading about this the whole time, but an answer was nowhere to be found.

Someone MUST know!! Please help me! It's not a big thing, but my ubuntu is so... perfect, otherwise, that I can't stand it. :)

EDIT: typos

---

### Post by Ramses de Norre on 2006-04-09
sudo apt-get install gcursor
system > preferences > mouse
Or isn't this what you mean?

---

### Post by louis_nichols on 2006-04-09
gcursor just sets the theme for the current user. stores the theme under ~... not that GDM wouldn't be able to see it, but I expect GDM to read the theme from /usr/share/theme or smth. I thought it had something to do with the theme for root user, but I changed cursors for root many times, in all possible ways, and still no change under GDM.

---

### Post by louis_nichols on 2006-04-10
C'mon ppl! Someone must know something!

Pretty pleeeeazeeee! :)

---

### Post by maitreya on 2006-04-10
/usr/share/themes/Human/cursor.theme maybe

Replace Human if you're not using the default one.

---

### Post by louis_nichols on 2006-04-10
Thanks for the tip, maitreya, but, unfortunatelly, it didn't do it. :( I still got the same black cursor theme.

Human is actually the one I want, but dunno where to set that.

---

### Post by txgunslinger on 2006-04-10
This is just for the login screen, right?  Once you log in, does your curser return to normal?

---

### Post by louis_nichols on 2006-04-10
yes, everything is great! both for user and root. (well, except acroread, which shows an unknown theme, but I'm looking into that too). As soon as I login, I see the desired theme for each.

This is just for the darned login screen.

---

### Post by maitreya on 2006-04-11
Does this /usr/share/icons/Human exist. Your gdm is fully themed (Human), except for the cursor, is that correct.

---

### Post by louis_nichols on 2006-04-11
yes, /usr/share/icons/Human is there. Here's what's in it:

```
myself@home:~$ ls -lRh /usr/share/icons/Human/
/usr/share/icons/Human/:
total 9.0K
drwxr-xr-x  2 root root 1.1K 2006-01-25 12:26 cursors
-rw-r--r--  1 root root 3.5K 2006-01-25 12:30 icon-theme.cache
-rw-r--r--  1 root root  411 2005-10-05 02:13 index.theme
drwxr-xr-x  5 root root  128 2006-01-25 12:26 scalable

/usr/share/icons/Human/cursors:
total 180K
-rw-r--r--  1 root root  19K 2005-10-05 02:13 08e8e1c95fe2fc01f976f1e063a24ccd
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 arrow
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 based_arrow_down
-rw-r--r--  1 root root 2.3K 2005-10-05 02:13 based_arrow_up
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 bottom_left_corner
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 bottom_right_corner
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 bottom_side
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 double_arrow
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 draft_large
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 draft_small
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 fleur
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 hand1
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 hand2
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 left_ptr
-rw-r--r--  1 root root  19K 2005-10-05 02:13 left_ptr_watch
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 left_side
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 ll_angle
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 question_arrow
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 right_ptr
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 right_side
-rw-r--r--  1 root root 2.3K 2005-10-05 02:13 sb_h_double_arrow
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 sb_right_arrow
-rw-r--r--  1 root root 2.3K 2005-10-05 02:13 sb_up_arrow
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 sb_v_double_arrow
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 top_left_arrow
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 top_left_corner
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 top_right_corner
-rw-r--r--  1 root root 2.3K 2005-10-05 02:13 top_side
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 ul_angle
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 ur_angle
-rw-r--r--  1 root root  19K 2005-10-05 02:13 watch
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 X_cursor
-rw-r--r--  1 root root 2.4K 2005-10-05 02:13 xterm

/usr/share/icons/Human/scalable:
total 2.0K
drwxr-xr-x  2 root root 2.0K 2006-01-25 12:26 apps
drwxr-xr-x  2 root root  288 2006-01-25 12:26 devices
drwxr-xr-x  2 root root  920 2006-01-25 12:26 filesystems

/usr/share/icons/Human/scalable/apps:
total 1.7M
-rw-r--r--  1 root root 30K 2005-10-05 02:13 administration.svg
-rw-r--r--  1 root root 21K 2005-10-05 02:13 coaster.svg
-rw-r--r--  1 root root 30K 2005-10-05 02:13 control-center2.svg
-rw-r--r--  1 root root 15K 2005-10-05 02:13 cups.svg
-rw-r--r--  1 root root 20K 2005-10-05 02:13 disks.svg
-rw-r--r--  1 root root 20K 2005-10-05 02:13 display-capplet.svg
-rw-r--r--  1 root root 48K 2005-10-05 02:13 epiphany.svg
-rw-r--r--  1 root root 41K 2005-10-05 02:13 evolution.svg
-rw-r--r--  1 root root 16K 2005-10-05 02:13 file-manager.svg
-rw-r--r--  1 root root 19K 2005-10-05 02:13 file-roller.svg
-rw-r--r--  1 root root 27K 2005-10-05 02:13 firefox.svg
-rw-r--r--  1 root root 23K 2005-10-05 02:13 gaim.svg
-rw-r--r--  1 root root 32K 2005-10-05 02:13 galeon.svg
-rw-r--r--  1 root root 23K 2005-10-05 02:13 gedit-icon.svg
-rw-r--r--  1 root root 33K 2005-10-05 02:13 gftp.svg
-rw-r--r--  1 root root 34K 2005-10-05 02:13 gimp.svg
-rw-r--r--  1 root root 20K 2005-10-05 02:13 glade.svg
-rw-r--r--  1 root root 26K 2005-10-05 02:13 gnome-cd-player.svg
-rw-r--r--  1 root root 19K 2005-10-05 02:13 gnome-cd.svg
-rw-r--r--  1 root root 34K 2005-10-05 02:13 gnome-devel.svg
-rw-r--r--  1 root root 15K 2005-10-05 02:13 gnome-folder.svg
-rw-r--r--  1 root root 23K 2005-10-05 02:13 gnome-globe.svg
-rw-r--r--  1 root root 23K 2005-10-05 02:13 gnome-graphics.svg
-rw-r--r--  1 root root 23K 2005-10-05 02:13 gnome-help.svg
-rw-r--r--  1 root root 27K 2005-10-05 02:13 gnome-joystick.svg
-rw-r--r--  1 root root 45K 2005-10-05 02:13 gnome-multimedia.svg
-rw-r--r--  1 root root 28K 2005-10-05 02:13 gnome-network-capplet.svg
-rw-r--r--  1 root root 19K 2005-10-05 02:13 gnome-other.svg
-rw-r--r--  1 root root 30K 2005-10-05 02:13 gnome-settings.svg
-rw-r--r--  1 root root 34K 2005-10-05 02:13 gnome-setting.svg
-rw-r--r--  1 root root 38K 2005-10-05 02:13 gnome-system-config.svg
-rw-r--r--  1 root root 15K 2005-10-05 02:13 gnome-system-monitor.svg
-rw-r--r--  1 root root 19K 2005-10-05 02:13 gnome-system.svg
-rw-r--r--  1 root root 15K 2005-10-05 02:13 gnome-terminal.svg
-rw-r--r--  1 root root 26K 2005-10-05 02:13 gnome-util.svg
-rw-r--r--  1 root root 21K 2005-10-05 02:13 graveman.svg
-rw-r--r--  1 root root 45K 2005-10-05 02:13 inkscape.svg
-rw-r--r--  1 root root 21K 2005-10-05 02:13 k3b.svg
-rw-r--r--  1 root root 23K 2005-10-05 02:13 kate.svg
-rw-r--r--  1 root root 41K 2005-10-05 02:13 media-player-48.svg
-rw-r--r--  1 root root 27K 2005-10-05 02:13 mozilla-firefox.svg
-rw-r--r--  1 root root 28K 2005-10-05 02:13 mozilla-icon.svg
-rw-r--r--  1 root root 28K 2005-10-05 02:13 mozilla.svg
-rw-r--r--  1 root root 19K 2005-10-05 02:13 my-computer.svg
-rw-r--r--  1 root root 15K 2005-10-05 02:13 ooo_printeradmin.svg
-rw-r--r--  1 root root 15K 2005-10-05 02:13 print-manager.svg
-rw-r--r--  1 root root 23K 2005-10-05 02:13 quanta.svg
-rw-r--r--  1 root root 28K 2005-10-05 02:13 redhat-internet.svg
-rw-r--r--  1 root root 34K 2005-10-05 02:13 sodipodi.svg
-rw-r--r--  1 root root 40K 2005-10-05 02:13 synaptic.svg
-rw-r--r--  1 root root 16K 2005-10-05 02:13 temp-home.svg
-rw-r--r--  1 root root 37K 2005-10-05 02:13 totem.svg
-rw-r--r--  1 root root 32K 2005-10-05 02:13 tsclient.svg
-rw-r--r--  1 root root 37K 2005-10-05 02:13 tux.svg
-rw-r--r--  1 root root 48K 2005-10-05 02:13 web-browser.svg
-rw-r--r--  1 root root 25K 2005-10-05 02:13 wine.svg
-rw-r--r--  1 root root 48K 2005-10-05 02:13 xchat.svg
-rw-r--r--  1 root root 26K 2005-10-05 02:13 xscreensaver.svg

/usr/share/icons/Human/scalable/devices:
total 156K
-rw-r--r--  1 root root 29K 2005-10-05 02:13 gnome-dev-cdrom.svg
-rw-r--r--  1 root root 28K 2005-10-05 02:13 gnome-dev-dvd.svg
-rw-r--r--  1 root root 22K 2005-10-05 02:13 gnome-dev-mouse-optical.svg
-rw-r--r--  1 root root 27K 2005-10-05 02:13 gnome-dev-mouse.svg
-rw-r--r--  1 root root 14K 2005-10-05 02:13 gnome-dev-printer.svg
-rw-r--r--  1 root root 28K 2005-10-05 02:13 gnome-dev-rw.svg

/usr/share/icons/Human/scalable/filesystems:
total 608K
-rw-r--r--  1 root root  52K 2005-10-05 02:13 gnome-fs-blockdev.svg
-rw-r--r--  1 root root  34K 2005-10-05 02:13 gnome-fs-bookmark-missing.svg
-rw-r--r--  1 root root  27K 2005-10-05 02:13 gnome-fs-bookmark.svg
-rw-r--r--  1 root root  19K 2005-10-05 02:13 gnome-fs-client.svg
-rw-r--r--  1 root root  38K 2005-10-05 02:13 gnome-fs-desktop.svg
-rw-r--r--  1 root root  18K 2005-10-05 02:13 gnome-fs-directory-accept.svg
-rw-r--r--  1 root root  15K 2005-10-05 02:13 gnome-fs-directory.svg
-rw-r--r--  1 root root  18K 2005-10-05 02:13 gnome-fs-directory-visiting.svg
-rw-r--r--  1 root root  33K 2005-10-05 02:13 gnome-fs-ftp.svg
-rw-r--r--  1 root root  16K 2005-10-05 02:13 gnome-fs-home.svg
-rw-r--r--  1 root root  18K 2005-10-05 02:13 gnome-fs-loading-icon.svg
-rw-r--r--  1 root root  44K 2005-10-05 02:13 gnome-fs-network.svg
-rw-r--r--  1 root root  18K 2005-10-05 02:13 gnome-fs-nfs.svg
-rw-r--r--  1 root root 8.5K 2005-10-05 02:13 gnome-fs-regular.svg
-rw-r--r--  1 root root  26K 2005-10-05 02:13 gnome-fs-search.svg
-rw-r--r--  1 root root  46K 2005-10-05 02:13 gnome-fs-server.svg
-rw-r--r--  1 root root  24K 2005-10-05 02:13 gnome-fs-share.svg
-rw-r--r--  1 root root  19K 2005-10-05 02:13 gnome-fs-smb.svg
-rw-r--r--  1 root root  18K 2005-10-05 02:13 gnome-fs-ssh.svg
-rw-r--r--  1 root root  24K 2005-10-05 02:13 gnome-fs-trash-empty.svg
-rw-r--r--  1 root root  30K 2005-10-05 02:13 gnome-fs-trash-full.svg
-rw-r--r--  1 root root  30K 2005-10-05 02:13 gnome-fs-web.svg
myself@home:~$


```

I think it's not missing anything, but I'm not sure.

And yes, everything else about the login screen is perfect except for the cursor. And the mouse doesn't work, no matter what theme I choose. I even used the GTK login scree, and the mouse cursors still didn't change.

The only thing that happened (I dunno how relevant this is)... I configured the login screen to let me use the setup window from it, without login. Now, when that setup window would show up, cursors were ok, with the Human theme. But then, as soon as I changed anything there (like the theme or smth) it would go back to X black before I even closed that window and stay that way.

EDIT: typo

---

### Post by maitreya on 2006-04-11
Sorry but I don't think I know what else to do. Good luck though.

---

### Post by louis_nichols on 2006-04-11
Thank you very much for trying! Hope someone will help me sort this out sooner or later.

---

### Post by cap10morgan on 2006-04-23
Try this:

```

sudo rm /etc/alternatives/x-cursor-theme
sudo ln -s /usr/share/themes/Human/cursor.theme /etc/alternatives/x-cursor-theme

```

---

### Post by syutzy on 2006-09-04
See [http://www.ubuntuforums.org/showthread.php?p=1463844#post1463844]("http://www.ubuntuforums.org/showthread.php?p=1463844#post1463844")

---

### Post by louis_nichols on 2006-09-05
> **syutzy said:**
> See [http://www.ubuntuforums.org/showthread.php?p=1463844#post1463844]("http://www.ubuntuforums.org/showthread.php?p=1463844#post1463844")

Thanx for the answer, syutzy! But the problem is so old I all but forgot about it. In the meantime, I reinstalled the system perhaps even twice, so that's gone.

It's good to know, though, in case I'll ever need it again. :)

---

