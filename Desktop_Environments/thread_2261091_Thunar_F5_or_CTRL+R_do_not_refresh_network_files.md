---
title: "Thunar: F5 or CTRL+R do not refresh network files"
date: 2015-01-16
forum: Desktop Environments
---

### Post by riksoft on 2015-01-16
I've found an old thread with the same problem I have
[http://ubuntuforums.org/showthread.php?t=1767254&highlight=thunar+refresh](http://ubuntuforums.org/showthread.php?t=1767254&highlight=thunar+refresh)
and the problem is still here in 2015.

When accessing a dir via Samba, _Thunar doesn't refresh the size of the files_ not automatically nor manually (F5 or CTRL+R).
So, if I overwrite a file, the only way to see the new size is changing dir and go back.
Another way is to rename the file.
Both HORRIBLE ways to accomplish this simple task.
I'm OK with the no auto-notification through the kernel, but at least _the manual refresh SHOULD work_. It's a must!

If I had known of that problem I would have choosen Lubuntu.

---

### Post by Toz on 2015-01-17
Which version of Xubuntu, Xfce and Thunar are you using?
How are you connecting via Samba?

On my Xubuntu 14.04 install, Xfce 4.10, thunar 1.6.3, Thunar automatically refreshes.

---

### Post by riksoft on 2015-01-19
I've tried different distros with XFCE and they all have this problem.
Xubuntu is the latest LTS(14.04.01) 32b, with it's standard config.
The same happen with 14.01 or the latest LTS of Mint Rebecca XFCE (based on Ubuntu 14.04.01).
Doesn't happen with distros based on LXDE or MATE.

Are you sure you've done the right test?
Try this:
1) Create an empty text file on your local fs
2) Access a samba path and copy that file in there.
3) Reopen the file in your local FS and add "aaaa" and save
4) Copy this file on the file in the path samba. It will ask to confirm the overwrite. Ask yes.
5) Look at the size of the file, both in the status bar and from "Properties": it will still show 0 bytes instead of 4.
6) If you now press F5 or CTRL+R the size remains 0 bytes

The only way to see the right size is change directory and get back to this dir.

No problem to see any NEW files or deleted files. The problem is when the files are overwritten. It's surely a bug.

---

### Post by riksoft on 2015-01-19
You could also repeat point 4 hundreds of times and the overwrite alert will continue saying that you are going to overwrite the zero lenght file, despite it has already overwritten previously with the 4 byte version.

---

### Post by riksoft on 2015-01-19
Going to file a bug report, I've discovered that the problem it's even worse because it's not a matter of smb path: The same problem exists between 2 directories in the same local FS.:-s That's ridiculous!

---

### Post by Toz on 2015-01-20
> **riksoft said:**
> I've tried different distros with XFCE and they all have this problem.
Xubuntu is the latest LTS(14.04.01) 32b, with it's standard config.
The same happen with 14.01 or the latest LTS of Mint Rebecca XFCE (based on Ubuntu 14.04.01).
Doesn't happen with distros based on LXDE or MATE.

Are you sure you've done the right test?
Try this:
1) Create an empty text file on your local fs
2) Access a samba path and copy that file in there.
3) Reopen the file in your local FS and add "aaaa" and save
4) Copy this file on the file in the path samba. It will ask to confirm the overwrite. Ask yes.
5) Look at the size of the file, both in the status bar and from "Properties": it will still show 0 bytes instead of 4.
6) If you now press F5 or CTRL+R the size remains 0 bytes

The only way to see the right size is change directory and get back to this dir.

No problem to see any NEW files or deleted files. The problem is when the files are overwritten. It's surely a bug.

Yep. Same test. File size auto updates in Thunar. Only, I'm running the 64 bit version of Xubuntu and I  am connecting to the samba share via autofs.

What version of Thunar do you have? 1.6.3?

---

### Post by riksoft on 2015-01-20
Yep, 1.6.3.

As I said before, the problem is in the local FS as well, even without network paths.

While I was reporting the problem on bugzilla.xfce.org, I discovered that other bug reports are saying that this problem is also on the file date, and it's even worse because there are cases in which the date is not updated even changing dir and coming back, creating HUMONGOUSLY problems.
However, I can't wait for a fix so I've solved the problem this way: PcManFm (the FM of Lubuntu) instead of Thunar.  ):P

I think I'll never use Thunar again even if they solve this problem, because PcManFm is far better. E.g. it has F3 for splitting the panel, open new win from a folder, open a new tab from a folder, and... it works. It also seems faster with thunbnails operations.

So problem, radically solved!:biggrin:

---

### Post by riksoft on 2015-01-26
By the way, I've discovered the problem with Thunar is worse than I thought before.

1) I have one directory where it actually works as expected. On other distro I have more than one dir working properly.

2) I tried to discover why, but there is no easy solution. Even copying entirely the working dir with a slightly different name, it stops working.

3) On not working dirs (basically everywhere), NOT ONLY OVERWRITING has problems, even a deletion + copy: the new file keep the size of the old one as if it was a cache that remember name=size and it isn't updated.

4) As reported by some other guys on Bugzilla, this happen even after changing and getting back on that dir.

So Xubuntu and many others distro with XFCE and the default file manager are highly dangerous when dealing with files manipulation!
The immediate solution is installing PcManFM or even better, despite a little bit heavy (10MB), Nemo.

---

### Post by Toz on 2015-01-26
I was able to do some further testing on this.

