---
title: "Ubuntu 12.04 VMware image - low disk space warning"
date: 2012-06-02
forum: Desktop Environments
---

### Post by MCV44 on 2012-06-02
I recently installed 12.04 in my VMware environment and have been running it for about 3 weeks.  Everything is running great except for this error I'm not getting whenever I attempt to extract .rar files.  I get a Low Disk Space warning on the volume "filesystem root" but when I elect to examine it, it's nowhere near capacity.  I have a mount point set for another virtual drive where I store all my downloads and this must somehow be causing the issue.  The thing is, this was never a problem prior to 12.04.  Please see image below and PLEASE let me know if anyone can think of why this is happening now.

Thanks in advance.

[IMG]http://home.comcast.net/~mvaia/lowdiskspace.png[/IMG]

---

### Post by Paddy Landau on 2012-06-03
When you attach a screen-shot, please attach it the normal way, because the screen-shot is so wide that I have to scroll my screen left-and-right in order to read your problem.

Are you running standard Ubuntu 12.04?

I'm not sure what makes you think the system is nowhere near capacity. According to your own screen-shot, root ("/") is 100% full. The space is only 21.8Gb, which is plenty for root but perhaps not for data.

Is your /home on  a separate partition?

Try deleting all files in /tmp and reboot.

---

### Post by VanillaMozilla on 2012-06-03
The 100% doesn't mean what it seems.

In a terminal window type the command
df --human-readable
and post the results.  That will better show you what's available in each partition.

---

### Post by MCV44 on 2012-06-12
> **VanillaMozilla said:**
> The 100% doesn't mean what it seems.

In a terminal window type the command
df --human-readable
and post the results.  That will better show you what's available in each partition.

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       7.5G  4.4G  2.8G  62% /
udev            7.9G  4.0K  7.9G   1% /dev
tmpfs           3.2G  736K  3.2G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            7.9G  264K  7.9G   1% /run/shm
/dev/sdb1       256G  6.9G  237G   3% /extstorage

---

### Post by MCV44 on 2012-06-12
> **Paddy Landau said:**
> When you attach a screen-shot, please attach it the normal way, because the screen-shot is so wide that I have to scroll my screen left-and-right in order to read your problem.

Are you running standard Ubuntu 12.04?

I'm not sure what makes you think the system is nowhere near capacity. According to your own screen-shot, root ("/") is 100% full. The space is only 21.8Gb, which is plenty for root but perhaps not for data.

Is your /home on  a separate partition?

Try deleting all files in /tmp and reboot.

To clarify, I have a local drive (root) with a total capacity of 21.8GB, but I also have a secondary drive mounted at "/extstorage", with a total capacity of 250GB+ for all my data.  Even though there is PLENTY of space on my mount point, I can't seem to expand compressed files without getting these warnings (which are always followed by decompression failure).  Am I just missing something here?

---

### Post by Paddy Landau on 2012-06-13
> **MCV44 said:**
> To clarify, I have a local drive (root) with a total capacity of 21.8GB, but I also have a secondary drive mounted at "/extstorage", with a total capacity of 250GB+ for all my data.  Even though there is PLENTY of space on my mount point, I can't seem to expand compressed files without getting these warnings (which are always followed by decompression failure).  Am I just missing something here?
It may be that the decompression is taking place in your [FONT=Lucida Console]/tmp[/FONT] folder, which of course is on your almost-full root drive.

Try the following, which tells your computer to use a temporary folder in your extra storage partition instead of on your root drive:

[LIST]
[*]Create a folder [FONT=Lucida Console].tmp[/FONT] in your extra storage partition. Either use Nautilus or enter the following command in a terminal.```
mkdir /extstorage/.tmp
```
[*]Edit the file [FONT=Lucida Console].profile[/FONT] in your home folder. At the very end of the file, add the following lines:```
if [ -d '/extstorage/.tmp' ]
then
        TMPDIR='/extstorage/.tmp'
fi
```
[*]Log out; log in again (or just reboot).
[*]Try decompressing your files now.
[/LIST]
If that works, my theory is correct.

---

### Post by MCV44 on 2012-06-18
Thanks for the tip but I did exactly what you said and it's still coming up with low disk space warnings after decompressions.  Any other thoughts?

---

### Post by Paddy Landau on 2012-06-19
The big point is that your root drive is full. The real solution, rather than the workarounds that we've been talking about, is to fix that problem.

Your root is on /dev/sda1, which is where your /home appears to be.

Your /extstorage is on /dev/sdb1.

Usually, one puts /home on the separate partition (in your case, on a separate drive), because that's where the data goes.

Therefore, my suggestion is to move the entire contents of your /home to /extstorage. This is a fairly simple task, even if you have multiple users, but made slightly more complex if you have an encrypted folder.

