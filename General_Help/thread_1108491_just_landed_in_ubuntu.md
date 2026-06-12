---
title: "just landed in ubuntu"
date: 2009-03-27
forum: General Help
---

### Post by ash_pro on 2009-03-27
wow . . this is really good for free software  . .feels really cosy

Install on a Dell Inspiron 6400


till now no errors what so ever, all the drivers were either detected or were downloaded afterwards ( broadcom wifi, nvdia 7300, etc)

even the front panel buttons work . . wow

3 issues

1) The grub shows 2 entries for ubuntu along with Xp
2) Was looking for an alternate browser other than fire fox (dont getme wrong . . i love firefox . . but was looking for a light weight browser also)
3) My m3u playlist created on xp arent working in ubuntu ( after mounting the drive )  . . i think this is a path name issue . . . any suggestions how to fix this . . ? ?  ( pleasae point me to the right thread . . i dont wanna double post)

Big hug to Canonical . . . keep up the good work  . . . 

also any suggestions on how to get started on learning the command line for ubuntu ? ?

Thanks all

ubuntu rocks:guitar::guitar:

---

### Post by dhughes on 2009-03-27
> **ash_pro said:**
> wow . . this is really good for free software  . .feels really cosy

Install on a Dell Inspiron 6400


till now no errors what so ever, all the drivers were either detected or were downloaded afterwards ( broadcom wifi, nvdia 7300, etc)

even the front panel buttons work . . wow

3 issues

1) The grub shows 2 entries for ubuntu along with Xp
2) Was looking for an alternate browser other than fire fox (dont getme wrong . . i love firefox . . but was looking for a light weight browser also)
3) My m3u playlist created on xp arent working in ubuntu ( after mounting the drive )  . . i think this is a path name issue . . . any suggestions how to fix this . . ? ?  ( pleasae point me to the right thread . . i dont wanna double post)

Big hug to Canonical . . . keep up the good work  . . . 

also any suggestions on how to get started on learning the command line for ubuntu ? ?

Thanks all

ubuntu rocks:guitar::guitar:

1) Probably a recovery option
2) Opera, Epiphany
3) Amarok or Songbird?

---

### Post by drs305 on 2009-03-27
Allow me to be the first to welcome you to the Ubuntu forums - well ok, the second.

The two copies of ubuntu are probably the normal version and a "recovery" mode. You probably want to keep both available for use. You can set up grub to automatically boot the normal mode and have a delay which gives you time to select the recovery mode if necessary. It's also possible you have two ubuntu kernels installed (the original one from your initial install and an update).

Grub has a lot of configuration options, including whether or not you see the menu, for how long, which kernel to boot, etc. I recommend using StartUp-Manager, a gui editing tool for grub's menu.lst
I've written a guide that tells how to install StartUp-Manager and explains the various options. The link is in my signature line.

---

### Post by Dr Small on 2009-03-27
1.) There should be 2 Ubuntu entries. One boots to multi-user mode (your desktop) and the second one is Recovery mode, which boots to Single User mode (into the root account).

2.) My suggestions on lightweight browsers will not fascinate you, so I'll not mention any! :D

3.) I would say that it is a path issue too. Just edit the file and change the paths, as that should correct the problem.

---

### Post by ash_pro on 2009-03-27
thanks guys . . . thanks for replying

wow the community is oozing so much love . . . 

i wish i would have switchied earlier . . . (actully i still am using xp . . but maan  it feels good to be free from vista . . . )

regarding the entries in grub  . . 
actually there are 4 ubuntu entries 2 normal and 2 recoveries
they seem to be exact copy of eah other and then finally there is xp

the media player im using is rythembox player 

the m3u playlist file has filename as follows

one example

&#65279;E:\Mp3s\stuff i listen\Simple Minds - Don't You Forget About Me.mp3


what part of this should i edit to make the file playable ?

thanks again . . .

---

### Post by jeremyjjbrown on 2009-03-27
> **ash_pro said:**
> w

also any suggestions on how to get started on learning the command line for ubuntu ? ?

ubuntu rocks:guitar::guitar:

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

helped me get started with the cmd line. ;)

---

### Post by Vevmesteren on 2009-03-27
the easiest way would be, open up a nautilus (*File Explorer) window, navigate to your music. The address bar up top will then give you your new path. After that I would suggest you use gedit (*notepad) to find and replace your paths.

Welcome to Ubuntu. Oh and you remove Micrsut installation and run XP through virtualBox or if that is not even all needed, run selected WinSoftware through. Wine, But now I am jumping ahead here maybe. Welcome to the ooze!

---

### Post by VCoolio on 2009-03-27
edit the first part of the location. Linux does not work with c:\, e:\ etc. It uses / slashes instead of \ backslashes. You can find your partitions / drives in /media/. 

A site for commandline learning: [look here]("http://www.linuxcommand.org/learning_the_shell.php").

---

### Post by drs305 on 2009-03-27
> **ash_pro said:**
> regarding the entries in grub  . . 
actually there are 4 ubuntu entries 2 normal and 2 recoveries
they seem to be exact copy of eah other and then finally there is 

