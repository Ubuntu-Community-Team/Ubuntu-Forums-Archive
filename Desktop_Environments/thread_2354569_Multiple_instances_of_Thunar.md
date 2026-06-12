---
title: "Multiple instances of Thunar?"
date: 2017-03-04
forum: Desktop Environments
---

### Post by &amp;KyT$0P# on 2017-03-04
I run several programs in firejail sandbox, with firejail's [FONT=Courier New]--overlay-tmpfs[/FONT] option.  Sometimes I need to use a graphical file manager inside the sandbox.

In Xubuntu 16.04, when I try to run Thunar in the sandbox...what happens is, the existing Thunar instance, the one outside the firejail sandbox, just opens a new window.  You can see for yourself by running this command -
```
firejail --noprofile --overlay-tmpfs Thunar
```
Notice how the firejail sandbox quits like right away, yet the Thunar window remains open and functional.

How to run a separate instance of Thunar inside the sandbox?

---

### Post by #&amp;thj^% on 2017-03-04
This works on my end anyway. If I understand you correctly. 
```
firejail --noprofile --overlay-tmpfs Thunar & disown
```
This will allow you to close that terminal and issue another instance of thunar.
I find this useful to me, by not having multiple terminal windows open at once. (Just less confusing)

---

### Post by &amp;KyT$0P# on 2017-03-04
Sorry, I apparently wasn't being clear.  I'll try explaining the problem by demonstrating.

Run in Terminal -
```
FIREJAIL_PROMPT=yes firejail --noprofile --overlay-tmpfs
```
Inside the firejail, run
```
touch FooFooFoo
```
Then confirm the file was created -
```
ls -la
```

Leave that firejail running for now.

Next, open your home folder in Thunar (this step without firejail).  Notice that the FooFooFoo file does not exist, as expected.

Now let's try to launch a Thunar instance inside our existing firejail.  Back to the firejail terminal and run this -
```
Thunar
```

Do you see the FooFooFoo file?  Also, notice what happened in the Terminal window?

You can also use the system monitor's hierarchy display of processes to confirm what happened.

---

### Post by #&amp;thj^% on 2017-03-04
> **halogen2 said:**
> Sorry, I apparently wasn't being clear.  I'll try explaining the problem by demonstrating.

Run in Terminal -
```
FIREJAIL_PROMPT=yes firejail --noprofile --overlay-tmpfs
```
Inside the firejail, run
```
touch FooFooFoo
```
Then confirm the file was created -
```
ls -la
```

Leave that firejail running for now.

Next, open your home folder in Thunar (this step without firejail).  Notice that the FooFooFoo file does not exist, as expected.

Now let's try to launch a Thunar instance inside our existing firejail.  Back to the firejail terminal and run this -
```
Thunar
```

Do you see the FooFooFoo file?  Also, notice what happened in the Terminal window?

You can also use the system monitor's hierarchy display of processes to confirm what happened.

Ah Ha! Now I see..;)
Funny thing here with your code:
```
$ FIREJAIL_PROMPT=yes firejail --noprofile --overlay-tmpfs
Parent pid 9054, child pid 9055
OverlayFS configured in /run/firejail/mnt directory
Warning: cannot mount /tmp/.X11-unix in overlay
Dropping all Linux capabilities and enforcing default seccomp filter
Warning: failed to unmount /sys
Warning: whitelist feature is disabled in overlay
Child process initialized


```
I have seen multiple threads on firejail with "seccomp"
Let me see if I can come up with something here.

---

### Post by #&amp;thj^% on 2017-03-04
Huumm? This works for me.
```
FIREJAIL_PROMPT=yes firejail --overlay-tmpfs --noprofile 
```