If you know how to do this, go ahead and do it; if you don't, let us know whether or not you have an encrypted folder; also post your file [FONT=Lucida Console]/etc/fstab[/FONT] here (please remember to paste the contents between [FONT=Lucida Console][noparse]```
[/noparse][/FONT] and [FONT=Lucida Console][noparse]
```[/noparse][/FONT]); and I'll give you instructions.

---

### Post by SrijanM on 2012-06-28
Hi!
I am facing the same problem.I have installed Ubuntu 12.04 through wubi in the same drive as my Windows. The size of the drive is 640GB and around 330GB of it is free but still it gives me this error with only 15MB left.

The output of my df --human-readable is

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       18G   17G   90M 100% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           778M  908K  777M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  532K  1.9G   1% /run/shm
/dev/sda2       577G  333G  245G  58% /host
```

What should i do to fix this?

---

### Post by Paddy Landau on 2012-06-29
SrijanM, this is not quite the same problem. You are running WUBI, not VMware. Ideally, this should be a new thread, but I'll answer here anyway.

When you install WUBI, it sets aside a fixed area of your disk for Ubuntu. Although your WIndows drive is 640Gb, in  your case only 18Gb has been set aside for Ubuntu.

The first line of your output shows this:
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       18G   17G   90M 100% /
```Your Ubuntu "drive" (actually a virtual partition) is 18Gb, with over 17Gb used and just 90Mb free.

Unfortunately, there is no easy way to increase the partition size in WUBI (although with a standard installation of Ubuntu, it would have been easy).

I suggest you try a solution similar to [post=12038691]post #8[/post]: move your data (or at least your big data) from [FONT=Lucida Console]/home[/FONT] to a new folder in [FONT=Lucida Console]/host[/FONT] (which, I think, is your Windows drive). This is hardly an ideal solution, but at least it will solve your problem for the time being.

For future note: WUBI is ideal for experimenting with and testing Ubuntu to see whether or not you like it, but WUBI's limitations and susceptibility to fatal failures make it unsuitable for long-term use.

---

### Post by MCV44 on 2012-07-05
> **Paddy Landau said:**
> The big point is that your root drive is full. The real solution, rather than the workarounds that we've been talking about, is to fix that problem.

Your root is on /dev/sda1, which is where your /home appears to be.

Your /extstorage is on /dev/sdb1.

Usually, one puts /home on the separate partition (in your case, on a separate drive), because that's where the data goes.

Therefore, my suggestion is to move the entire contents of your /home to /extstorage. This is a fairly simple task, even if you have multiple users, but made slightly more complex if you have an encrypted folder.

If you know how to do this, go ahead and do it; if you don't, let us know whether or not you have an encrypted folder; also post your file [FONT=Lucida Console]/etc/fstab[/FONT] here (please remember to paste the contents between [FONT=Lucida Console][noparse]```
[/noparse][/FONT] and [FONT=Lucida Console][noparse]
```[/noparse][/FONT]); and I'll give you instructions.

Thanks for your help.  Unfortunately, I'm new[er] to Linux and don't have a clue how to accomplish this.  I do not have an encrypted folder and there is only one user folder.

Sorry for the delay in response.  I do appreciate all your help with this!

---

### Post by Paddy Landau on 2012-07-06
First, I need to see your file system table (fstab).

[LIST=1]
[*]Open your Text Editor.
[*]Open [FONT=Lucida Console]/etc/fstab[/FONT] (File > Open > File System > [FONT=Lucida Console]etc[/FONT] > [FONT=Lucida Console]fstab[/FONT] > Open).
[*]Select everything (Edit > Select All).
[*]Copy (Edit > Copy).
[*]Come back here and paste the contents into a new reply.
[*]Highlight the part that you just pasted, and press the [FONT=Lucida Console]#[/FONT] button in the toolbar (that will surround the code with [FONT=Lucida Console][noparse]```
[/noparse][/FONT] and [FONT=Lucida Console][noparse]
```[/noparse][/FONT]).
[/LIST]
I also need to see your partitioning.

[LIST=1]
[*]Open a Terminal.
[*]Type (or cut-and-paste) the following command, which will prompt you for your password:```
sudo parted --list
```
[*]Using your mouse, highlight the response; right-click and Copy.
[*]Paste the results into your new reply.
[*]Highlight the part that you just pasted, and press the [FONT=Lucida Console]#[/FONT] button in the toolbar (that will surround the code with [FONT=Lucida Console][noparse]```
[/noparse][/FONT] and [FONT=Lucida Console][noparse]
```[/noparse][/FONT]).
[/LIST]
Finally, submit your reply.

---

