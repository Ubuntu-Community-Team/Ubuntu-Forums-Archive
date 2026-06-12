---
title: "Few problems/bugs with Lubuntu"
date: 2012-03-02
forum: Desktop Environments
---

### Post by Blitz Tungsten on 2012-03-02
For the last 4 months I've been using Lubuntu 11.10 because it provides what I'm basically looking for in a Linux distro:
- lightweight DE -> less RAM used;
- system performance (especially for a 6.5 years old laptop);
- minimalistic interface.

But I'd like to point out few problems/bugs that I've encountered in these 4 months.

**1) Extracting files from archives by dragging them manually on the desktop**:
i.e. I've a folder with many files and I just want to extract one of them to the desktop.
Result: I've to reboot. I receive a window with an error and there's no way to kill the process or to do anything else if not manually rebooting the computer.
On the other hand, if I extract files by clicking on the extract button whitin the File Archiver, everything is OK.

**2) Is there any CTRL+Z/undo in pcmanfm?**
i.e. I delete a file, but then I want to recover it, I can't undo this action by pressing CTRL+Z.
I've to manually recover it from the trash.
Or if I paste a file to the wrong folder, I can't undo this action either.
Is there any workaround?

**3) When I try to paste something on the desktop, it always appears a window asking "Confirm to replace files" -> There is already a file with the same name in this location.**
It seems to happen only on the desktop and not elsewhere.
Of course, I don't have a file with the same name, but it seems that it's trying to paste twice the same file, so immediately after it starts pasting the file, it asks for replacement.
It's pretty annoying.
Any suggestions?

**4) Volume control.**
I've installed Alsa mixer and Pulse Audio, but there's no way to mute the microphone of my laptop if I am not using it.
i.e. If I'm not using Skype, I'd like to turn off my mic. 
What can I do?

**5) Few tabs with Flash (YouTube, ESPN.com, ecc.) and... the system freezes.**
I've to manually reboot. And it doesn't happen when it exceeds the memory available. It just happens even if I have one YouTube tab and few other random tabs.
It was happening to me also when I was using Ubuntu.
Sometimes it happens twice a day.
It happens with Chromium, I don't know if it occurs in Firefox too.
I've the latest version of Flash (64-bit) and lately, with Chromium 17, I've started experiencing a lot of "Aw, snap!" tabs and I've to reload too often...
What am I doing wrong?

**6) Mounting NTFS partition.**
The first time of each session that I mount my data partition (NTFS) I get the following error message:
> DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending
I just click "Ok" and it mounts correctly.
How can I avoid this?


Apart from these issues, I love Lubuntu and I would use it even if I had a last gen. quad core with 16GB of RAM, because I love the philosophy behind a light desktop environment.

---

### Post by Paddy Landau on 2012-03-02
Hello Blitz

For future note, it would probably be better to post each problem in a separate thread in the appropriate forums.

I don't have all the answers, but I will answer what I can.

> **Blitz Tungsten said:**
> **2) Is there any CTRL+Z/undo in pcmanfm?**
No, sorry. That is something that pcmanfm, Thunar, Nautilus, etc. would be well placed to add.

> **Blitz Tungsten said:**
> **5) Few tabs with Flash (YouTube, ESPN.com, ecc.) and... the system freezes.**
There are several possibilities. First, you really want to install only from the repositories (and not from downloads) to be sure of compatibility. Second, ensure your computer is fully up-to-date (using Update Manager). Third, if you haven't installed [lubuntu-restricted-extras]("apt:lubuntu-restricted-extras") package, do so and reboot. Fourth, unfortunately it can be a hardware problem, in which case I'm sorry I have no answers for you.

---

### Post by Rodney9 on 2012-03-02
1. To kill stubborn programmes type in terminal or alt/f2 > xkill and click on the bad program.

4. Fix internal mic for use with Skype