Using autofs and cifs-utils or directly via the mount command, the problem is not present.

Mounting a samba share using Thunar via smb://x.x.x.x/share _does_ exhibit the problem. Since thunar uses gvfs to mount shares, it must be a problem with gvfs. In fact, using gvfs directly:
```
gvfs-mount smb://x.x.x.x/share
```
...displays the same problem. The bug report should be with gvfs.

Note: [This]("https://bugzilla.gnome.org/show_bug.cgi?id=627107") might be of interest. It appears that gvfs doesn't support remote file monitoring of cifs (samba) shares. ugh.

I'd be curious to know what protocol/mechanism pcmanfm uses.

---

### Post by Morbius1 on 2015-01-26
>  I'd be curious to know what protocol/mechanism pcmanfm uses. 		
In Lubuntu 14.10 with pcmanfm at 1.2.3 it appears to be gvfs since it mounts to /run/user/$UID/gvfs/.......

---

### Post by Toz on 2015-01-26
> **Morbius1 said:**
> In Lubuntu 14.10 with pcmanfm at 1.2.3 it appears to be gvfs since it mounts to /run/user/$UID/gvfs/.......

Thanks. Then I wonder how they are dealing with the issue? I just installed pcmanfm, and it kind of works. When I copy over the file, it actually creates two icons of the same file - one with the older file size and one with the newer file size. An F5 refresh sorts it out though.

On Thunar, no amount of refreshing gets it to work. As the @OP says, you need to back out and in again. Hmmm.

From [http://sourceforge.net/p/pcmanfm/bugs/760/]("http://sourceforge.net/p/pcmanfm/bugs/760/"):
> Yes, it is exactly how it works. PCManFM never scans file directory for updates, it just "subscribes" for updates (it is GFileMonitor object in GIO) and GVFS should send an update when something is changed. If GVFS sends nothing then there is no possibility to know if something was changed. It's why such monitoring issue should be reported to gvfs, not to application which uses gvfs.
...and yet they've somehow sorted it out.

To the @OP, I see you've created a [bug report against Thunar]("https://bugzilla.xfce.org/show_bug.cgi?id=11468"). Lets see where this goes.

Seems like a potential workaround, if you're still interested in using Thunar, is to not use gvfs for mounting, but rather use manual, fstab or autofs mount mechanisms.

---

### Post by Morbius1 on 2015-01-26
There seems to a lot of going out of thunar and back again lately: [https://bugzilla.xfce.org/show_bug.cgi?id=11001](https://bugzilla.xfce.org/show_bug.cgi?id=11001)

---

### Post by mikodo on 2015-01-26
I apologize riksoft, for side tracking here.

Does anyone know if the Xfce-devels, are still hopeful in developing Thunar to manage the desktop, replacing [Xfdesktop?]("http://docs.xfce.org/xfce/xfdesktop/start")  I can't find any links to substantiate this any more.

---

### Post by riksoft on 2015-01-27
> Using autofs and cifs-utils or directly via the mount command, the problem is not present.[B]
Please, note that the problem has turned to be [U]NOT NETWORK RELATED

[/U][/B]
It happens on normal operations on the local FS, and I have this problem on every computer, despite on some computers and in only some directories it works properly (and I don't understand what is the cause because even copying that working directory, the copy doesn't have the same luck :p)

Maybe it's better explained in _the bug report I opened on Bugzilla_
[https://bugzilla.xfce.org/show_bug.cgi?id=11468](https://bugzilla.xfce.org/show_bug.cgi?id=11468)

If you search on bugzilla for thunar + refresh, you'll get some similar reports despite focused on other aspect:
[URL="https://bugzilla.xfce.org/show_bug.cgi?id=11008"]https://bugzilla.xfce.org/show_bug.cgi?id=11008
[/URL][https://bugzilla.xfce.org/show_bug.cgi?id=10504](https://bugzilla.xfce.org/show_bug.cgi?id=10504)

There is also a video demonstrating the problem.
[http://youtu.be/9rU_5IUuMqM](http://youtu.be/9rU_5IUuMqM)

There is surely a sneaky bug, not easy to find because these reports are from 2013.
I can't wait years, so in the meantime I shifted from Thunar to PcManFm and Nemo that are both in the Ubuntu repo.

---

### Post by LewisTM on 2015-01-27
Hi there,

I can replicate this behavior, which is a strange one. 

However, there is no issue when copying by drag-and-drop (holding ctrl) to a directory in the tree or by rick-clicking the target folder and selecting "Paste into folder". In other words, if you copy to a directory that is not currently listed, you're good. As proof, drag and drop between tabs is also broken, presumably because the target directory gets displayed before the operation completes.

Dunno if that helps anyone...

---

### Post by Toz on 2015-01-27
> **mikodo said:**
> 
Does anyone know if the Xfce-devels, are still hopeful in developing Thunar to manage the desktop, replacing [Xfdesktop?]("http://docs.xfce.org/xfce/xfdesktop/start")  I can't find any links to substantiate this any more.

I haven't heard anything in quite a while. I believe [this]("http://git.xfce.org/users/nick/thunar/") is Nick's working git tree for the code. No updates in over a year.

---

### Post by mikodo on 2015-01-29
> **Toz said:**
> I haven't heard anything in quite a while. I believe [this]("http://git.xfce.org/users/nick/thunar/") is Nick's working git tree for the code. No updates in over a year.Thank you, Toz.

---

