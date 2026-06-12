---
title: "Firefox local file operations fail"
date: 2010-08-03
forum: Desktop Environments
---

### Post by TheLancashireman on 2010-08-03
Since I upgraded to 10.4 last week (in 2 steps from jaunty) Firefox has been behaving strangely. It refuses to open some directories. Among the affected parts are:

 - print to file (fails silently)
 - save page as (fails with an error dialog "...because you cannot change the contents of that folder".)
 - create a folder from the file/open dialog or similar (fails with an error dialog "Permission denied".)
 - upload a file to a website - not sure how - might be some javascript (fails silently, the uploaded file is empty)
 - the jpg file viewer also refuses to save.

If the destination is in my home directory there's no problem. There's also no problem saving or whatever into a directory in someone else's home directory where I have write permission. One place it doesn't work is on my 2nd (data) disk, which is an ext4 file system mounted at /data. I have all the necessary read and write permissions there - from a shell I can create the directories that firefox says I have no permission for, and if I save or create a file in $HOME from firefox I can move it to the place I want it from the shell too. At first I thought it might be an ext4 thing, so I created a new directory (as root) called /wizz and made myself owner of it and gave myself rwx permissions. I can create files and subdirectories there from the shell, but not from firefox. My / filesystem is reiserfs. My /home filesystem is also reiserfs.

I'm totally confused.....

System is Lucid 10.4 64-bit fully patched. I'm using the blackbox window manager, if that makes any difference.

Oh, and other programs such as ooffice have no trouble saving or loading files from the places where firefox fails, although I haven't tried everything, of course.

Everything was working fine before the upgrade.

I tried starting with a fresh profile, as that seems to have fixed some strange problems for other people, but that made no difference.

Any ideas, anyone?

---

### Post by lovinglinux on 2010-08-03
Create a new Ubuntu user just for testing, login with that account and test Firefox. The reason to do that is so we can exclude your user settings as culprit. Since you have already created a new Firefox profile and it didn't work, the next logical step would be to test another user account. If it works, then you probably have some gnome settings from Jaunty that are not playing well with Firefox. If it exhibits the same problems, then you might have issues with Firefox installation or the system itself.

---

### Post by TheLancashireman on 2010-08-04
OK - I tried that. The new user has exactly the same problem - at least in the test directory /wizz, which I changed to be owned by the new user just for the test.