You will still have seccomp enabled, it is just moved from thunar process to firejail process.
It is very difficult for me to say what is the best place for seccomp to be. In both cases there are advantages and disadvantages.
But anyway ls -la now shows:
```
$ ls -la
total 53924
drwx------ 27 me   me       4096 Mar  4 13:51 .
drwxr-xr-x  3 root root     4096 Mar  1 17:36 ..
-rw-------  1 me   me       2063 Mar  4 13:18 .bash_history
-rw-r--r--  1 me   me         21 Jan 21 14:03 .bash_logout
-rw-r--r--  1 me   me         57 Jan 21 14:03 .bash_profile
-rw-r--r--  1 me   me        274 Mar  1 23:43 .bashrc
drwxr-xr-x 14 me   me       4096 Mar  3 17:45 .cache
drwxr-xr-x 37 me   me       4096 Mar  4 13:16 .config
drwxr-xr-x 33 me   me       4096 Mar  3 07:00 .conky
drwxr-xr-x  2 me   me       4096 Mar  4 12:00 Desktop
-rw-r--r--  1 me   me         43 Mar  2 00:18 .dmrc
drwxr-xr-x  4 me   me       4096 Mar  4 11:58 Documents
drwxr-xr-x  3 me   me       4096 Mar  3 16:03 Downloads
drwxr-xr-x  2 me   me       4096 Mar  4 08:28 .dreamchess
drwxr-xr-x  4 me   me       4096 Mar  2 10:23 .emerald
-rw-------  1 me   me         16 Mar  1 17:39 .esd_auth
drwxr-xr-x  3 me   me      12288 Mar  2 00:47 .fonts
[COLOR=#ff0000]-rw-r--r--  1 me   me          0 Mar  4 13:51 FooFooFoo[/COLOR]
-rw-r-----  1 me   me          0 Mar  1 22:39 .gksu.lock
drwx------  3 me   me       4096 Mar  2 10:16 .gnome2
drwx------  3 me   me       4096 Mar  1 22:59 .gnupg
-rw-r--r--  1 me   me        122 Mar  2 07:34 .gtk-bookmarks
-rw-r--r--  1 me   me        607 Mar  1 23:08 .gtkrc-2.0
-rwxr-xr-x  1 root root      328 Mar  3 12:34 guidus.desktop
-rw-------  1 me   me       2178 Mar  4 09:15 .ICEauthority
drwxr-xr-x  2 me   me       4096 Mar  1 23:00 .icons
drwxr-xr-x  7 me   me       4096 Feb 27 19:58 .kodi
drwxr-xr-x  3 me   me       4096 Jan  5 09:55 .local
-rw-r--r--  1 root root     3389 Feb 11 15:25 md5sum.txt.asc
-rw-r--r--  1 root root 32505856 Oct  1  2014 mini.iso
-rw-r--r--  1 me   me      13607 Feb 11 15:23 mk_install-and-test-mkusb.bash
-rw-r--r--  1 me   me       4528 Oct  2  2014 mkusb-installer
-rwxr-xr-x  1 root root      516 Mar  3 12:34 mkusb-legacy.desktop
-rwxr-xr-x  1 root root      259 Mar  3 12:34 mkusb-legacy-root.desktop
drwx------  5 me   me       4096 Mar  1 22:45 .mozilla
drwxr-xr-x 14 me   me       4096 Mar  2 10:29 Music
drwx------  3 me   me       4096 Mar  1 18:33 .nv
-rw-r--r--  1 me   me       2149 Mar  3 19:01 .nvidia-settings-rc
drwxr-xr-x  6 me   me       4096 Mar  1 23:02 Pictures
drwx------  3 me   me       4096 Mar  2 07:07 .pki
drwxr-xr-x  2 me   me       4096 Mar  3 18:38 .steam
-rwx------  1 me   me       2209 Mar  3 18:38 steam.desktop
drwxr-xr-x  2 me   me       4096 Jan  5 09:55 Templates
drwxr-xr-x  2 me   me       4096 Mar  1 23:00 .themes
drwxr-xr-x  4 me   me       4096 Mar  1 23:13 .thumbnails
-rw-r--r--  1 root root 14680064 Oct  1  2014 TinyCore-5.4.iso
drwxr-xr-x  3 me   me       4096 Mar  4 06:19 .tor-browser-en
drwxr-xr-x  9 me   me       4096 Mar  4 08:59 Videos
-rw-r--r--  1 me   me         50 Jan  5 09:55 .vimrc
-rw-r--r--  1 me   me         50 Mar  4 09:15 .Xauthority
-rw-r--r--  1 me   me        261 Jan  5 09:55 .xinitrc
-rw-r--r--  1 me   me         99 Jan  5 09:55 .xsession
-rw-------  1 me   me    4732589 Mar  4 13:51 .xsession-errors
-rw-------  1 me   me    3043816 Mar  4 09:14 .xsession-errors.old
-rw-r--r--  1 me   me        104 Jan  5 09:55 .zprofile
-rw-r--r--  1 me   me        271 Jan  5 09:55 .zshrc
```
And when I open my file manager here without firejail I see the FooFooFoo file.

And now running it in firejail: I still see the FooFooFoo file.
```
$ firejail --list
9054:me:firejail --noprofile --overlay-tmpfs 
13594:me:firejail --overlay-tmpfs --noprofile 

```
EDIT: BTW you can use the join function to have more than one instance:
> Firejail Man snips

 --join-filesystem=name|pid
              Join the mount namespace of the sandbox identified  by  name  or
              PID.  By  default a /bin/bash shell is started after joining the
              sandbox.  If a program is specified, the program is run  in  the
              sandbox.  This command is available only to root user.  Security
              filters, cgroups and cpus configurations are not applied to  the
              process joining the sandbox.



---

### Post by &amp;KyT$0P# on 2017-03-04
I think I have still not made myself clear.

> **1fallen said:**
> And when I open my file manager here without firejail I see the FooFooFoo file.
:confused:
This shouldn't happen, and it doesn't happen for me.  Let's try again.