If they are separate kernels everything would look about the same except for the kernel number (for instance e.g. 2.6.27-9 and 2.6.27-11). If the numbers differ, the one with the higher ending number is the newer one and should be set as the default. Most people keep one older kernel to use should they develop a problem with the newer one. The link I supplied earlier discusses your options with older kernels as they accumulate.

If the entries are indeed identical, including the words at the end of the kernel line, you can safely remove one each of the normal and recovery entries. Just make sure the kernel numbers and UUIDs (the long alpha-numeric entries) are the same.

If you have questions about it you can post the menu.lst here by typing in terminal:
```
cat /boot/grub/menu.lst
```
Copy the results here, placing it between [ code ] [ /code ] delimiters. You can insert them into the post by hitting the # symbol at the top of the post. (In the example I had to add extra spaces.)

---

### Post by ad_267 on 2009-03-27
> **ash_pro said:**
> 
the media player im using is rythembox player 

the m3u playlist file has filename as follows

one example

&#65279;E:\Mp3s\stuff i listen\Simple Minds - Don't You Forget About Me.mp3


what part of this should i edit to make the file playable ?

thanks again . . .

You can open up the playlist with the text editor and do a find and replace to replace "E:\" with the path the partition is mounted at. You can use the "mount" command in the terminal to get a list of where everything is mounted. You'll also have to replace all the back slashes with forward slashes.

---

### Post by ash_pro on 2009-03-27
:P

Thanks guys . . . 

I really appreciate your replies . . . :)

I think i got it . . . ( the path name for mp3s in the m3u file)

edit: i checked the entries in grub and they are completely identical

I also booted with the 2nd entry and it boots up fine . . .( im sure there is only one install of ubuntu in that partition)

here is the code

```
 


title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		28d80952-36f1-488d-afd3-4563b466008f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=28d80952-36f1-488d-afd3-4563b466008f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		28d80952-36f1-488d-afd3-4563b466008f
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=28d80952-36f1-488d-afd3-4563b466008f ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		28d80952-36f1-488d-afd3-4563b466008f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=28d80952-36f1-488d-afd3-4563b466008f ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		28d80952-36f1-488d-afd3-4563b466008f
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=28d80952-36f1-488d-afd3-4563b466008f ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		28d80952-36f1-488d-afd3-4563b466008f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


```

---

### Post by drs305 on 2009-03-27
What you have are two ubuntu kernels, their associated recovery modes, plus memtest86, an analysis mode. As stated earlier, many users keep at least one extra kernel in addition to the currently used one. I personally don't keep the recovery mode of the backup kernel.

A couple of things about grub's menu.lst: Just because you remove an item from menu.lst doesn't mean it is removed from your system. However, if you remove a kernel via synaptic (it would be listed as linux-image-2.6.27-7-generic) it *is* automatically removed from the menu.lst since it is no longer available.

So here are your options (these are and/or options):  a. Leave it as it is. b. Remove the entry for the -7 recovery mode. c. Remove both the -7 normal *and* -7 recovery modes. d. Remove the memtest86 entry. By 'removing' the entry, I mean the entire 4-5 line entry. 

You can also *hide* the entries by placing a # symbol at the start of the line. I do this with the "memtest" entries since I may one day want to use it, but not very likely. If I ever do, I can uncomment the entry.

If you are currently running the -11 kernel (most likely, but you can check by entering "uname-r" in a terminal), you definitely don't want to remove that one. 

When an new kernel is downloaded and installed, you will be greeted by two more entries for the new kernel, unless you alter menu.lst to limit the number of kernels you want displayed. You can do this via StartUp-Manager or manually editing the menu.lst (again see the StartUp-Manager guide).

Hope this clears up the grub entry for you.

---

### Post by ash_pro on 2009-03-27
youve explained the issue very clearly

but I myself am not that confident to make changes in the boot loader of an OS i have very less exposure to ( let alone linux, i havent touched the boot loader for windows . . idd rather use the restore CD . . i know . .i ***** out when doing these kind of things . .. :P)

So i think im gonna leave it like that . . .

Thanks again for replying . .

---

### Post by sekinto on 2009-03-27
If you don't want to mess with the bootloader you can just remove the Linux kernel 2.6.27-7-generic in Synaptic since you have 2.6.27-11-generic and  2.6.27-7-generic is no longer necessary unless you are having problems.

As for alternative browsers, I would really love to recommend Epiphany-Webkit because I love Webkit and Epiphany is a lightweight browser, but Epiphany isn't very mature yet and crashes quite a bit. Arora is a Webkit browser using the QT toolkit, it is very lightweight but lacks a lot of features. You might want to give Opera a try, there is also Konqueror and many others though.

As for music players. Banshee is my favorite, but Songbird and Amarok are also awesome.

You can download programs using the Synaptic Package Manager (System > Administration > Synaptic Package Manager).

---

### Post by Chemical Imbalance on 2009-03-27
I recommend you always have a backup kernel, just in case something goes wrong with the current kernel (for instance, installing graphics drivers, etc...).

---

### Post by ash_pro on 2009-03-28
thanks guys  . . . 

I appreciate your replies

:)

---

