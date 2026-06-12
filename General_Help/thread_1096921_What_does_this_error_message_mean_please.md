---
title: "What does this error message mean please?"
date: 2009-03-15
forum: General Help
---

### Post by WOOHOOHOO on 2009-03-15
(and how do i fix it?) :o)

When i started up this morning, an error message came up saying "Users $HOME.dmrc file is being ignored. This prevents sessions and languages from being saved. File should be owned by user and have 644 permissions."

I was pee'ing around yesterday with permissions (as im fed up of being told i can't do stuff as i'm not the admin, even tough i am). I screwed up....

Any ideas?

---

### Post by taurus on 2009-03-15
At the GUI login screen, press <Ctrl><Alt>F2 and log in with your username and password.  Then, run

```
sudo chown -R username:username /home/username
sudo chown 600 /home/username/.dmrc
```
Replace username with your login name.
Now, press <Alt>F7 to get back to GUI login screen and log in.  Do you still get the same error message about $HOME/.dmrc?

---

### Post by WOOHOOHOO on 2009-03-15
hi, thanks for the quick reply. I don't go through the log-in screen, when i turn on it auto goes to full load up. How can i restart to that?

cheers!

---

### Post by taurus on 2009-03-15
Just log out.  That would drop you to a GUI login screen.  Otherwise, just open a terminal and run those commands from there.

Applications -> Accessories -> Terminal

---

### Post by WOOHOOHOO on 2009-03-15
Did the above and restarted, the same error message is there.

---

### Post by taurus on 2009-03-15
Post the output of this command from a terminal.

```
ls -la ~
```

---

### Post by WOOHOOHOO on 2009-03-15
-rw-r--r--  1 jamie jamie    60 2009-02-03 09:02 .openalrc
drwxrwxrwx  3 jamie jamie  4096 2009-02-06 10:23 .openoffice.org2
drwxrwxrwx  3 jamie jamie  4096 2009-02-26 21:31 .openttd
drwxrwxrwx  2 jamie jamie  4096 2009-02-22 15:45 Pictures
-rw-r--r--  1 jamie jamie   675 2008-12-03 17:48 .profile
drwxrwxrwx  2 jamie jamie  4096 2008-12-03 18:02 Public
drwxrwxrwx  2 jamie jamie  4096 2008-12-03 18:02 .pulse
-rw-------  1 jamie jamie   256 2008-12-03 18:02 .pulse-cookie
drwxrwxrwx  6 jamie jamie  4096 2009-03-14 12:35 .purple
-rw-------  1 jamie jamie   887 2009-02-06 10:00 .recently-used
-rw-------  1 jamie jamie 36281 2009-03-14 08:41 .recently-used.xbel
-rw-r--r--  1 jamie jamie     0 2008-12-03 18:17 .sudo_as_admin_successful
drwxrwxrwx  4 jamie jamie  4096 2008-12-31 13:51 .sudoku
drwxrwxrwx  2 jamie jamie  4096 2008-12-03 18:02 Templates
drwxrwxrwx  2 jamie jamie  4096 2009-01-12 19:58 .themes
drwxrwxrwx  5 jamie jamie  4096 2009-01-12 19:58 .thumbnails
drwxrwxrwx  2 jamie jamie  4096 2008-12-03 19:09 .update-manager-core
drwxrwxrwx  2 jamie jamie  4096 2008-12-03 18:02 .update-notifier
drwxrwxrwx  2 jamie jamie  4096 2008-12-03 18:02 Videos
drwxrwxrwx  2 jamie jamie  4096 2009-01-01 08:49 .wapi
-rw-r--r--  1 jamie jamie     2 2009-02-23 10:28 .windows-serial
-rw-------  1 jamie jamie   123 2009-03-14 06:58 .Xauthority
-rw-r--r--  1 jamie jamie  1796 2009-03-15 17:20 .xsession-errors

---

### Post by taurus on 2009-03-15
Use the scroll bar on the right to scroll up.  You only posted the last 24 lines of the output.

---

### Post by WOOHOOHOO on 2009-03-15
sorry, prety new to this.