First, make sure Thunar is running **outside of firejail**.  And make sure there is **no "FooFooFoo" file in your home directory**.

Then, leaving Thunar open, run this command in a Terminal -
```
FIREJAIL_PROMPT=yes firejail --overlay-tmpfs --noprofile bash -c 'touch FooFooFoo;ls -la;Thunar'
```

What I'm looking for: A new instance (separate process) of Thunar opens in the firejail sandbox, and displays the home directory including the "FooFooFoo" file.

What actually happens: The Thunar command just makes the Thunar instance **outside the sandbox** open a new window.  Thus, no "FooFooFoo" file is displayed.

See now? :)

---

### Post by #&amp;thj^% on 2017-03-04
> **halogen2 said:**
> I think I have still not made myself clear.


:confused:
This shouldn't happen, and it doesn't happen for me.  Let's try again.

First, make sure Thunar is running **outside of firejail**.  And make sure there is **no "FooFooFoo" file in your home directory**.

Then, leaving Thunar open, run this command in a Terminal -
```
FIREJAIL_PROMPT=yes firejail --overlay-tmpfs --noprofile bash -c 'touch FooFooFoo;ls -la;Thunar'
```

What I'm looking for: A new instance (separate process) of Thunar opens in the firejail sandbox, and displays the home directory including the "FooFooFoo" file.

What actually happens: The Thunar command just makes the Thunar instance **outside the sandbox** open a new window.  Thus, no "FooFooFoo" file is displayed.

See now? :)

halogen2 Yes :smile: ... I was able to reproduce using the method you describe.
Funny thing is it shows with ls -la
```
$ FIREJAIL_PROMPT=yes firejail --overlay-tmpfs --noprofile bash -c 'touch FooFooFoo;ls -la;caja'
Parent pid 2604, child pid 2605
OverlayFS configured in /run/firejail/mnt directory
Warning: cannot mount /tmp/.X11-unix in overlay
Dropping all Linux capabilities and enforcing default seccomp filter
Warning: failed to unmount /sys
Warning: whitelist feature is disabled in overlay
Child process initialized
total 57436
drwx------  1 me   me         60 Mar  4 17:21 .
drwxr-xr-x  3 root root       60 Mar  4 17:21 ..
-rw-------  1 me   me       2240 Mar  4 16:30 .bash_history
-rw-r--r--  1 me   me         21 Jan 21 14:03 .bash_logout
-rw-r--r--  1 me   me         57 Jan 21 14:03 .bash_profile
-rw-r--r--  1 me   me        274 Mar  1 23:43 .bashrc
drwxr-xr-x 15 me   me       4096 Mar  4 13:53 .cache
drwxr-xr-x 37 me   me       4096 Mar  4 13:16 .config
drwxr-xr-x 33 me   me       4096 Mar  3 07:00 .conky
drwxr-xr-x  2 me   me       4096 Mar  4 12:00 Desktop
-rw-r--r--  1 me   me         43 Mar  2 00:18 .dmrc
drwxr-xr-x  4 me   me       4096 Mar  4 11:58 Documents
drwxr-xr-x  3 me   me       4096 Mar  4 17:03 Downloads
drwxr-xr-x  2 me   me       4096 Mar  4 08:28 .dreamchess
drwxr-xr-x  4 me   me       4096 Mar  2 10:23 .emerald
-rw-------  1 me   me         16 Mar  1 17:39 .esd_auth
drwxr-xr-x  3 me   me      12288 Mar  2 00:47 .fonts
-rw-r--r--  1 me   me          0 Mar  4 17:21 FooFooFoo
drwxr-xr-x 24 me   me       4096 Mar  4 13:55 .gimp-2.8
-rw-r-----  1 me   me          0 Mar  1 22:39 .gksu.lock
drwx------  3 me   me       4096 Mar  2 10:16 .gnome2
drwx------  3 me   me       4096 Mar  1 22:59 .gnupg
-rw-r--r--  1 me   me        122 Mar  2 07:34 .gtk-bookmarks
-rw-r--r--  1 me   me        607 Mar  1 23:08 .gtkrc-2.0
-rwxr-xr-x  1 root root      328 Mar  3 12:34 guidus.desktop
-rw-------  1 me   me       2178 Mar  4 09:15 .ICEauthority
drwxr-xr-x  2 me   me       4096 Mar  1 23:00 .icons
drwxr-xr-x  7 me   me       4096 Feb 27 19:58 .kodi
drwxr-xr-x  3 me   me       4096 Jan  5 09:55 .local
-rw-r--r--  1 root root     3389 Feb 11 15:25 md5sum.txt.asc
-rw-r--r--  1 root root 32505856 Oct  1  2014 mini.iso
-rw-r--r--  1 me   me      13607 Feb 11 15:23 mk_install-and-test-mkusb.bash
-rw-r--r--  1 me   me       4528 Oct  2  2014 mkusb-installer
-rwxr-xr-x  1 root root      516 Mar  3 12:34 mkusb-legacy.desktop
-rwxr-xr-x  1 root root      259 Mar  3 12:34 mkusb-legacy-root.desktop
drwx------  5 me   me       4096 Mar  1 22:45 .mozilla
drwxr-xr-x 14 me   me       4096 Mar  2 10:29 Music
drwx------  3 me   me       4096 Mar  1 18:33 .nv
-rw-r--r--  1 me   me       2149 Mar  3 19:01 .nvidia-settings-rc
drwxr-xr-x  6 me   me       4096 Mar  1 23:02 Pictures
drwx------  3 me   me       4096 Mar  2 07:07 .pki
drwxr-xr-x  2 me   me       4096 Mar  3 18:38 .steam
-rwx------  1 me   me       2209 Mar  3 18:38 steam.desktop
drwxr-xr-x  2 me   me       4096 Jan  5 09:55 Templates
drwxr-xr-x  2 me   me       4096 Mar  1 23:00 .themes
drwxr-xr-x  4 me   me       4096 Mar  1 23:13 .thumbnails
-rw-r--r--  1 root root 14680064 Oct  1  2014 TinyCore-5.4.iso
drwxr-xr-x  3 me   me       4096 Mar  4 06:19 .tor-browser-en
drwxr-xr-x  9 me   me       4096 Mar  4 08:59 Videos
-rw-r--r--  1 me   me         50 Jan  5 09:55 .vimrc
-rw-r--r--  1 me   me         50 Mar  4 09:15 .Xauthority
-rw-r--r--  1 me   me        261 Jan  5 09:55 .xinitrc
-rw-r--r--  1 me   me         99 Jan  5 09:55 .xsession
-rw-------  1 me   me    8335073 Mar  4 17:21 .xsession-errors
-rw-------  1 me   me    3043816 Mar  4 09:14 .xsession-errors.old
-rw-r--r--  1 me   me        104 Jan  5 09:55 .zprofile
-rw-r--r--  1 me   me        271 Jan  5 09:55 .zshrc

Parent is shutting down, bye...


```
Need to wrap my head around this for a bit.
Will report back.