[http://ubuntuforums.org/showthread.php?t=1732074&highlight=pavucontrol](http://ubuntuforums.org/showthread.php?t=1732074&highlight=pavucontrol)

Thanks To ZekeGraal

6. For reading/writing to Windows partions have you installed NTFS_3G ?

NTFS-3G uses FUSE (Filesystem in Userspace) to provide support for the NTFS
filesystem used by Microsoft Windows. It can:

 * create, remove, rename, or move files, directories, hard links, and streams;
 * read and write files, including streams, sparse files, and transparently
   compressed files;
 * handle special files like symbolic links, devices, and FIFOs;
 * provide standard management of file ownership and permissions, including
   POSIX ACLs.



For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by Blitz Tungsten on 2012-03-02
> **Paddy Landau said:**
> Hello Blitz

For future note, it would probably be better to post each problem in a separate thread in the appropriate forums.

I don't have all the answers, but I will answer what I can.


No, sorry. That is something that pcmanfm, Thunar, Nautilus, etc. would be well placed to add.

I didn't know how to handle multiple issues, so I thought about a single post to be linked in the Lubuntu One Stop Thread.

I'm in the waiting list for a pcmanfm, Nautilus, etc. evolution!

> There are several possibilities. First, you really want to install only from the repositories (and not from downloads) to be sure of compatibility. Second, ensure your computer is fully up-to-date (using Update Manager). Third, if you haven't installed [lubuntu-restricted-extras]("apt:lubuntu-restricted-extras") package, do so and reboot. Fourth, unfortunately it can be a hardware problem, in which case I'm sorry I have no answers for you.

I've installed flash64 from the repos, I update my PC daily, I've installed the restriced extras seconds after installing Lubuntu and for what concerns the hardware, I didn't have such problems 13+ months ago when I stopped using Windows XP on this laptop.

Recently it started happening to often while using Chromium with a few tabs open (with usually one of them with a flash video).

Thanks for your help!

---

### Post by Blitz Tungsten on 2012-03-02
> **Rodney9 said:**
> 1. To kill stubborn programmes type in terminal or alt/f2  and click on the bad program.

The problem is that when I try to drag a file from an archive to the desktop/any other folder, there is nothing I can do. 
Lubuntu freezes, I've even tried to wait for hours but nothing can be done. The mouse cursor doesn't move, the keyboard is unresponsive... I can only press on the power button.

> 4. Fix internal mic for use with Skype

[http://ubuntuforums.org/showthread.php?t=1732074&highlight=pavucontrol](http://ubuntuforums.org/showthread.php?t=1732074&highlight=pavucontrol)

Thanks To ZekeGraal

The mic is working perfectly with Skype.
The problem is that I want to mute it/shut it down while I'm not using Skype.
In Ubuntu you can easily do it in the sound control panel, but I haven't found a way to do it in Lubuntu, even after installing Alsa Mixer/Pulse Audio.

> 6. For reading/writing to Windows partions have you installed NTFS_3G ?

NTFS-3G uses FUSE (Filesystem in Userspace) to provide support for the NTFS
filesystem used by Microsoft Windows. It can:

 * create, remove, rename, or move files, directories, hard links, and streams;
 * read and write files, including streams, sparse files, and transparently
   compressed files;
 * handle special files like symbolic links, devices, and FIFOs;
 * provide standard management of file ownership and permissions, including
   POSIX ACLs.

Of course I've installed NTFS-3G.
But I just receive that error message when I try to mount the NTFS partition for the first time during a session.
After clicking on "Ok" button of the error message window, everything works find.

I don't receive such an error with either Ubuntu or Linux Mint.

Additional note: it used to be a data partition that I opened both from Windows and from Ubuntu. 
From more than a year my laptop is Windows free but I haven't changed this partition type (NTFS) because I don't want to risk to lose all my data on it.

> For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

As I've mentioned in my previous post, I didn't know exactly how to deal with multiple issues/single thread/Lubuntu One Stop Thread.

Thanks for your help!

---

### Post by Paddy Landau on 2012-03-03
> **Blitz Tungsten said:**
> The mouse cursor doesn't move, the keyboard is unresponsive... I can only press on the power button.
I'm sorry, I have no clever answers for you (wish I did).

However, I can tell you how to shut down Linux cleanly when it won't respond. First, you need to find the SysRq key; if it is not marked on your keyboard, it will be the PrintScreen button.

Press the following keys, in order. You may or may not get any response from these keystrokes apart from the final one.


[LIST]
[*]Alt-SysRq-R
[*]Alt-SysRq-E (then wait a minute)
[*]Alt-SysRq-I (then wait about 10 seconds)
[*]Alt-SysRq-S
[*]Alt-SysRq-U
[*]Alt-SysRq-B (the computer will reboot; if it does not, you have to revert to the power button)
[/LIST]

To remember the order of the keys, notice that REISUB reads BUSIER backwards.

---

### Post by SteveDee on 2012-03-03
> **Blitz Tungsten said:**
> ...The problem is that I want to mute it/shut it down while I'm not using Skype.
In Ubuntu you can easily do it in the sound control panel, but I haven't found a way to do it in Lubuntu, even after installing Alsa Mixer/Pulse Audio....

Sorry, I'm being a bit dim here, but are you saying the mic mute function in alsamixer is not working?

Just to be clear, in alsamixer:-
 - Press F5 to display all controls
 - right-arrow to highlight the mic
 - press m to mute

---

### Post by Blitz Tungsten on 2012-03-03
> **Paddy Landau said:**
> I'm sorry, I have no clever answers for you (wish I did).

However, I can tell you how to shut down Linux cleanly when it won't respond. First, you need to find the SysRq key; if it is not marked on your keyboard, it will be the PrintScreen button.

Press the following keys, in order. You may or may not get any response from these keystrokes apart from the final one.


[LIST]
[*]Alt-SysRq-R
[*]Alt-SysRq-E (then wait a minute)
[*]Alt-SysRq-I (then wait about 10 seconds)
[*]Alt-SysRq-S
[*]Alt-SysRq-U
[*]Alt-SysRq-B (the computer will reboot; if it does not, you have to revert to the power button)
[/LIST]

To remember the order of the keys, notice that REISUB reads BUSIER backwards.

Thanks, the REISUB "procedure" works!
My main concern is that it shouldn't happen while using L/Ubuntu.
I'm looking for stability, no need to reboot, no system freezing, etc. and it happens few times a week to reboot the PC due to (I suppose) Flash Player...
I mean, 10 years old Windows XP was more stable.
And I truly hate to say that.

Since I'd like to improve Ubuntu/Lubuntu, how can I look for these kind of errors? Is there any system log for them?

---

### Post by marinara on 2012-03-03
the lockup problem could also be temperature-related or lack of memory. would turning off hardware accel help? I donno

also the drag and drop bug is here
[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/878993](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/878993)

---

### Post by Blitz Tungsten on 2012-03-03
> **SteveDee said:**
> Sorry, I'm being a bit dim here, but are you saying the mic mute function in alsamixer is not working?

Just to be clear, in alsamixer:-
 - Press F5 to display all controls
 - right-arrow to highlight the mic
 - press m to mute

I've installed the following packages:

- alsa-base
- alsa-utils
- alsamixergui
- pulseaudio

and others (various libsound, audacious-plugins).

In the volume control indicator (in the task bar) I can only set the volume/mute the speakers.

If I open alsamixergui F5 isn't doing anything.

I have two columns: Master and Capture.

If I lock caputre and I close the alsamixergui, the change doesn't apply.

What packages am I missing?

---

### Post by Blitz Tungsten on 2012-03-03
> **marinara said:**
> the lockup problem could also be temperature-related or lack of memory.  I donno

It occured in various circumstances.

Many of them while the laptop was relatively "cold" (turned on since few minutes) and while I kept open only a few tabs: 5-6, with one containing a flash video and the others were forums, GMail and stuff like that.

Mind that I have 2GB (DDR2), AMD Turion ML-37 2.0 GHz and Lubuntu amd64 version.

I could accept it if I was processing an heavy simulation in python, 3D plots, 4-5 pdfs opened, 10 Chromium tabs, Skype, emacs and so on, but with just 5-6 tabs in Chromium... It's a bit puzzling to me.

---

### Post by Paddy Landau on 2012-03-03
This is certainly puzzling, I agree.

You have 2Gb RAM -- Lubuntu should fly like a bird on that. Is it fast?

I wonder if your swap is large enough? Please open either Disk Utility or GParted to see how large your swap partition is. It should, ideally, be at least the same size as your RAM (2Gb).

---

### Post by anselm on 2012-03-03
> 5) Few tabs with Flash (YouTube, ESPN.com, ecc.) and... the system freezes.
I've to manually reboot. And it doesn't happen when it exceeds the memory available. It just happens even if I have one YouTube tab and few other random tabs.
It was happening to me also when I was using Ubuntu.
Sometimes it happens twice a day.
It happens with Chromium, I don't know if it occurs in Firefox too.
I've the latest version of Flash (64-bit) and lately, with Chromium 17, I've started experiencing a lot of "Aw, snap!" tabs and I've to reload too often...
What am I doing wrong?

This is happening in Windows also, my son uses windows vista on his laptop he gets a lot of "Aw, snap!" too.

With Chromium I get aw snap every now and then firefox no problems.

---

### Post by Blitz Tungsten on 2012-03-03
> **Paddy Landau said:**
> This is certainly puzzling, I agree.

You have 2Gb RAM -- Lubuntu should fly like a bird on that. Is it fast?

I wonder if your swap is large enough? Please open either Disk Utility or GParted to see how large your swap partition is. It should, ideally, be at least the same size as your RAM (2Gb).

Yes, it boots pretty fast and I've no speed issues heavy using Octave/Matlab, while doing reading multiple pdfs, compiling large documents in LaTeX and surfing on the internet.

My swap file is extactly 2GB. Matter of fact I can successfully hibernate my session and get back on it.

---

### Post by Paddy Landau on 2012-03-03
> **Blitz Tungsten said:**
> My swap file is extactly 2GB.
In that case, that rules out swap.

> **anselm said:**
> This is happening in Windows also...
With Chromium I get aw snap every now and then firefox no problems.
Ah, that points to a Chromium problem. I don't use it; I use Firefox.

Try Firefox instead of Chromium for a couple of days to see whether or not it has the same problem.

---

### Post by SteveDee on 2012-03-03
> **Blitz Tungsten said:**
> ...If I open alsamixergui F5 isn't doing anything....

Open LXTerminal & type: alsamixer
...then as per my previous post

---

### Post by Blitz Tungsten on 2012-03-03
> **SteveDee said:**
> Open LXTerminal & type: alsamixer
...then as per my previous post

When I open the alsamixer the Mic is already mute, if "MM" stands for mute. 

But if I open the "Sound Recorder", wheter the Mic is set on "MM" or on "00" it starts recording.
So it seems like that the Mic is always on.

---

### Post by Blitz Tungsten on 2012-03-03
> **Paddy Landau said:**
> In that case, that rules out swap.


Ah, that points to a Chromium problem. I don't use it; I use Firefox.

Try Firefox instead of Chromium for a couple of days to see whether or not it has the same problem.

Somehow I hope it's a "fail" on the Chromium side of the equation rather than on the Ubuntu one!

---

### Post by ssokolow on 2012-06-05
> **Blitz Tungsten said:**
> The problem is that when I try to drag a file from an archive to the desktop/any other folder, there is nothing I can do. 
Lubuntu freezes, I've even tried to wait for hours but nothing can be done. The mouse cursor doesn't move, the keyboard is unresponsive... I can only press on the power button.

The mouse cursor not moving is a new one, but on every Lubuntu machine I've worked on, I've encountered that problem.

On my computer, the mouse cursor does move and the problem is in how drag-and-drop is implemented. (Something goes wrong and file-roller ends up not letting go of its exclusive grab on the mouse but also not listening for input from it)

Killing file-roller (eg. via SSH) makes the desktop responsive again on my system. I don't know enough about your system to tell you whether it would also apply in your case or whether the frozen mouse pointer indicates something more is going on.

---