So I have now ruled out:
 - filesystem permissions (I can create the files and directories from other programs (shell, openoffice, gimp)
 - filesystem type (does the same for ext4 and reiserfs, problem doesn't happen on /home, which is also reiserfs)
 - some kind of strangeness about leftover gnome settings (although why that should prevent firefox from accessing files beats me)

Any more ideas?

---

### Post by lovinglinux on 2010-08-04
> **TheLancashireman said:**
> Any more ideas?

Create a symlink on your home, pointing to the problematic folder and check if you can save the files.

---

### Post by TheLancashireman on 2010-08-04
OK - I tried that.  Still "Permission denied" when trying to create a directory from the file chooser dialog in print-to-file. I assume all other save/write operations will be the same.

---

### Post by TheLancashireman on 2010-08-04
I also tried deinstalling firefox (which removed 4 packages) and reinstalling (which only installed 2). No change.

---

### Post by lovinglinux on 2010-08-04
I would suggest to change the problematic directory ownership to you, but I guess you already have done that.

---

### Post by TheLancashireman on 2010-08-04
The problem directories are all owned by me. I also tried a directory not owned by me, but with world rwx permissions. Still the same. But Firefox will let me save files in /tmp...

[FONT=Courier New]> ls -ld /tmp /wizz
drwxrwxrwt 14 root    root 12288 2010-08-04 20:41 /tmp
drwxrwxrwx  3 newuser dave  4096 2010-08-03 20:33 /wizz[/FONT]

The only difference is the 't' flag.

This is wierd.

---

### Post by lovinglinux on 2010-08-04
> **TheLancashireman said:**
> The problem directories are all owned by me. I also tried a directory not owned by me, but with world rwx permissions. Still the same. But Firefox will let me save files in /tmp...

[FONT=Courier New]> ls -ld /tmp /wizz
drwxrwxrwt 14 root    root 12288 2010-08-04 20:41 /tmp
drwxrwxrwx  3 newuser dave  4096 2010-08-03 20:33 /wizz[/FONT]

The only difference is the 't' flag.

This is wierd.

Indeed. I have no idea what is going on.

---

### Post by TheLancashireman on 2010-08-05
Progress! It's something in the .mozilla directory, but not the profile.

I moved ~/.mozilla to somewhere else and started firefox from new, and everything seems OK now.

I'm going to start putting things back slowly, starting with my profile because there's lots of stuff there that I don't want to lose if I can help it.

---

### Post by lovinglinux on 2010-08-05
> **TheLancashireman said:**
> Progress! It's something in the .mozilla directory, but not the profile.

I moved ~/.mozilla to somewhere else and started firefox from new, and everything seems OK now.

I'm going to start putting things back slowly, starting with my profile because there's lots of stuff there that I don't want to lose if I can help it.

In this case see [Fixing a problematic or corrupted profile](http://firefox-tutorials.blogspot.com/2010/05/fixing-problematic-or-corrupted-profile.html)

---

### Post by TheLancashireman on 2010-08-05
Right. Now I'm really confused.

I put .mozilla back as it was, then moved the firefox directory. Started firefox - everything OK.

Close firefox, copy all the files from the profile directory into the new profile directory,  restart firefox - everything OK.

Close firefox, copy pluginreg.dat from old firefox into new, restart firefox - everything OK.

So now I have a .mozilla directory that to all intents and purposes is the same as it was before, except that I can now save files into directories outside home. The only differences are:
 - the profile now has a different name
 - profile.ini only has one profile in it, but since I created the 2nd profile in the old directory to try to troubleshoot this problem, I don't think it can be the source of the problem.

So: not solved, exactly, but gone away.
Stuff like this is what I associate with Windows, not with Linux. It's more than a little worrying, I have to say.

---

### Post by TheLancashireman on 2010-08-05
I tried creating a new profile already - the problem was still there.

---

### Post by lovinglinux on 2010-08-05
> **TheLancashireman said:**
> Right. Now I'm really confused.

I put .mozilla back as it was, then moved the firefox directory. Started firefox - everything OK.

Close firefox, copy all the files from the profile directory into the new profile directory,  restart firefox - everything OK.

Close firefox, copy pluginreg.dat from old firefox into new, restart firefox - everything OK.

So now I have a .mozilla directory that to all intents and purposes is the same as it was before, except that I can now save files into directories outside home. The only differences are:
 - the profile now has a different name
 - profile.ini only has one profile in it, but since I created the 2nd profile in the old directory to try to troubleshoot this problem, I don't think it can be the source of the problem.

So: not solved, exactly, but gone away.
Stuff like this is what I associate with Windows, not with Linux. It's more than a little worrying, I have to say.

Weird. Let's hope it doesn't come back.

---

### Post by Eeqmcsq on 2010-08-12
I have the exact same problem. I upgraded from ubuntu 9.04 32-bit to 9.10 then to 10.04. I am unable to save files to certain directories, such as to /dev/shm, which should be writable by anyone. I had been using /dev/shm as my Firefox cache location and it had worked in 9.04. Strangely enough, Firefox does let me save to /tmp. Using /tmp as my Firefox cache location also works. 

- On my machine, /tmp is mounted as a tmpfs, so it is exactly the same as /dev/shm. Both of them also have this 't' property, so that rules out the 't' as being a cause.

~$ ls -ld /tmp /dev/shm
drwxrwxrwt  2 root root 100 2010-08-11 20:30 /dev/shm
drwxrwxrwt 15 root root 360 2010-08-11 20:38 /tmp

- If I create a "testdir" under /home with full 777 permissions, I can save a web page there correctly:

sudo mkdir /home/testdir
sudo chmod 777 /home/testdir
launch firefox -> save google home page to /home/testdir = works OK, files saved.

If I now move this "testdir" to the root directory, the test fails:

sudo mv /home/testdir/ /
save google home page to /testdir = FAIL "cannot change the contents of that folder".

The same failure happens if I move the "testdir" to /var. Firefox cannot save to /var/testdir.

Strangely enough, the test was OK under the directory /mnt/testdir. I did some further testing and I discovered that Firefox could save into the "testdir" directory if "testdir" was a subdirectory of this list directories:

/home /mnt /media /tmp

... but not under this list:

/var /dev /lib /usr /opt

I didn't test every subdirectory from the root directory, but based on the few that I did test, I can conclude that something is limiting Firefox to only allow writing to a certain directories.

- If I softlink to /dev/shm from inside /tmp, the test fails.

~$ ln -s /dev/shm /tmp/softlink_to_devshm
save google home page to /tmp/softlink_to_devshm = FAIL "cannot change the contents of that folder".

This tells me it's not the path name itself that's causing the failure.

- If I run Firefox as root, I still cannot save to /dev/shm.
~$ gksudo firefox
save google home page to /dev/shm = FAIL "cannot change the contents of that folder".

Um, that should be impossible. Firefox as root should be able to write anywhere!

Any idea what's causing this?

---

### Post by Eeqmcsq on 2010-08-19
I think I found a solution.

I repeatedly cloned my ubuntu 10.04 partition to a separate drive and ran multiple tests. I still can't figure out why the problem happens, but my tests have shown me that it has something to do with Firefox's "residual config files". Whatever the cause, I figured out the minimum steps required for Firefox to save to /dev/shm.

Make sure all Firefox instances are closed. Or better yet, execute these steps after logging in from a fresh reboot.

1. Back up your current Firefox settings. This way, the purge operation will not delete your settings.
mv ~/.mozilla ~/.mozilla.orig

2. Completely uninstall Firefox, including config files. 
sudo apt-get -y purge firefox

3. Reboot the computer. I don't know why, but this is required.

4. Restore your current Firefox settings.
mv ~/.mozilla.orig ~/.mozilla

5. Reinstall Firefox.
sudo apt-get -y install firefox

6. Retest the problem
launch firefox -> save google home page to /dev/shm = works OK, files saved.

---

### Post by lovinglinux on 2010-08-19
> **Eeqmcsq said:**
> 1. Back up your current Firefox settings. This way, the purge operation will not delete your settings.
mv ~/.mozilla ~/.mozilla.orig

There is no need to do that. The purge command does not delete user config files, but system config files. Your Firefox personal profile will be kept even if you remove, install, reinstall, purge, update Firefox.

---

### Post by Eeqmcsq on 2010-08-19
Hmm, that's interesting. I always assumed that Synaptic's package removal including residual config files, would remove the settings in my home directory, to ensure a completely clean uninstall. So I assumed that the purge command did the exact same thing. I just ran a test for purging Firefox, and the .mozilla directory was still intact.

So that would reduce my steps to simply 3 steps: purge of firefox, reboot, and then reinstall firefox.

My original problem was that firefox would NOT save to /dev/shm after upgrading past 9.04. I didn't have any problems starting Firefox.

As for my solution being a "workaround", I could not find the cause of Firefox not being able to save to /dev/shm. It was not in ~/.mozilla. None of the options in safe-mode made any difference. I replaced /usr/lib/firefox-3.6.8 with a working version from another 32-bit ubuntu installation and the problem was still there.

In hindsight, I didn't know that rebooting the computer was a factor at the time, so I should have rebooted the computer after each test, but it's too late now, because both my cloned partition and my original partition have had their Firefox installations purged and reinstalled. So now I can save files to /dev/shm from Firefox once again, and also my Firefox cache can be written to /dev/shm once again.

Edit: Ignore this paragraph.
The only interesting note is that when I uninstall firefox from Synaptic now, there are no more "residual config files" left. I can only assume that something in one of these residual config files prevented Firefox from writing to /dev/shm.

---

### Post by lovinglinux on 2010-08-19
> **Eeqmcsq said:**
> Hmm, that's interesting. I always assumed that Synaptic's package removal including residual config files, would remove the settings in my home directory, to ensure a completely clean uninstall. So I assumed that the purge command did the exact same thing. I just ran a test for purging Firefox, and the .mozilla directory was still intact.

As far as I know, the purge and Synaptic complete removal clean up config files from /etc and lines inserted on /etc/init.d and such, not files from home.

> **Eeqmcsq said:**
> My original problem was that firefox would NOT save to /dev/shm after upgrading past 9.04. I didn't have any problems starting Firefox.

I know, I mixed up your problem with another issue I was replying to. I assume you had to redo your method every time you start Firefox. That's why I called it "workaround" :) Sorry for that.

> **Eeqmcsq said:**
> The only interesting note is that when I uninstall firefox from Synaptic now, there are no more "residual config files" left. I can only assume that something in one of these residual config files prevented Firefox from writing to /dev/shm.

What "residual config files"?

---

### Post by Eeqmcsq on 2010-08-19
In Synaptic Package Manager, sometimes when you Mark for Complete Removal, and then you apply the changes, the package is not fully uninstalled. In Synaptic, the package is displayed under the status: "Not installed, residual config".

But now that I think about it again, I am mistaken when I said that about "no more residual config files" for Firefox. I remember now that when I ran my uninstall tests from Synaptic on my cloned image, I had intentionally chosen to "Mark for Removal", not "Mark for Complete Removal". "Mark for Removal" would leave the residual config files behind, which required "Mark for Complete Removal" for the package to be fully uninstalled. I did it this way because I had thought that the residual config files included the .mozilla directory in my home directory. At the time, I was looking to see if the cause was somewhere in /usr/lib/firefox-3.6.8/, or if the cause was somewhere in .mozilla.

So what I remember is that I "Mark for Removal" on Firefox, apply, reboot, reinstall from Synaptic, and the problem would still exist. It wasn't until I removed the residual config files, rebooted, and THEN the problem went away and I could save to /dev/shm.

---

### Post by lovinglinux on 2010-08-19
> **Eeqmcsq said:**
> In Synaptic Package Manager, sometimes when you Mark for Complete Removal, and then you apply the changes, the package is not fully uninstalled. In Synaptic, the package is displayed under the status: "Not installed, residual config".

But now that I think about it again, I am mistaken when I said that about "no more residual config files" for Firefox. I remember now that when I ran my uninstall tests from Synaptic on my cloned image, I had intentionally chosen to "Mark for Removal", not "Mark for Complete Removal". "Mark for Removal" would leave the residual config files behind, which required "Mark for Complete Removal" for the package to be fully uninstalled. I did it this way because I had thought that the residual config files included the .mozilla directory in my home directory. At the time, I was looking to see if the cause was somewhere in /usr/lib/firefox-3.6.8/, or if the cause was somewhere in .mozilla.

So what I remember is that I "Mark for Removal" on Firefox, apply, reboot, reinstall from Synaptic, and the problem would still exist. It wasn't until I removed the residual config files, rebooted, and THEN the problem went away and I could save to /dev/shm.

I have no idea what those residual config files for Firefox are. To be honest, I never saw Firefox on that list before, I guess because I always purge it. BTW, not all applications are included in that list when you don't purge. I thought this was the case with Firefox.

---

### Post by houndi on 2010-08-19
right click and save the page first then open the locan file operations and chevk the firefox settings

---

### Post by sollentuna1 on 2010-09-27
> **Eeqmcsq said:**
> I think I found a solution.

I repeatedly cloned my ubuntu 10.04 partition to a separate drive and ran multiple tests. I still can't figure out why the problem happens, but my tests have shown me that it has something to do with Firefox's "residual config files". Whatever the cause, I figured out the minimum steps required for Firefox to save to /dev/shm.

Make sure all Firefox instances are closed. Or better yet, execute these steps after logging in from a fresh reboot.

1. Back up your current Firefox settings. This way, the purge operation will not delete your settings.
mv ~/.mozilla ~/.mozilla.orig

2. Completely uninstall Firefox, including config files. 
sudo apt-get -y purge firefox

3. Reboot the computer. I don't know why, but this is required.

4. Restore your current Firefox settings.
mv ~/.mozilla.orig ~/.mozilla

5. Reinstall Firefox.
sudo apt-get -y install firefox

6. Retest the problem
launch firefox -> save google home page to /dev/shm = works OK, files saved.

Great. This solved my problem. I had the same problem in 10.04 with Firefox 3.6.10 and the version before
. I could save to /tmp and my home folder but no other folder.

I did not pay enough attention but I saw in Nautilus that my /tmp folder content "flickered" when  I tried to save to some other folder!

---

### Post by ticket on 2013-01-20
I also had the problem where the "File -> Save Page as ..." menu item would do nothing (on Firefox 18.0).

It turned out it was due having the extension "Mozilla Archive Format" extension installed.  disabling it cured the problem, and a full fix was obtained simply by re-installing the extension.  Other extensions might also cause the issue - try the same trick!

---