---

### Post by #&amp;thj^% on 2017-03-05
See if this is to your liking:
```
$ touch FooFooFoo;FIREJAIL_PROMPT=yes firejail --overlay-tmpfs --noprofile bash -c 'ls -la;Thunar'
```
It now pops up with FooFooFoo visible in view.
Mine shows:
```
$ touch FooFooFoo;FIREJAIL_PROMPT=yes firejail --overlay-tmpfs --noprofile bash -c 'ls -la;caja'
Parent pid 15608, child pid 15609
OverlayFS configured in /run/firejail/mnt directory
Warning: cannot mount /tmp/.X11-unix in overlay
Dropping all Linux capabilities and enforcing default seccomp filter
Warning: failed to unmount /sys
Warning: whitelist feature is disabled in overlay
Child process initialized
total 62036
drwx------ 28 me   me       4096 Mar  4 21:55 .
drwxr-xr-x  3 root root       60 Mar  4 21:55 ..
-rw-------  1 me   me       3085 Mar  4 21:23 .bash_history
-rw-r--r--  1 me   me         21 Jan 21 14:03 .bash_logout
-rw-r--r--  1 me   me         57 Jan 21 14:03 .bash_profile
-rw-r--r--  1 me   me        274 Mar  1 23:43 .bashrc
drwxr-xr-x 15 me   me       4096 Mar  4 13:53 .cache
drwxr-xr-x 37 me   me       4096 Mar  4 20:50 .config
drwxr-xr-x 33 me   me       4096 Mar  3 07:00 .conky
drwxr-xr-x  2 me   me       4096 Mar  4 12:00 Desktop
-rw-r--r--  1 me   me         43 Mar  2 00:18 .dmrc
drwxr-xr-x  4 me   me       4096 Mar  4 19:45 Documents
drwxr-xr-x  3 me   me       4096 Mar  4 17:03 Downloads
drwxr-xr-x  2 me   me       4096 Mar  4 08:28 .dreamchess
drwxr-xr-x  4 me   me       4096 Mar  2 10:23 .emerald
-rw-------  1 me   me         16 Mar  1 17:39 .esd_auth
drwxr-xr-x  3 me   me      12288 Mar  2 00:47 .fonts
-rw-r--r--  1 me   me          0 Mar  4 21:55 FooFooFoo
drwxr-xr-x 24 me   me       4096 Mar  4 13:55 .gimp-2.8
-rw-r-----  1 me   me          0 Mar  1 22:39 .gksu.lock
drwx------  3 me   me       4096 Mar  2 10:16 .gnome2
drwx------  3 me   me       4096 Mar  1 22:59 .gnupg
-rw-r--r--  1 me   me        122 Mar  2 07:34 .gtk-bookmarks
-rw-r--r--  1 me   me        607 Mar  1 23:08 .gtkrc-2.0
-rwxr-xr-x  1 root root      328 Mar  3 12:34 guidus.desktop
-rw-------  1 me   me       2178 Mar  4 09:15 .ICEauthority
drwxr-xr-x  2 me   me       4096 Mar  1 23:00 .icons
drwxr-xr-x  7 me   me       4096 Feb 27 19:58 .kodi
drwxr-xr-x  3 me   me       4096 Jan  5 09:55 .local
-rw-r--r--  1 root root     3389 Feb 11 15:25 md5sum.txt.asc
-rw-r--r--  1 root root 32505856 Oct  1  2014 mini.iso
-rw-r--r--  1 me   me      13607 Feb 11 15:23 mk_install-and-test-mkusb.bash
-rw-r--r--  1 me   me       4528 Oct  2  2014 mkusb-installer
-rwxr-xr-x  1 root root      516 Mar  3 12:34 mkusb-legacy.desktop
-rwxr-xr-x  1 root root      259 Mar  3 12:34 mkusb-legacy-root.desktop
drwx------  5 me   me       4096 Mar  1 22:45 .mozilla
drwxr-xr-x 14 me   me       4096 Mar  2 10:29 Music
drwx------  3 me   me       4096 Mar  1 18:33 .nv
-rw-r--r--  1 me   me       2149 Mar  4 20:50 .nvidia-settings-rc
drwxr-xr-x  6 me   me       4096 Mar  1 23:02 Pictures
drwx------  3 me   me       4096 Mar  2 07:07 .pki
drwxr-xr-x  2 me   me       4096 Mar  3 18:38 .steam
-rwx------  1 me   me       2209 Mar  3 18:38 steam.desktop
drwxr-xr-x  2 me   me       4096 Jan  5 09:55 Templates
drwxr-xr-x  2 me   me       4096 Mar  1 23:00 .themes
drwxr-xr-x  4 me   me       4096 Mar  1 23:13 .thumbnails
-rw-r--r--  1 root root 14680064 Oct  1  2014 TinyCore-5.4.iso
drwxr-xr-x  3 me   me       4096 Mar  4 06:19 .tor-browser-en
drwxr-xr-x  9 me   me       4096 Mar  4 08:59 Videos
-rw-r--r--  1 me   me         50 Jan  5 09:55 .vimrc
-rw-r--r--  1 me   me         50 Mar  4 09:15 .Xauthority
-rw-r--r--  1 me   me        261 Jan  5 09:55 .xinitrc
-rw-r--r--  1 me   me         99 Jan  5 09:55 .xsession
-rw-------  1 me   me   13041053 Mar  4 21:55 .xsession-errors
-rw-------  1 me   me    3043816 Mar  4 09:14 .xsession-errors.old
-rw-r--r--  1 me   me        104 Jan  5 09:55 .zprofile
-rw-r--r--  1 me   me        271 Jan  5 09:55 .zshrc

Parent is shutting down, bye...
```
Screenshot also.

