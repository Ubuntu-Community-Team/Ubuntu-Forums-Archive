---
title: "Pulling my hair out over mpd/gmpc"
date: 2009-05-27
forum: General Help
---

### Post by The Switch Blade on 2009-05-27
```
apt-get install mpd gmpc
``` worked, but then when I edited the ```
/etc/mpd.conf
``` file to put my /media/Storage/Music folder as the directory as per the tutorial, things broke. So I found this tutorial:

[http://ubuntuforums.org/showthread.php?t=31763](http://ubuntuforums.org/showthread.php?t=31763)

So I tried uninstalling mpd and gmpc, but it wouldn't let me. After restarting and trying to uninstall and reinstall again, it says I have a broken package (libao2) and I get this error:

> E: mpd: subprocess post-installation script returned error exit status 2What do I do?!??!

---

### Post by maheshasolkar on 2009-05-27
Since you have broken packages, first thing you should do is fix them:

  [https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages](https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages)

Then I would try to run mpd with a minimal mpd.conf. Starting with a simple mpd.conf file in your home directory, for example (/home/you/mpd.conf):

```
port                    "6600"
music_directory         "/media/Storage/Music"
playlist_directory      "/home/you/mpd/playlists"
db_file                 "/home/you/mpd/mpd.db"
log_file                "/home/you/mpd/mpd.log"
error_file              "/home/you/mpd/mpd.error"

```

Try to run mpd on the command line:

```
  % mpd /home/you/mpd.conf
```

Check if there are any errors. There may be some clue.

---

### Post by The Switch Blade on 2009-05-27
Basically the same error as before (when I first started)

** ERROR **: problems opening file /home/earl/mpd.conf for reading: No such file or directory

---

### Post by mcduck on 2009-05-27
Another, and very easy option, is to leave the mpd.conf as it is by default, and instead just symlink your music directory into MPD's default directory. (Of course also let MPD run as system service which is pretty much the main idea of using MPD in the first place).

If you do it this way you shouldn't really need to do anything else than install MPD & client packages and create the link. 

**mcduck's 3-step guide to MPD:**
```

sudo apt-get install mpd mpc ncmpc sonata
sudo ln -s /path/to/your/music /var/lib/mpd/music
mpc update
```

---

### Post by maheshasolkar on 2009-05-27
> **The Switch Blade said:**
> Basically the same error as before (when I first started)

** ERROR **: problems opening file /home/earl/mpd.conf for reading: No such file or directory

Well, that means /home/earl/mpd.conf does not exist. Can you list that file:

```
  ls /home/earl/mpd.conf
```

---

### Post by The Switch Blade on 2009-05-27
ls: cannot access /home/earl/mpd.conf: No such file or directory

also

mpd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mpd (0.14.2-3ubuntu2) ...
 * Starting Music Player Daemon mpd                                              * /etc/mpd.conf must have db_file and pid_file set; cannot start daemon.
invoke-rc.d: initscript mpd, action "start" failed.
dpkg: error processing mpd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by The Switch Blade on 2009-05-27
> **mcduck said:**
> Another, and very easy option, is to leave the mpd.conf as it is by default, and instead just symlink your music directory into MPD's default directory. (Of course also let MPD run as system service which is pretty much the main idea of using MPD in the first place).

If you do it this way you shouldn't really need to do anything else than install MPD & client packages and create the link. 

**mcduck's 3-step guide to MPD:**
```

sudo apt-get install mpd mpc ncmpc sonata
sudo ln -s /path/to/your/music /var/lib/mpd/music
mpc update
```
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Errors were encountered while processing:
 mpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
earl@earl-desktop:~$ sudo ln -s /media/Storage/Music /var/lib/mpd/music
earl@earl-desktop:~$ mpd update

** ERROR **: problems opening file update for reading: No such file or directory

aborting...
Aborted

---

### Post by The Switch Blade on 2009-05-27
oh, mpc update doesn't work either

earl@earl-desktop:~$ sudo mpc update
MPD_HOST and/or MPD_PORT environment variables are not set
error: problems connecting to "localhost" on port 6600: Connection refused

---

### Post by maheshasolkar on 2009-05-27
It is:

```
  % mpc update
```

---

### Post by The Switch Blade on 2009-05-27
earl@earl-desktop:~$ sudo dpkg-reconfigure mpd
/usr/sbin/dpkg-reconfigure: mpd is broken or not fully installed

---

### Post by maheshasolkar on 2009-05-27
> **The Switch Blade said:**
> ls: cannot access /home/earl/mpd.conf: No such file or directory



The mpd.conf file does not exist. Can you create a new mpd.conf file:

```
  % touch /home/earl/mpd.conf
```

Edit it:

```
  % gedit /home/earl/mpd.conf
```

And add the following content in it:

```
port                    "6600"
music_directory         "/media/Storage/Music"
playlist_directory      "/home/you/mpd/playlists"
db_file                 "/home/you/mpd/mpd.db"
log_file                "/home/you/mpd/mpd.log"
error_file              "/home/you/mpd/mpd.error"
```

Then run:

```
  % mpd /home/you/mpd.conf
```

---

### Post by maheshasolkar on 2009-05-27
> **The Switch Blade said:**
> earl@earl-desktop:~$ sudo dpkg-reconfigure mpd
/usr/sbin/dpkg-reconfigure: mpd is broken or not fully installed

I would again fix the broken packages first:

  [https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages](https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages)

---

### Post by mcduck on 2009-05-27
> **The Switch Blade said:**
> oh, mpc update doesn't work either

earl@earl-desktop:~$ sudo mpc update
MPD_HOST and/or MPD_PORT environment variables are not set
error: problems connecting to "localhost" on port 6600: Connection refused
Those commands work great assuming that you start with no MPD installed, or with farily close to default MPD configuration. As you have already installed MPD, and changed it's configurations, you'll need to undo your own changes to get MPD back to default setup.

When you have returned MPD's config to defaults you just need to create the link. 

(And always when following any guide it's pointless to continue if some step fails. If installing some package fails it's not likely that any of the following steps would still work :D)

---

### Post by The Switch Blade on 2009-05-27
earl@earl-desktop:~$ mpd /home/earl/mpd.conf
problem opening log file "/home/earl/mpd/mpd.log" (config line 5) for writing
Aborted

---

### Post by The Switch Blade on 2009-05-27
> **maheshasolkar said:**
> I would again fix the broken packages first:

  [https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages](https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages)
When I went to do that, it doesn't ungrey apply marked changes. :???:

---

### Post by The Switch Blade on 2009-05-27
Why doesn't mpd allow you to just uninstall everything and start from scratch? This is really aggravating...

---

### Post by mcduck on 2009-05-27
> **The Switch Blade said:**
> Why doesn't mpd allow you to just uninstall everything and start from scratch? This is really aggravating...

It's not MPD's job to do that. Package manager handles that kind of stuff. :)

