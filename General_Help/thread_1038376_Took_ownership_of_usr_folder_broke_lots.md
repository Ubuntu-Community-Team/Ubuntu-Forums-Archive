---
title: "Took ownership of usr folder broke lots"
date: 2009-01-12
forum: General Help
---

### Post by drs305 on 2009-01-12
I wrote a how-to on .dmrc permission errors:
[Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?p=6161267")

That should get things back in order once you get to a root prompt.

Normally you should be able to get to the recovery mode (without using the cd) since it appears you can boot to the normal mode but get error messages. 

If you don't see the menu because you have 'autologon' enabled, reboot your computer and after you hear your computer's system beep start hitting the ESC key until grub's menu.lst appears. You should see an option for "Recovery Mode". Select this, hit Enter, and then select "Drop to a root shell prompt". Then follow the instructions in the how-to.

---

### Post by Lostin60's on 2009-01-12
I know there is a thread for this, but I can't find it. So here is my problem. I accidentally took ownership of my usr directory. One of the things that this caused, was loss of my sudo. And of course, all the fixes I could find that didn't require using the cd, did require sudo. A post said use the cd and enter the recovery mode. There isn't on on my cd. However, on my first attempt to fix this I putzed around and managed to get to a command line without actually booting the cd. I mean I got to a command line during the boot process. I don't remember how I did it though. So I typed

```
ls -l usr/bin/sudo
```

That gave me daniel daniel for ownership, so I chowned it and got root root. So I re-booted the computer. During re-boot I got messages. "users home/.dmrc is being ignored. User needs to own this dir and have 644 permisions" I open this file to see what it was, and it was empty. I also got "couldn't update ICEauthorazation file. /home/daniel/ICEauthorization" So, I need to know how to get back to that command line when starting the cd. I also need to know how to change the permission (mode?) I tried chmod when I re-booted without the cd, but I have so many issues it didn't work. Oh, it told me 644 was (not a permission mode?) Any and all help will be appreciated...and needed..lol. I am running Intrepid, by the way.

__________________

---

### Post by bodhi.zazen on 2009-01-12
You are probably best off re-installing as it is difficult and time consuming to fix these issues.

---

### Post by The Cog on 2009-01-12
I agree with bodhi.zazen. Although most of the files in /usr are owned by root, the few that aren't (shouldn't be) could be a cause of difficulties for a long time to come, and very hard to track down.

---

### Post by mssever on 2009-01-12
> **Lostin60's said:**
> So I re-booted the computer. During re-boot I got messages. "users home/.dmrc is being ignored. User needs to own this dir and have 644 permisions" I open this file to see what it was, and it was empty. I also got "couldn't update ICEauthorazation file. /home/daniel/ICEauthorization" So, I need to know how to get back to that command line when starting the cd. I also need to know how to change the permission (mode?) I tried chmod when I re-booted without the cd, but I have so many issues it didn't work. Oh, it told me 644 was (not a permission mode?) Any and all help will be appreciated...and needed..lol. I am running Intrepid, by the way.
bodhi.zazen's advice might end up being the best advice, however if you want to keep working on this, here are a couple of things to try:

