---
title: "Precise new install -- dash &amp; hud show nothing"
date: 2012-04-08
forum: Desktop Environments
---

### Post by shadowfirebird on 2012-04-08
**EDIT: *Of course*, I figured it out five minutes after posting.  There is lots of bugginess going on here, but the root cause is a home directory that was a carry on from 11.04.  With a fresh $HOME, it works.**


**TL;DR version: **
After a new install of 12.04 final beta, everything seems to work except the Dash and the HUD.  Both appear on command but contain no data.  (So, typing "terminal" into the Dash, for example, brings up nothing.)   

Can anyone tell me what I need to do to get better information about what is happening?   


**Details:**
I've just installed the 12.04 final beta.   It did not really go very smoothly.  However, at third try and after no special fiddling from me, everything appears to work now except the Dash and the HUD.   Not having the Dash, as you can imagine, is very nearly a show stopper.

I've tried reinstalling unity-lens-*.  No change.

I've seen people recommending that you delete ~/.cache/software-center.   There is no such directory in my $HOME.

I've tried 'unity --reload &', which didn't help but did allow me to see a number of interesting error messages:

```
Initializing unityshell options...done
compiz (core) - Warn: unhandled ConfigureNotify on 0x180009e!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x18000a1!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x18000a1!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x18000a4!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x18000a7!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
compiz (core) - Warn: unhandled ConfigureNotify on 0x18000aa!
compiz (core) - Warn: this should never happen. you should probably file a bug about this.
WARN  2012-04-08 11:04:32 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/firefox.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-04-08 11:04:32 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-writer.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-04-08 11:04:32 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-calc.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-04-08 11:04:32 unity.libindicator <unknown>:0 Desktop file '/usr/share/applications/libreoffice-impress.desktop' is using a deprecated format for its actions that will be dropped soon.
WARN  2012-04-08 11:04:33 unity.launcher Launcher.cpp:2991 Object registration failed. Won't get dynamic launcher addition.
WARN  2012-04-08 11:04:33 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window48268348: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window48268348
WARN  2012-04-08 11:04:33 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window48268362: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window48268362
WARN  2012-04-08 11:04:33 unity <unknown>:0 Failed to fetch view type at /org/ayatana/bamf/window48268376: No such interface `org.ayatana.bamf.view' on object at path /org/ayatana/bamf/window48268376
Initializing staticswitcher options...done
Setting Update "main_menu_key"
Setting Update "run_key"
WARN  2012-04-08 11:04:39 unity.glib.dbusproxy GLibDBusProxy.cpp:182 Unable to connect to proxy: Error calling StartServiceByName for net.launchpad.lens.video: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/unity-lens-video/unity-lens-video exited with status 1

```

The "unhandled configurenotify" thing looks to be a long standing bug, [#877505]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/877505"). Might be nothing to do with this(?).

It looks as if someone else had exactly this problem with 11.10 about six months ago, but no-one was able to help him -- see [this]("http://ubuntuforums.org/showthread.php?p=11472173").

---

### Post by r_mano on 2012-04-30
Well --- wiping my HOME is not an answer, I suppose. What should I remove to have dash working again?

---

### Post by shadowfirebird on 2012-04-30
It's the hidden files and directories that begin with a . (dot)

If I were you I would backup your entire $HOME to ${HOME}_old and then remove all the config files in $HOME.  You can always move some of them back piece by piece after you're sure you've fixed the problem.

So, my login name is andy, and I would:

```
sudo rsync -aP /home/andy home/andy_old
rm $HOME/.[a-zA-Z]*
```

There is probably a more elegant way to do that.  Also, untested; make sure the first step really did back up all your $HOME before you do the second.

---

### Post by r_mano on 2012-04-30
Well --- thanks, I was thinking doing it, but then I solved it as specified by Vinay in [https://bugs.launchpad.net/unity/+bug/987689](https://bugs.launchpad.net/unity/+bug/987689). 

Basically

apt-get remove -purge unity-lens-applications
apt-get remove -purge unity-lens-music
apt-get remove -purge unity-lens-files

and then reinstall them 
apt-get install unity-lens-applications unity-lens-music unity-lens-files

and in the middle I wiped the $HOME/.cache directory. Then restart with 

unity --reset

logout and login and now it seems to work again.

---

### Post by Akhnatoun on 2012-05-01
> **r_mano said:**
> Well --- thanks, I was thinking doing it, but then I solved it as specified by Vinay in [https://bugs.launchpad.net/unity/+bug/987689](https://bugs.launchpad.net/unity/+bug/987689). 

Basically

apt-get remove -purge unity-lens-applications
apt-get remove -purge unity-lens-music
apt-get remove -purge unity-lens-files

and then reinstall them 
apt-get install unity-lens-applications unity-lens-music unity-lens-files

and in the middle I wiped the $HOME/.cache directory. Then restart with 

unity --reset

logout and login and now it seems to work again.

Thanks for these instruction, but it didn't work in my case.
may because I got a different error which is related to unity-lens-video, although I followed the above method and purged both unity-lens-applications, music, files an videos, but i still have the same problem after unity reset and reboot.

---

### Post by Koura on 2012-05-03
I upgraded from 11.04 to 12.04 and found that Dash did not work in my "user" account but did work as "guest".

I then did a fresh install and , from my Home backup, copied only my personal folders to the new Home folder. No hidden files were copied other than my Thunderbird profile. Having done this Dash seems to be working O.K.

---

### Post by colin.p on 2012-05-06
> **shadowfirebird said:**
> It's the hidden files and directories that begin with a . (dot)

If I were you I would backup your entire $HOME to ${HOME}_old and then remove all the config files in $HOME.  You can always move some of them back piece by piece after you're sure you've fixed the problem.

So, my login name is andy, and I would:

```
sudo rsync -aP /home/andy home/andy_old
rm $HOME/.[a-zA-Z]*
```

There is probably a more elegant way to do that.  Also, untested; make sure the first step really did back up all your $HOME before you do the second.

Thanks, that was the simplist answer. Actually I should have known, I did read quite awhile ago that a fresh install with a saved "Home" directory, should have the ".files" removed. It was never an issue before, but now it is. I removed all of them except thunderbird and now HUD works (quite well actually). I will add what I need back when the coresponding app gets installed.

---