If you wan to start from scratch, "sudo apt-get purge mpd" will remove MPD and it's system-wide configurations. You'll have to remove the configs you have created in your home directory yourself (although the default setup won't ever even use config files from user's home directories).

Then let the MPD run as system service, that's how you get most out of it (that's why it's called music player *daemon*). You don't ever need to start mpd yourself, it will start automatically on boot, and the default configurations work fine unless you wish to change some small details like audio output or character set settings.

---

### Post by The Switch Blade on 2009-05-27
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mpd*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 508kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 152922 files and directories currently installed.)
Removing mpd ...
 * /etc/mpd.conf must have pid_file set; cannot stop daemon.
invoke-rc.d: initscript mpd, action "stop" failed.
dpkg: error processing mpd (--purge):
 subprocess pre-removal script returned error exit status 1
action: abort-remove not supported
Errors were encountered while processing:
 mpd
E: Sub-process /usr/bin/dpkg returned an error code (1)


I'm about to switch back to windows... :X

---

### Post by mcduck on 2009-05-28
> **The Switch Blade said:**
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  mpd*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 508kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 152922 files and directories currently installed.)
Removing mpd ...
 * /etc/mpd.conf must have pid_file set; cannot stop daemon.
invoke-rc.d: initscript mpd, action "stop" failed.
dpkg: error processing mpd (--purge):
 subprocess pre-removal script returned error exit status 1
action: abort-remove not supported
Errors were encountered while processing:
 mpd
E: Sub-process /usr/bin/dpkg returned an error code (1)


I'm about to switch back to windows... :X
First, have you tried fixing the issue with the broken package? Somebody suggested that in the first reply to this thread and you really need to fix package install issues before even trying to do anything else.

Really, every time you follow any guide, or actually try to do anything, if get an error you should stop, fix that error, and only after that continue with whatever you were doing.

---

### Post by spyrosebastos on 2009-05-29
I have the same broken repositories problem the thread starter has.  Maheshalkar, or anyone have any suggestions for, if after** Edit> fix broken packages** the **apply marked changes** isn't highlighted and cannot be selected?

mpd is ok, db just created.

Edit:
or do I just have to select the broken packages b4 applying? no, no...

...synaptec isn't identifying mpd-dbg as broken *FIXED*

---