[LIST=1]
[*]To get to recovery mode, hit Esc during the Grub splash screen (it's really brief, so pay attention).
[*]Your home directory needs to be owned by your user and have permissions of 644 or more restrictive. Go ahead and delete ~daniel/.dmrc and ~daniel/.ICEauthorization.
[/LIST]
However, not everything under /usr should be owned by root. If you never did a recursive chown, you should be able to putt out of it without too much trouble. If you recursively chowned, you're in for a serious headache if you decide to fix it manually instead of reinstalling.

---

### Post by Lostin60's on 2009-01-12
> **drs305 said:**
> I wrote a how-to on .dmrc permission errors:
[Solving .dmrc and $HOME Permission Errors]("http://ubuntuforums.org/showthread.php?p=6161267")

That should get things back in order once you get to a root prompt.


Great advice! Got sudo back, and can run command line again.  However, I have other issues now. I don't have an internet connection any more, although ndiswrapper is installed and all the files seem to be in the right places. *lshw -C network* says the correct driver is in use. Also I have no network icon in the top panel. My second issue is that I can no longer access Windows from Ubuntu. It shows up in "Places", but won't mount. And permission modes seem to be messed up. I tried chmod but nothing changed.
Is -1 /home/daniel/.dmrc       
-rw-rw— 1 daniel daniel [COLOR="Red"]2[/COLOR] 2009-01-12 18:25 /home/daniel/.dmrc daniel@localhost:/$ 
Is -1 /home/daniel 
total 52
-rw-r~r~ 1 daniel daniel 82 2009-01-07 00:27 = drwxr-xr-x 3 daniel daniel 4096 2009-01-11 18:07 Desktop drwxr-xr-x 5 daniel daniel 4096 2009-01-09 22:14 Documents
lrwxrwxrwx 1 daniel daniel 26 2008-12-27 14:22 Examples -> /usr/share/example-content
drwxr-xr-x 2 daniel daniel 4096 2009-01-04 16:47 From Windows
drwxr-xr-x 2 daniel daniel 4096 2009-01-10 22:30 Internet Downloads
drwxr-xr-x 2 daniel daniel 4096 2008-12-27 14:39 Music
drwxr-xr-x 3 daniel daniel 4096 2009-01-07 17:39 Photos
drwxr-xr-x 2 daniel daniel 4096 2008-12-27 14:39 Pictures
drwxr-xr-x 2 daniel daniel 4096 2008-12-27 14:39 Public
drwxr-xr-x 2 daniel daniel 4096 2008-12-27 14:39 Templates
-rw-r-r- 1 daniel daniel 2388 2009-01-10 22:29 t_skariah.asc.gpg
drwxr-xr-x 2 daniel daniel 4096 2008-12-27 14:39 Videos
drwxr-xr-x 3 daniel daniel 4096 2009-01-10 16:26 work
daniel@localhost:/$
The 644 and 755 permissions are also wrong.  I would greatly appreciate any other help you can offer.
[COLOR="White"]aa[/COLOR]

---

### Post by Lostin60's on 2009-01-12
> **mssever said:**
> bodhi.zazen's advice might end up being the best advice, however if you want to keep working on this, here are a couple of things to try:

[LIST=1]
[*]To get to recovery mode, hit Esc during the Grub splash screen (it's really brief, so pay attention).
[*]Your home directory needs to be owned by your user and have permissions of 644 or more restrictive. Go ahead and delete ~daniel/.dmrc and ~daniel/.ICEauthorization.
[/LIST]
However, not everything under /usr should be owned by root. If you never did a recursive chown, you should be able to putt out of it without too much trouble. If you recursively chowned, you're in for a serious headache if you decide to fix it manually instead of reinstalling.

OK, I have this post in 2 threads, as I did not know which one was the more appropriate. I also got a reply in the other post that was helpful. I still have a ways to go, though. This is my reply to that post.

Great advice! Got sudo back, and can run command line again. However, I have other issues now. I don't have an internet connection any more, although ndiswrapper is installed and all the files seem to be in the right places. lshw -C network says the correct driver is in use. Also I have no network icon in the top panel. My second issue is that I can no longer access Windows from Ubuntu. It shows up in "Places", but won't mount. And permission modes seem to be messed up. I tried chmod but nothing changed.
Is -1 /home/daniel/.dmrc
-rw-rw— 1 daniel daniel [COLOR="Red"]2[/COLOR] 2009-01-12 18:25 /home/daniel/.dmrc daniel@localhost:/$
Is -1 /home/daniel
total 52
-rw-r~r~ 1 daniel daniel 82 2009-01-07 00:27 = drwxr-xr-x 3 daniel daniel 4096 2009-01-11 18:07 Desktop drwxr-xr-x 5 daniel daniel 4096 2009-01-09 22:14 Documents
lrwxrwxrwx 1 daniel daniel 26 2008-12-27 14:22 Examples -> /usr/share/example-content
drwxr-xr-x 2 daniel daniel 4096 2009-01-04 16:47 From Windows
drwxr-xr-x 2 daniel daniel 4096 2009-01-10 22:30 Internet Downloads
drwxr-xr-x 2 daniel daniel 4096 2008-12-27 14:39 Music
drwxr-xr-x 3 daniel daniel 4096 2009-01-07 17:39 Photos
drwxr-xr-x 2 daniel daniel 4096 2008-12-27 14:39 Pictures
drwxr-xr-x 2 daniel daniel 4096 2008-12-27 14:39 Public
drwxr-xr-x 2 daniel daniel 4096 2008-12-27 14:39 Templates
-rw-r-r- 1 daniel daniel 2388 2009-01-10 22:29 t_skariah.asc.gpg
drwxr-xr-x 2 daniel daniel 4096 2008-12-27 14:39 Videos
drwxr-xr-x 3 daniel daniel 4096 2009-01-10 16:26 work
daniel@localhost:/$
The 644 and 755 permissions are also wrong. I would greatly appreciate any other help you can offer.

Now, if someone could offer some advice on these problems, I would be most grateful. At this point, reinstall is not  an option. No offense meant here, honestly, but if I wanted to reinstall every time I had issues, I would stick with Windows. I did that too many times when I knew the problem, but couldn't access the files I needed to fix it. That is one reason I am here. My issues with windows are too numerous to list. I won't learn if I keep starting from scratch. I am starting to teach myself C++, and I want to learn all I can about Ubuntu.  I am more than willing to take the time and effort to do that. Between putzing around on my own, and all the advice available in the forums, I'll get there. Any and all help will be appreciated.
[COLOR="White"]aa[/COLOR]

---

### Post by mssever on 2009-01-12
I admire you for not wanting to re-install. I tend to take that attitude myself, though I might make an exception in your case. Be warned that this will be a very time-consuming and error-prone task.

As far as Windows partition permissions go, you have to fix them in fstab. Read "man 8 mount" for documentation.

Aside from that, you'll need to take a systematic approach to make sure you address every file under /usr. To discover each file's proper permissions, you'll likely need to do a bit of research.

One idea you can test (I don't know if it will work) is to see if reinstalling a package will fix the permissions for all its files. It probably will fix everything except configuration files, but those are mostly under /etc so might not be relevant. You can use ```
dpkg --search filename
```to discover which package a given file belongs to. This would likely be nearly like reinstalling, but doing it in a controlled manner.

---

### Post by bodhi.zazen on 2009-01-13
To fix you .drmc error see here :

[http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)

I do not see how this particular error occurred based on the information you provided and suspect your system permissions are deeply disturbed.

How (what command) did you use to cause your problems ?

As has been said by several experienced users, if you changed ownership in /usr restoration may take a long time and may be incomplete.

Best of luck to you and we will watch with interest.

---

### Post by handydan918 on 2009-01-13
> **Lostin60's said:**
> OK, I have this post in 2 threads, as I did not know which one was the more appropriate. I also got a reply in the other post that was helpful. I still have a ways to go, though. This is my reply to that post.

Great advice! Got sudo back, and can run command line again. However, I have other issues now. I don't have an internet connection any more, although ndiswrapper is installed and all the files seem to be in the right places. lshw -C network says the correct driver is in use. Also I have no network icon in the top panel. My second issue is that I can no longer access Windows from Ubuntu. It shows up in "Places", but won't mount. And permission modes seem to be messed up. I tried chmod but nothing changed.
Is -1 /home/daniel/.dmrc
-rw-rw— 1 daniel daniel [COLOR="Red"]2[/COLOR] 2009-01-12 18:25 /home/daniel/.dmrc daniel@localhost:/$
Is -1 /home/daniel
total 52
-rw-r~r~ 1 daniel daniel 82 2009-01-07 00:27 = drwxr-xr-x 3 daniel daniel 4096 2009-01-11 18:07 Desktop drwxr-xr-x 5 daniel daniel 4096 2009-01-09 22:14 Documents
lrwxrwxrwx 1 daniel daniel 26 2008-12-27 14:22 Examples -> /usr/share/example-content
drwxr-xr-x 2 daniel daniel 4096 2009-01-04 16:47 From Windows
drwxr-xr-x 2 daniel daniel 4096 2009-01-10 22:30 Internet Downloads
drwxr-xr-x 2 daniel daniel 4096 2008-12-27 14:39 Music
drwxr-xr-x 3 daniel daniel 4096 2009-01-07 17:39 Photos
drwxr-xr-x 2 daniel daniel 4096 2008-12-27 14:39 Pictures
drwxr-xr-x 2 daniel daniel 4096 2008-12-27 14:39 Public
drwxr-xr-x 2 daniel daniel 4096 2008-12-27 14:39 Templates
-rw-r-r- 1 daniel daniel 2388 2009-01-10 22:29 t_skariah.asc.gpg
drwxr-xr-x 2 daniel daniel 4096 2008-12-27 14:39 Videos
drwxr-xr-x 3 daniel daniel 4096 2009-01-10 16:26 work
daniel@localhost:/$
The 644 and 755 permissions are also wrong. I would greatly appreciate any other help you can offer.

Now, if someone could offer some advice on these problems, I would be most grateful. At this point, reinstall is not  an option. No offense meant here, honestly, but if I wanted to reinstall every time I had issues, I would stick with Windows. I did that too many times when I knew the problem, but couldn't access the files I needed to fix it. That is one reason I am here. My issues with windows are too numerous to list. I won't learn if I keep starting from scratch. I am starting to teach myself C++, and I want to learn all I can about Ubuntu.  I am more than willing to take the time and effort to do that. Between putzing around on my own, and all the advice available in the forums, I'll get there. Any and all help will be appreciated.
[COLOR="White"]aa[/COLOR]

Here is my ls -l on the same directory. It's Intrepid, but it's a vbox install. Hope it helps.```
daniel@ubu-vbox:~$ ls -l /home/daniel
total 28
drwxr-xr-x 2 daniel daniel 4096 2008-11-12 12:54 Desktop
drwxr-xr-x 2 daniel daniel 4096 2008-11-12 12:54 Documents
lrwxrwxrwx 1 daniel daniel   26 2008-11-12 12:46 Examples -> /usr/share/example-content
drwxr-xr-x 2 daniel daniel 4096 2008-11-12 12:54 Music
drwxr-xr-x 2 daniel daniel 4096 2008-11-12 12:54 Pictures
drwxr-xr-x 2 daniel daniel 4096 2008-11-12 12:54 Public
drwxr-xr-x 2 daniel daniel 4096 2008-11-12 12:54 Templates
drwxr-xr-x 2 daniel daniel 4096 2008-11-12 12:54 Videos

```

---

### Post by Lostin60's on 2009-01-14
> **bodhi.zazen said:**
> To fix you .drmc error see here :

[http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)

I do not see how this particular error occurred based on the information you provided and suspect your system permissions are deeply disturbed.

How (what command) did you use to cause your problems ?

As has been said by several experienced users, if you changed ownership in /usr restoration may take a long time and may be incomplete.

Best of luck to you and we will watch with interest.

Well, I decided I want a workable ubuntu now, but I want to fix these issues, as I think it will be a GREAT learning tool. So, I downsized my windows partition and my ubuntu partition. Then I installed Intrepid. Now I can work on fixing the old install. I am sure I will return to this post daily, in other words, "Hi'ya Teach"...lol. I know I am getting the hang of this command line usage. On my first install it took me 3 or 4 days to get my Broadcom driver to work. Today it was about an hour, and that was only because I had to figure out how to update the blacklist.
```
sudo update-initramfs -k all -u
```
That returned "not permitted" error so I did a chown
```
chown -r daniel initrd.img-2.6.27-7-generic
```
And gave root full permissions. Re-booted and there was my internet. My goal in the long run is to repair my crushed (a good description) install, make myself an ubuntu guide as I go, and finally to "killdisk" my HDD and do a clean install of only ubuntu....whew, daunting. So, I appreciate the advice I have gotten so far, and will certainly be back for more. Since I can compare content, ownership, and permissions, on this install to those on the previous install I won't need to figure out as much "what to fix" and concentrate on "how to fix". I hope to create a good tutorial on how to fix a badly broken install. Again, thanks for the help, and here I gooooooo!!!

Sorry,almost forgot. You asked how I fouled up my .dmrc.  No laughing now...well ok, but just a little. In the heat of battle, I think I accidentally did "chown root" instead of "chown daniel", but far worse, I didn't just take ownership of /usr, I took it recursively. Sigh....OK, go ahead and laugh.
[COLOR="White"]aa[/COLOR] 
[COLOR="White"]aa[/COLOR]

---

### Post by mssever on 2009-01-14
> **Lostin60's said:**
> Well, I decided I want a workable ubuntu now, but I want to fix these issues, as I think it will be a GREAT learning tool.
It'll be a good learning tool, but eventually you'll have the hang of it and it will simply become tedious (I believe that there are well over 10,000 files you'll need to examine). At the point where it becomes tedious, I urge you to stop trying to restore your system, because once you've learned what you can learn, further effort down that road will be just wasting time.

NOTE: I've already said that I prefer not to reinstall (I've only had one problem that I had to reinstall to fix). I also happen to know that bodhi.zazen isn't one to suggest reinstalling to fix every little problem. Both of us have years of Linux experience (> 10 in my case), and we're both recommending a re-install at some point, so you should take that into consideration. (I don't know the other posters enough to know their experience level.)
> That returned "not permitted" error so I did a chown
```
chown -r daniel initrd.img-2.6.27-7-generic
```And gave root full permissions. Re-booted and there was my internet.Careful, now. Don't go chowning stuff willy-nilly. initrd should be owned by root. (Here's a hint: The only place where files need to be owned by your user is below your home directory. There are a handful of other places where it might be convenient to have your user own files--such as Apache's website directory--but those are rare exceptions.)

Don't chown system files (i.e., those not in a user's homedir) to your account unless you know what you're doing. And I don't think you have enough experience yet to know what you're doing--even if you think you do.

I don't know what it was that made your Internet work, but it wasn't chowning initrd. Fortunately, in this case it's probably not a big deal. But that's an unnecessary gamble.

EDIT: I just noticed you did a chown -r on initrd. That's worrying, because it suggests that you're using the recursive flag without understanding it--which is what got you into this mess in the first place. Read the man page of all commands before running those commands. And *only use -r when you really, really mean recursive*. In this case, it didn't hurt anything since you can't recurse a single file. But the mere fact that you used the recursive option when you didn't need to is worrying.

---

### Post by Lostin60's on 2009-01-14
> **mssever said:**
>  At the point where it becomes tedious, I urge you to stop trying to restore your system, because once you've learned what you can learn, further effort down that road will be just wasting time.
Careful, now. Don't go chowning stuff willy-nilly. initrd should be owned by root. (Here's a hint: The only place where files need to be owned by your user is below your home directory. There are a handful of other places where it might be convenient to have your user own files--such as Apache's website directory--but those are rare exceptions.)
Don't chown system files (i.e., those not in a user's homedir) to your account unless you know what you're doing. And I don't think you have enough experience yet to know what you're doing--even if you think you do.
I don't know what it was that made your Internet work, but it wasn't chowning initrd. Fortunately, in this case it's probably not a big deal. But that's an unnecessary gamble.

EDIT: I just noticed you did a chown -r on initrd.  And *only use -r when you really, really mean recursive*. In this case, it didn't hurt anything since you can't recurse a single file. But the mere fact that you used the recursive option when you didn't need to is worrying.

First off, I wish to truly thank you for your valuable input, and hope you will continue to help me out. I also want you to know that I do respect your expertise, so when it seems I am arguing a point, it is only for clarification. Having said that, I will now argue..lol.

I agree that there will come a point where I am simply doing the same thing to file after file. When I get to that point, or very close to it, I will stop, as by then I will have learned what I need. 

As far as chowning goes, I will explain why I did that, then if you know a better way to accomplish it, I am all ears. Also I am  returning ownership to root. Here is what happened, and it is an internet issue.  I have a broadcom WLAN card, and needed to use ndiswrapper with it. I also needed to blacklist "b43 and ssb" as they were claiming my card. However just adding them to the blacklist file, doesn't stop those modules from opening on boot, unless I update initramfs.
> ndiswrapper won't work until you tell the system not to use the module that's trying to claim the card. You can prevent the system from loading modules by adding them to '/etc/modprobe.d/blacklist.

> Code: 
update-initramfs -k all -uNow reboot. Thereafter, the system will not load ath_pci until you remove it from the blacklist

Source: Sticky:   [all variants]   Comprehensive ndiswrapper troubleshooting guide
pytheas22 
But that code gives this return
```
update-initramfs: Generating /boot/initrd.img-2.6.27-7-generic
/usr/sbin/update-initramfs: 547: cannot create /var/lib/initramfs-tools/2.6.27-7-generic: Permission denied
```
And I could see no way around this except for taking ownership. I do see now, that recursive was unnecessary. But I thought if I only owned the folder, the file still wouldn't change. I also figured out how to get the file extracted and alone, *after* I did the chown. I am pretty sure that what pytheas22 said is true, as I rebooted twice and "b43" stil claimed my card, but when I rebooted after the update my driver claimed the card, and I was up and running. Which brings me to my question. What is the effective difference between leaving root with ownership and taking ownership myself, but giving root full permissions? And, how would you have handled this?
Once again, my thanks.
[COLOR="White"]aa[/COLOR]

---

### Post by bodhi.zazen on 2009-01-14
use sudo

```
sudo update-initramfs -k all -u
```

---

### Post by mssever on 2009-01-14
@Lostin60's:

I won't take offense at what you say if you don't take offense at what I say. :) I hope my last post wasn't worded too strongly (I've had some misgivings about that), but I think it's better for both of us to speak clearly.

As to your explanation about initrd, I see now why you did that. In the future, use sudo. Basically, most system files can only be modified by root for security reasons. The Ubuntu way to get root access is to put sudo before each command. The instructions you followed might not have used sudo because the traditional way to get root access is to use one of several methods to get a root shell. This is how most distributions work, as well. Personally, I think that using sudo is superior to a traditional root shell. So just remember that if you get a permissions error and you aren't using sudo, the first thing to try is sudo, given if the documentation you're reading doesn't explicitly mention it.

Also, I think I remember you saying that this is on your new install with un-borked permissions. It's safe to assume that system files on an un-borked box will have the proper ownership and permissions unless you change them.

Finally, you've set your initrd ownership and permissions back to the way it's supposed to be, right? (owned by root:root with permissions 0644)

---

### Post by Lostin60's on 2009-01-15
> **mssever said:**
> @Lostin60's:

I won't take offense at what you say if you don't take offense at what I say. :) I hope my last post wasn't worded too strongly (I've had some misgivings about that), but I think it's better for both of us to speak clearly.
Also, I think I remember you saying that this is on your new install with un-borked permissions. 
Finally, you've set your initrd ownership and permissions back to the way it's supposed to be, right? (owned by root:root with permissions 0644)

Please, feel free to speak freely. Tact is fine..in it's place, but if you are trying to emphasize the seriousness of what you say, tack is pretty much useless.
I assume un-borked is a nice way of saying I haven't screwed it up yet..lol.
And,yes, I have returned ownership (root:root), and I assumed it would default to 644, or 600, however
```
daniel@GLENDA:/$ ls -l /boot/initrd.img-2.6.27-7-generic
-rw-r--r-- 1 root root 8201872 2009-01-15 01:57 /boot/initrd.img-2.6.27-7-generic
```

[COLOR="Cyan"]```
daniel@GLENDA:/$ sudo chmod -v 644 /boot/initrd.img-2.6.27-7-generic
mode of `/boot/initrd.img-2.6.27-7-generic' retained as 0644[/COLOR] (rw-r--r--)
daniel@GLENDA:/$ ls -l /boot/initrd.img-2.6.27-7-generic
-rw-r--r-- 1 root root 8201872 2009-01-15 01:57 /boot/initrd.img-2.6.27-7-generic
```
I thought that the *ls -l* gave the mode? I think it does when I am in the old install, working on it. I am going to check that. Oh, does ubuntu have a good voice recognition program. A tree made a diligent effort at removing my hand back in '89. I still have the hand, but it makes typing so slow.
As always...thanks.
[COLOR="White"]aa[/COLOR]

---

### Post by mssever on 2009-01-15
> **Lostin60's said:**
> I thought that the *ls -l* gave the mode?
It does. -rw-r--r-- is equivalent to 0644.

> Oh, does ubuntu have a good voice recognition program. A tree made a diligent effort at removing my hand back in '89. I still have the hand, but it makes typing so slow.
I don't know of any such program, but I've never looked for one, either. As an alternative, you might consider using one of the one-handed Dvorak keyboard layouts.

---

### Post by albinootje on 2009-01-15
> **Lostin60's said:**
> Since I can compare content, ownership, and permissions, on this install to those on the previous install I won't need to figure out as much "what to fix" and concentrate on "how to fix". I hope to create a good tutorial on how to fix a badly broken install.

Comparing the permissions with a properly installed Ubuntu installation is a good idea, but, apart from the more regular chmod and chown actions, you will also need to study on the setuid- and perhaps setgid, sticky bit permissions for files and/or directories.

This might help to learn more :
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