total 352
drwxrwxrwx 50 jamie jamie  4096 2009-03-15 17:19 .
drwxr-xr-x  3 root  root   4096 2008-12-03 17:48 ..
drwxrwxrwx  3 jamie jamie  4096 2008-12-03 18:30 .adobe
-rw-------  1 jamie jamie  9725 2009-03-15 17:27 .bash_history
-rw-r--r--  1 jamie jamie   220 2008-12-03 17:48 .bash_logout
-rw-r--r--  1 jamie jamie  3115 2008-12-03 17:48 .bashrc
drwxrwxrwx  2 jamie jamie  4096 2009-03-11 22:51 bin
drwxrwxrwx  5 jamie jamie  4096 2009-03-07 08:02 .cache
drwxrwxrwx  9 jamie jamie  4096 2009-03-15 17:19 .config
drwxrwxrwx  3 jamie jamie  4096 2008-12-03 18:02 .dbus
drwxrwxrwx  3 jamie jamie  4096 2009-03-14 08:40 Desktop
-rw-------  1   600 jamie    28 2009-03-14 06:58 .dmrc
drwxrwxrwx  2 jamie jamie  4096 2008-12-16 21:42 Documents
-rw-------  1 jamie jamie    16 2008-12-03 18:02 .esd_auth
drwxrwxrwx  8 jamie jamie  4096 2009-01-02 22:30 .evolution
lrwxrwxrwx  1 jamie jamie    26 2008-12-03 17:48 Examples -> /usr/share/example-content
drwxrwxrwx  2 jamie jamie  4096 2009-03-06 19:50 .fontconfig
drwxrwxrwx  3 jamie jamie  4096 2009-02-23 08:49 .fr-fD14Q4
drwxrwxrwx  3 jamie jamie  4096 2009-02-23 08:39 .fr-PukWdW
drwxrwxrwx  2 jamie jamie  4096 2008-12-05 11:51 .gcjwebplugin
drwxrwxrwx  5 jamie jamie  4096 2009-03-15 17:19 .gconf
drwxrwxrwx  2 jamie jamie  4096 2009-03-15 17:30 .gconfd
drwxrwxrwx  4 jamie jamie  4096 2008-12-09 10:09 .gegl-0.0
drwxrwxrwx  2 jamie jamie  4096 2008-12-04 12:11 .ggz
drwxrwxrwx 22 jamie jamie  4096 2009-02-04 23:14 .gimp-2.6
-rw-r-----  1 jamie jamie     0 2009-03-14 13:20 .gksu.lock
drwxrwxrwx  3 jamie jamie  4096 2009-02-01 20:42 .glest
drwxrwxrwx 17 jamie jamie  4096 2009-03-14 17:52 .gnome2
drwxrwxrwx  2 jamie jamie  4096 2008-12-03 18:02 .gnome2_private
drwxrwxrwx  2 jamie jamie  4096 2008-12-03 18:02 .gnupg
drwxrwxrwx  2 jamie jamie  4096 2009-03-14 14:56 .gstreamer-0.10
-rw-r--r--  1 jamie jamie   108 2009-03-15 17:19 .gtk-bookmarks
drwx------  2 jamie jamie  4096 2008-12-03 18:02 .gvfs
-rw-------  1 jamie jamie 20864 2009-03-15 17:19 .ICEauthority
drwxrwxrwx  2 jamie jamie  4096 2009-02-23 07:56 .icedteaplugin
drwxrwxrwx  2 jamie jamie  4096 2009-01-12 19:58 .icons
drwxrwxrwx  3 jamie jamie  4096 2009-02-14 11:38 .java
drwxrwxrwx  3 jamie jamie  4096 2009-01-02 22:15 .kde
drwxrwxrwx  2 jamie jamie  4096 2008-02-25 22:39 lib
drwxrwxrwx  3 jamie jamie  4096 2008-12-03 18:02 .local
drwxrwxrwx  3 jamie jamie  4096 2008-12-03 18:30 .macromedia
drwxrwxrwx  4 jamie jamie  4096 2008-12-03 18:04 .mozilla
-rw-r--r--  1 jamie jamie     0 2009-02-25 07:40 .mtab.fuseiso
drwxrwxrwx  2 jamie jamie  4096 2008-12-03 18:02 Music
drwxrwxrwx  3 jamie jamie 32768 2009-03-14 17:52 .nautilus
drwxrwxrwx  3 jamie jamie  4096 2008-12-06 14:33 .netx
-rw-r--r--  1 jamie jamie    54 2008-12-05 12:07 .netxrc
-rw-r--r--  1 jamie jamie    60 2009-02-03 09:02 .openalrc
drwxrwxrwx  3 jamie jamie  4096 2009-02-06 10:23 .openoffice.org2
drwxrwxrwx  3 jamie jamie  4096 2009-02-26 21:31 .openttd
drwxrwxrwx  2 jamie jamie  4096 2009-02-22 15:45 Pictures
-rw-r--r--  1 jamie jamie   675 2008-12-03 17:48 .profile
drwxrwxrwx  2 jamie jamie  4096 2008-12-03 18:02 Public
drwxrwxrwx  2 jamie jamie  4096 2008-12-03 18:02 .pulse
-rw-------  1 jamie jamie   256 2008-12-03 18:02 .pulse-cookie
drwxrwxrwx  6 jamie jamie  4096 2009-03-14 12:35 .purple
-rw-------  1 jamie jamie   887 2009-02-06 10:00 .recently-used
-rw-------  1 jamie jamie 36281 2009-03-14 08:41 .recently-used.xbel
-rw-r--r--  1 jamie jamie     0 2008-12-03 18:17 .sudo_as_admin_successful
drwxrwxrwx  4 jamie jamie  4096 2008-12-31 13:51 .sudoku
drwxrwxrwx  2 jamie jamie  4096 2008-12-03 18:02 Templates
drwxrwxrwx  2 jamie jamie  4096 2009-01-12 19:58 .themes
drwxrwxrwx  5 jamie jamie  4096 2009-01-12 19:58 .thumbnails
drwxrwxrwx  2 jamie jamie  4096 2008-12-03 19:09 .update-manager-core
drwxrwxrwx  2 jamie jamie  4096 2008-12-03 18:02 .update-notifier
drwxrwxrwx  2 jamie jamie  4096 2008-12-03 18:02 Videos
drwxrwxrwx  2 jamie jamie  4096 2009-01-01 08:49 .wapi
-rw-r--r--  1 jamie jamie     2 2009-02-23 10:28 .windows-serial
-rw-------  1 jamie jamie   123 2009-03-14 06:58 .Xauthority
-rw-r--r--  1 jamie jamie  1796 2009-03-15 17:20 .xsession-errors