---

### Post by &amp;KyT$0P# on 2017-03-05
Err, 1fallen, the goal is not just to see an empty file named "FooFooFoo" listed in Thunar. :)

I would like to run a Thunar window **inside the firejail sandbox**.  While **also** running Thunar **outside** the sandbox.

This likely is more of a Thunar question than a firejail question, I reckon.

---

### Post by #&amp;thj^% on 2017-03-05
I Cant read minds here::P
This will work then...or should, it dose for me.
```
firejail touch FooFooFoo;FIREJAIL_PROMPT=yes firejail --overlay-tmpfs --noprofile bash -c 'ls -la';firejail Thunar
```
Also worth noting here is I call the code within a "sandboxed xterm"...they have quite a few of the terminal apps blacklisted by default.
Any way here is my sandbox list after the command from above:
```
[me@me-pc ~]$ firejail --list
28374:me:firejail xterm 

```
Ok I must be tired...just reread your post's again and noticed this:
> What I'm looking for: A new instance (separate process) of Thunar opens  in the firejail sandbox, and displays the home directory including the  "FooFooFoo" file.
There are you happy now...;)
Going to bed now [Good Nite John Boy]("https://www.youtube.com/watch?v=cp7_u0kcQRo").

---

### Post by #&amp;thj^% on 2017-03-05
Ok.. Big apology here :oops:...fired up Xubuntu...issued my commands in my last post#10
and Yep your right Thunar seems to fall out of the sandbox.:confused:
This even calling just Thunar IE: 'firejail Thunar'... file opens alright.. but not listed in the sandbox???
Now I'm not sure if it is indeed outside of the sandbox for sure.
But I know pcmanfm works as expected.
So to summarize: 
```
firejail touch FooFooFoo;FIREJAIL_PROMPT=yes firejail --overlay-tmpfs --noprofile bash -c 'ls -la';firejail pcmanfm
```
And after entering the code above.. the expected results are there.
Also shows in the sandbox:
```
$ firejail --list
24783:me:firejail pcmanfm 

```
So there you have it...just need to decide if you want to install another/extra FM
I have had good results with PcmanFM on a XFCE4 session.(just my 2 cents worth.)
I'm trying to get in touch with "netblue" to see if he can shed some more thought here.
Regards

