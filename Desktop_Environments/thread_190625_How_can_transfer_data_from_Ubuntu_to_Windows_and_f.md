---
title: "How can transfer data from Ubuntu to Windows and from Windows to Ubuntu?"
date: 2006-06-06
forum: Desktop Environments
---

### Post by sidy on 2006-06-06
Hi there,

I have ubuntu 6.06 installed and also windows xp.

HOW CAN I SHARE THERE DATAS?

I need full commands, because I have never done it before?

Thank you!

---

### Post by NoUse on 2006-06-06
You can install a driver on Windows so you can read your ext3 (Linux) partitions.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

As for writing to Windows from Linux, if the drive is formatted as NTFS, there is no safe way to do that.

---

### Post by siorai on 2006-06-06
The easiest that comes to my mind would be to have a FAT32 partition. That will give you the ability to read/write to it in both Ubuntu and Windows. I can't give detailed instructions, because I wouldn't want to forget something vital and screw it up. I'm certain there are people with much more knowledge than myself that would be more than happy to help.

---

### Post by sidy on 2006-06-06
[QUOTE=NoUse]You can install a driver on Windows so you can read your ext3 (Linux) partitions.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

As for writing to Windows from Linux, if the drive is formatted as NTFS, there is no safe way to do that.[/QUOTE]

I didn't say before, but I have amd 64 and on this link you gave me is for x86 (I don't know the meaning).

What would be the procedure for amd 64?
So, on linux I could copy data from windowns and on windons copy to linux.

Or Would would be the commands to do so?

rgds

---

### Post by Ramses de Norre on 2006-06-06
It's a driver to install on windows. Are you running windows 64bit? It's not because you've got a 64bit cpu that windows is running 64bit, every normal windows install is 32 (and thus uses x86 software).

---

### Post by sidy on 2006-06-06
[QUOTE=Ramses de Norre]It's a driver to install on windows. Are you running windows 64bit? It's not because you've got a 64bit cpu that windows is running 64bit, every normal windows install is 32 (and thus uses x86 software).[/QUOTE]

Fine!

:?: Now, I have ext2fs installed, but how can I use it? How can I go to linux datas from windons?

:?:  Or, How can I go from linux to windows, please?

To be able to copy and transfers datas?

rgds

---

### Post by Ramses de Norre on 2006-06-06
Go to the configuration screen and there is an icon for the driver, when you click on it you can define drive letters for the linux partitions. Choose a letter that's not used for removable devices yet to avoid conflicts.

Linux to windows: there is no save way yet to write on ntfs from linux (it's in development though.. )

---

### Post by sidy on 2006-06-06
[QUOTE=Ramses de Norre]Go to the configuration screen and there is an icon for the driver, when you click on it you can define drive letters for the linux partitions. Choose a letter that's not used for removable devices yet to avoid conflicts.[/QUOTE]

Perfect!!!
Thank you very much.
On windows, I can transfer data from linux to windows and tranfer it back.

[QUOTE=Ramses de Norre]Linux to windows: there is no save way yet to write on ntfs from linux (it's in development though.. )[/QUOTE]

Now, on linux, would you know commands of trying to do the same?

And, another issue.
How can I make the audio on windows starts working? Because it works fine on ubuntu.
I have no idea of what driver or anithing!

rgds.

---

### Post by NoUse on 2006-06-06
There isn't a safe way to do Linux->Windows NTFS yet.  I use an USB2.0 External drive formatted to FAT32 to share data.

---

### Post by Ramses de Norre on 2006-06-06
Read the thread: already two times said that there is no safe way..

If you really want to try search the forums for fuse but I wouldn't use it if you've got data of any importance on the drives.

---

### Post by sidy on 2006-06-06
[QUOTE=Ramses de Norre]Read the thread: already two times said that there is no safe way..

If you really want to try search the forums for fuse but I wouldn't use it if you've got data of any importance on the drives.[/QUOTE]

Understood that, sorry.

About the sound issue for windows xp. Do you know how to fix it? How can I make the audio on windows starts working? Because it works fine on ubuntu.
I have no idea of what driver or anything to get sound or audio on windows.

Thank you once more.

---

### Post by jgcamp99 on 2006-06-08
Yep, a FAT32 transitory partition/hdd is the route I go, nothing stays on the partition/drive for very long.

---

### Post by shaneOj on 2006-06-08
if you just want to copy files from win to ubuntu, even with ntfs file format, you can.

which partition did you install win? you just have to mount it in any directory you choose to in your ubuntu..

---