---

### Post by taurus on 2009-03-15
```
chmod 755 /home/jamie
```
Now, log out and back in again.

---

### Post by WOOHOOHOO on 2009-03-15
nope, still same error message.

---

### Post by taurus on 2009-03-15
Reboot your machine.  Now, log in and if there is an error message, post the whole thing here.

---

### Post by Peasantoid on 2009-03-15
You can try recursively chmod-ing everything with a command like "chmod -R 0777 ~".

[edit] Oops, sorry, I didn't see this had been posted before.

---

### Post by WOOHOOHOO on 2009-03-15
word for word:

"User's $HOME.dmrc file is being ignored. This prevents sessions and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owened by user and not writable by others."

(can you let me know what i've done wrong also, as it means zip to me). Thanks!

---

### Post by drs305 on 2009-03-15
I refrained from jumping in as you were getting good advice. I think you've done all this but if you want to start from scratch or review what you have already accomplished you can look at this link:
[http://ubuntuforums.org/showthread.php?p=6161267]("http://ubuntuforums.org/showthread.php?p=6161267")

It's a howto on solving .dmrc errors.

---

### Post by taurus on 2009-03-15
> **WOOHOOHOO said:**
> word for word:

"User's **[COLOR="Red"]$HOME.dmrc[/COLOR]** file is being ignored. This prevents sessions and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owened by user and not writable by others."

(can you let me know what i've done wrong also, as it means zip to me). Thanks!

There is something wrong with that wording because it should have said $HOME/.dmrc.

---

### Post by mhgsys on 2009-03-15
```

chmod 644 /home/jamie

```

Or am I going crazy here.

btw, found this:
[http://ubuntuforums.org/archive/index.php/t-331855.html](http://ubuntuforums.org/archive/index.php/t-331855.html)

---

### Post by WOOHOOHOO on 2009-03-15
ok, since we can't fix it, will this problem cause me any major probs if not resolved?

(644, 700, 999, no idea!)

Oh yeah, i'm looking for a bopok to buy to really learn some Linux stuff (for beginners). Any ideas on good books? Would be nice to learn to fix my own crap :) )

---

### Post by mhgsys on 2009-03-15
Did you trie above?
+ Did you see the link in my edit

---

### Post by taurus on 2009-03-15
> **mhgsys said:**
> ```

chmod **[COLOR="Red"]6[/COLOR]**44 /home/jamie

```

Or am I going crazy here.

You need executable permission, x, if you want to change to a directory.  Making your $HOME with only read and write will lock you out alright.

If you don't believe, try it with your $HOME!

---

### Post by mhgsys on 2009-03-15
Should I edit a wrong post by deleting what I wrote or by adding the info I found?

This will fix the error message

```

sudo chmod 644 /home/username/.dmrc
sudo chown username /home/username/.dmrc
sudo chmod 755 /home/username

```

---

### Post by WOOHOOHOO on 2009-03-15
> **mhgsys said:**
> Did you trie above?
+ Did you see the link in my edit


yeah, i tried all above. I', just reading the link but it seems i did 99% of it.

Thinking back to when i screwed it up, I was trying to add ascenario to OTTD file, but it said i did needed permissions. So i read on a site to change permissions in users and groups. i also right clicked folders and changed permissions that way. It still didnt work, so i moved them through the terminal. I've tried to ndo what i did, but its no good.

---

### Post by WOOHOOHOO on 2009-03-15
> **mhgsys said:**
> Should I edit a wrong post by deleting what I wrote or by adding the info I found?



sudo chmod 644 /home/username/.dmrc
sudo chown username /home/username/.dmrc
sudo chmod 755 /home/username

Hey! i re entered the above in trerminal, and it worked, no more error message :)

Thanks sooo omuch for the help, slowly im getting there. :o)

---

### Post by mhgsys on 2009-03-15
lol  

I actually tried it with my own HOME.
and found this solution.\

nice to see it worked for you

[SOLVED]

---