---

### Post by &amp;KyT$0P# on 2017-03-05
Thanks 1fallen. :)

I did try installing PCManFM, which works well for this in Lubuntu 14.04.  And as long as PCManFM isn't using an already-running profile, it works great.  But I was hoping to avoid continuing the '*Oh, let's use Konqueror for this, PCManFM for that, oh and Thunar for this one thing, and...*' routine I've got going in Lubuntu 14.04.

> I'm trying to get in touch with "netblue" to see if he can shed some more thought here.
Is this discussion publicly viewable?

---

### Post by #&amp;thj^% on 2017-03-05
> **halogen2 said:**
> Thanks 1fallen. :)

I did try installing PCManFM, which works well for this in Lubuntu 14.04.  And as long as PCManFM isn't using an already-running profile, it works great.  But I was hoping to avoid continuing the '*Oh, let's use Konqueror for this, PCManFM for that, oh and Thunar for this one thing, and...*' routine I've got going in Lubuntu 14.04.

I totally get that..:D
> **halogen2 said:**
> 
Is this discussion publicly viewable?
Email so far...sounds like he might be a bit busy ATM
> Running **ls /etc/firejail/*.profile** will list all the security profiles distributed with Firejail. _Programs not listed there, are handled by a very restrictive /etc/firejail/default.profile_.
So I guess we have to read between the lines for now.
I will for sure point him to this thread though.

---

### Post by #&amp;thj^% on 2017-03-05
Well see if you can work with this, it's not very elegant but she works.(For Me at least)
Firstly lets make sure we have Firejail set-up...  run the following commands which makes all possible changes so that all users on your system will use Firejail with installed programs for which Firejail has a profile. Enter your password and hit enter.
```
sudo firecfg
```

Second run the following command which fixes any programs that have an incompatible menu launcher. You will need to run this command for every user.
```
firecfg --fix
```

If you install additional programs in the future for which there is a Firejail profile _you will have to re-run both of these commands._


Now on with the grind:
Same as before open Thunar as regular (non-sandboxed).
Now open "Top"...find the PID of the open Thunar.
Now we join it.
```
firejail --join=**"PIDofthunar"** touch FooFooFoo;FIREJAIL_PROMPT=yes firejail --overlay-tmpfs --noprofile bash -c 'ls -la';firejail --join=**"PIDofthunar"**
```
Replace **"PIDofthunar"** with **just the PID-number** given from top && without the quotes.
Now Check with:
```
firejail --tree
```
This even works with caja...showing the same behavior as thunar here.
```
$ firejail --tree
15330:me:firejail --join=13348 
  15331:me:/bin/bash 
25783:me:firejail seamonkey 
  25784:me:firejail seamonkey 
    25790:me:seamonkey 

```
I tried creating a profile for it ...but it got ugly ](*,)...so simpler was better,  for me at least. :)

---

### Post by &amp;KyT$0P# on 2017-03-06
Nope.  I'm not interested in putting *everything* in firejail sandboxes.  Best we let [FONT=Courier New]firecfg[/FONT] be.

The existing Thunar instance isn't sandboxed, and shouldn't be.  Thus, this part...
```
firejail --join="PIDofthunar" touch FooFooFoo;
```
... just creates a "FooFooFoo" file on the main filesystem.  Which defeats the purpose of creating the "FooFooFoo" file as a test.


I'll re-phrase my question again.  If I have Thunar already running, and an existing [FONT=Courier New]firejail --overlay-tmpfs[/FONT] sandbox -
```
firejail --noprofile --overlay-tmpfs
```

How to get these results, but using Thunar instead of PCManFM?
```
$ firejail --tree
3889:*******:firejail --noprofile --overlay-tmpfs
  3890:*******:firejail --noprofile --overlay-tmpfs
    3892:*******:/bin/bash
      3953:*******:pcmanfm

```

```
$ firejail --tree
3889:*******:firejail --noprofile --overlay-tmpfs
  3890:*******:firejail --noprofile --overlay-tmpfs
    3892:*******:/bin/bash
3931:*******:firejail --join=3889 pcmanfm
  3932:*******:pcmanfm

```


Now, interestingly, Thunar doesn't "jump the sandbox" if I run it like this -
```
$ Thunar --daemon
```
But it doesn't open any window that way.

Also, this command seems to get it working -
```
Thunar -q
```

I don't know what all that means?

---

### Post by &amp;KyT$0P# on 2017-03-06
> **halogen2 said:**
> Now, interestingly, Thunar doesn't "jump the sandbox" if I run it like this -
```
$ Thunar --daemon
```
But it doesn't open any window that way.

Also, this command seems to get it working -
```
Thunar -q
```

I don't know what all that means?
Note to self: try not to post random findings when too tired to think of doing proper searching about them. :P

Thanks again to 1fallen - who, by being unable to reproduce the problem with Thunar except in Xubuntu, really helped me discover the above. :KS

Anyway, I did some more research.  It seems that the problem of a running Thunar daemon eating every Thunar command is quite common.  But there are some related things I'm not finding any info about.

1) So I discovered it's possible to have multiple Thunar daemons running concurrently.  Is it possible to choose which Thunar daemon gets to eat any given Thunar command?  Or is this locked to the first Thunar daemon?

2) If I decide to just go with disabling the Thunar daemon.  I know that, then, every new Thunar instance would remain a separate process.  Which is a drawback in terms of speed and RAM usage.  Would I lose out on anything else?

3) In xfdesktop, when right-click something > Properties, it starts a Thunar daemon.  Can it be configured to start a regular Thunar instead?

---

### Post by #&amp;thj^% on 2017-03-07
> **halogen2 said:**
> Note to self: try not to post random findings when too tired to think of doing proper searching about them. :P

We have all done this at one time.:D
> **halogen2 said:**
> 
1) So I discovered it's possible to have multiple Thunar daemons running concurrently. Is it possible to choose which Thunar daemon gets to eat any given Thunar command? Or is this locked to the first Thunar daemon?


This is just my suggestion/opinion, but I like the join function, to choose which PID I want to sandbox.
Forgive me if I over explain here.;)
I like to use more specific use...Example:
For just Thunar> I find the PID with:
```
ps -C Thunar -o pid=
```
It will show in my case as "668"
So a just a basic use here, I join that PID:
```
firejail --join=668
```
So I now have just a sanboxed Thunar...Not a Daemon.
In a more general way, the command format is as follows:
 ```
 firejail  [options] program_and_arguments --join=PID
```

Without any arguments, Firejail starts a regular /bin/bash shell. Only the bash session and its descendants are visible inside the sandbox.

Now Thunar and Caja will not show in the firejail --tree **"in name"** (Like pcmanfm did) but only list's the PID for Thunar...Like mine here:
```
firejail --tree
9369:me:firejail join=668
  9370:me:/bin/bash
```
Hope that was useful...And you can use your {Options && Arguments} as you need to..or allowed.
> **halogen2 said:**
> 
2) If I decide to just go with disabling the Thunar daemon. I know that, then, every new Thunar instance would remain a separate process. Which is a drawback in terms of speed and RAM usage. Would I lose out on anything else?

First see how the join PID function works out for ya... I notice so very little difference with my use that it's hardly worth a mention.(Resource and Mem) 
> Would I lose out on anything else?
Probably not what you were asking for.. but still worth a mention here: when you use the **"--private"** mode...if you do not save or move anything you did or downloaded or any other object needed in **"./temp" **That will be lost.  
So Long story short...I you don't save before closing the session, it will be lost.
> **halogen2 said:**
> 
3) In xfdesktop, when right-click something > Properties, it starts a Thunar daemon. Can it be configured to start a regular Thunar instead?

I'm not real clear on your use here...but maybe the above may help..

And to open just a un-jailed Thunar...I just go to the menu and open it from there.
halogen2 I do somewhat know how you feel though...can be a real mind-bogler..:D
The more you play with with it...the more familiar it becomes.
You can speak or inquiry netblue30 here also: [https://firejail.wordpress.com/documentation-2/firefox-guide/](https://firejail.wordpress.com/documentation-2/firefox-guide/)
Best Regards

---

### Post by &amp;KyT$0P# on 2017-03-07
> **1fallen said:**
> Hope that was useful..
That is quite useful for me, thanks! :D
Although not so much for this.

Those firejail commands are the reverse of what I'm trying to do.  They join a firejail into a Thunar, instead of joining a Thunar into a firejail.

> I'm not real clear on your use here...
Yeah, sorry, that wasn't the greatest explanation.

So I quit Thunar -
```
Thunar -q
```
... then verify that it isn't running.
```
$ ps -C thunar,Thunar -o pid,command
  PID COMMAND
```

My XFCE desktop on that system has 3 items: File System, Home, and Trash.  Right-click one of them > Properties.  Close the properties window.

Check again for running Thunars, and I end up with this -
```
$ ps -C thunar,Thunar -o pid,command
  PID COMMAND
 3351 /usr/bin/Thunar --daemon
```

Note the [FONT=Courier New]--daemon[/FONT] switch.  Question is, can that be removed?

---

### Post by #&amp;thj^% on 2017-03-07
> **halogen2 said:**
> That is quite useful for me, thanks! :D
Although not so much for this.

Those firejail commands are the reverse of what I'm trying to do.  They join a firejail into a Thunar, instead of joining a Thunar into a firejail.


No...it opens Thunar by way of "PID"
I'm not following This though?:
```
ps -C thunar,Thunar -o pid,command
```
Maybe I lost you in my example. I just open Thunar>>Then open Terminal and issue:
This exact code:
```
ps -C Thunar -o pid=
```
It then shows 2 Lines Returned...The bottom number is the PID I use to join (or open) with.  See what I'm hinting at, Just Thunar and not the daemon... and not really joining but opening a new Box.
Example:
```
[me@me-pc ~]$ ps -C mate-session -o pid=
 2423
[me@me-pc ~]$ ps -C caja -o pid=
 2476

```

 >>Then I use other Options/Aurguments/Names
From "man firejail"
> Firejail Man snips

--join-filesystem=name|pid
Join the mount namespace of the sandbox identified by name or
PID. By default a /bin/bash shell is started after joining the
sandbox. If a program is specified, the program is run in the
sandbox. This command is available only to root user. Security
filters, cgroups and cpus configurations are not applied to the
process joining the sandbox.
Just keep in mind here Thunar is not a supported profile so you have to use the "PID" and not the "Program Name IE:Thunar"
I know I'm repeating the same information...just trying to keep it clear is all.:D
> **halogen2 said:**
> 
Note the --daemon switch. Question is, can that be removed?

I would be curious to see if that changes...using my method.
You will find the code you enter..to be a trial and error thing for a short time.;)

---

### Post by &amp;KyT$0P# on 2017-03-07
> **1fallen said:**
> I'm not following This though?:
```
ps -C thunar,Thunar -o pid,command
```
It gets all processes named "Thunar" or "thunar", and print both their PIDs and full commands.
```
$ ps -C thunar,Thunar -o pid,command
  PID COMMAND
 2144 Thunar --sm-client-id ((snipped)) --daemon
```
Then, as you suggested, I put the PID in firejail -
```
$ FIREJAIL_PROMPT=yes firejail --join=2144
changing root to /proc/2144/root
Child process initialized
```
But...again...it's the opposite of what I'm trying to do.
```
[COLOR="#FF0000"]**2794**[/COLOR]:xxxxxxx:firejail --noprofile --overlay-tmpfs
  2795:xxxxxxx:firejail --noprofile --overlay-tmpfs
    2797:xxxxxxx:/bin/bash
2824:xxxxxxx:firejail --join=[COLOR="#FF0000"]**2144**[/COLOR]
  2825:xxxxxxx:/bin/bash
```

This is the goal -
```
$ firejail --tree
[COLOR="#FF0000"]**2882**[/COLOR]:xxxxxxx:firejail --noprofile --overlay-tmpfs
  2883:xxxxxxx:firejail --noprofile --overlay-tmpfs
    2885:xxxxxxx:/bin/bash
2914:xxxxxxx:firejail --join=[COLOR="#FF0000"]**2882**[/COLOR] Thunar
  2915:xxxxxxx:Thunar

```


> I would be curious to see if that changes...using my method.
That part doesn't, and shouldn't, involve firejail at all.

---

### Post by #&amp;thj^% on 2017-03-08
> **halogen2 said:**
> 
That part doesn't, and shouldn't, involve firejail at all.
I think we are talking past each other now.:)
Yes indeed you are right....But I was refering to the "Note the --daemon switch. Question is, can that be removed?"
No big thing though.
Can I point out that "netblue" has pointed to me that this:
> This is the goal -:
```
$ firejail --tree
[COLOR=#ff0000]This is firejail as root-->[2882][/COLOR]:xxxxxxx:firejail --noprofile --overlay-tmpfs
  2883:xxxxxxx:firejail --noprofile --overlay-tmpfs
    2885:xxxxxxx:/bin/bash
2914:xxxxxxx:firejail --join=[COLOR=#ff0000][2882][/COLOR] Thunar[COLOR=#ff0000]<--This is program running as user. [/COLOR]
  2915:xxxxxxx:Thunar
```
  So you see that can't be. (To add clarity the same PID's)


Sounds like you need "netblues" skill level..  I provided a link earlier:  [https://firejail.wordpress.com/docum...firefox-guide/](https://firejail.wordpress.com/docum...firefox-guide/)
Scroll to bottom and make any respectful inquiry.
Sorry I was not more helpful.

---

### Post by &amp;KyT$0P# on 2017-03-08
Thank you 1fallen for all your effort to help. :KS

---

### Post by &amp;KyT$0P# on 2017-03-29
Update: I'm noticing some instability in Thunar (unrelated to this), so I have installed PCManFM anyway, which solves this issue for me.

---

