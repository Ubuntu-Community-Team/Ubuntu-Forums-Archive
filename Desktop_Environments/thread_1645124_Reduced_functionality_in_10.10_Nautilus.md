---
title: "Reduced functionality in 10.10 Nautilus"
date: 2010-12-14
forum: Desktop Environments
---

### Post by ingeva on 2010-12-14
I see to my big surprise that one of the VERY useful functions in Nautilus has been disabled in 10.10.

The FTP function which enables me to open folders on my web host as if they were local, has been removed. With this function I could not only copy files both ways, but when in a hurry I could open source files on my host for editing.

The loss of this functionality is a serious setback. Using gFTP, FileZilla or some other ftp program is very much more clumsy and inefficient for copying just one or a few files, and do not give any possibility of direct editing.

Is it possible do do something about this? Is there another program that can do this?
If not I'll have go back to 9.10 ....

---

### Post by mcduck on 2010-12-14
It's still there on my 10.10. 

Have you tried Places->Connect to Server from the panel menu? I have options for both public and login FTP servers there...

---

### Post by ingeva on 2010-12-14
> **mcduck said:**
> It's still there on my 10.10. 

Have you tried Places->Connect to Server from the panel menu? I have options for both public and login FTP servers there...

There are no such options in my installation.
I have one choice: Service type: Custom location.

Whatever I enter, I get this message:

[SIZE=3]Cannot Connect to Server. You
must enter a name for the server.[/SIZE]
Please enter a name and try again.

It works in 9.10, but I don't need it there. I can just enter
the ftp address and it asks for password the first time. With
the shortcuts in Panel I have very easy access. It's been like
as long as I can remember.

---

### Post by ingeva on 2010-12-14
I found the problem.

I have installed from the server version so I won't have to spend more time than necessary. When installing the desktop over the plain server software, Nautilus
doesn't get this functionality, but it does when installing the desktop version.

This is very impractical for a lot of reasons, the two most important being:
When upgrading, several packages are installed twice. It also upgrades the existing linux core image as well as installs a newer version.
It installs a new boot image and makes it the default, even when I already have a system installed that is meant to be the default boot system.
It installs a lot of software that I don't need or want. Doesn't matter so much except it consumes a lot of time.
I have to download and burn two versions of the system, because I also have a server that doesn't need all the desktop software.

Well, the problem is solved. Let's hope that we'll get a better solution at the next revision.

---

### Post by mrfuzzemz on 2011-01-03
Hi ingeva,
I know you've now marked the thread as solved, but some have run into this problem when upgrading. What works for many, including myself, is installing the package: gvfs-backends
Hope this helps.

---

### Post by ingeva on 2011-01-04
> **mrfuzzemz said:**
> Hi ingeva,
I know you've now marked the thread as solved, but some have run into this problem when upgrading. What works for many, including myself, is installing the package: gvfs-backends
Hope this helps.
Thanks for this useful information!
A solved thread can still help someone else! :)

But a new problem has occurred with nautilus: When I tried to display hidden files, and there ARE hidden files, nautilus crashes.

Until now I have not been able to build a stable 10.10. There's alsays something seriously wrong, and it's the same on two different computers. 10.04 was completely useless; there was no communication through my wireless mouse and keyboard. I think that better quality control is needed.

---

### Post by mrfuzzemz on 2011-01-04
If you run nautilus from the command line and do the same, does any telling information show up in the shell window during or after the crash?

I'm sorry to hear about your continued Ubuntu woes. I often end up with an issue or two that I need to hunt down the solution for, but usually not as crippling as no keyboard or mouse. Have you tried plugging in the USB receiver only after the system boots?

---

### Post by ingeva on 2011-01-04
> **mrfuzzemz said:**
> If you run nautilus from the command line and do the same, does any telling information show up in the shell window during or after the crash?

I'm sorry to hear about your continued Ubuntu woes. I often end up with an issue or two that I need to hunt down the solution for, but usually not as crippling as no keyboard or mouse. Have you tried plugging in the USB receiver only after the system boots?

I'm quite sure that I didn't try from the command line, but I regenerated the system several times to do some different things, and I feel pretty sure that it didn't happen every time. But then there were other things.... In short, I spent a lot of time trying different things, but there was something wrong every time.
Nautilus didn't show me any messages; it just disappeared. I didn't check the system logs. I'm probably not knowledgeable enough to interpret them anyway. :)

About the wireless in 10.04: I won't bother to try that again, since it works again in 10.10. But I did try what you suggested about the Bluetooth USB.

The troubles with 10.10 are not THAT serious, but as long as I have a working 9.10 that does what I need, I see no reason to pursue it any more. I wasted all my spare time around Christmas trying to work it out, and now I must focus on other things.

When the next Mint comes along I'll try that. The first Mint 10 had the same problem as Ubuntu 10.04, but I like Mint as a system. Easy to set up and pleasant to use, and a few things that were improved compared to Ubuntu. However, usually I prefer setting up a minimal server system, and then install all the additions afterwards. That way I won't have to install things twice if they've been upgraded after the CD was released.

If seems now that I have things working the way I want to. Samba works nicely. NFS works nicely but is unable to share the root folders (but I can use Samba for that if both computers are running 9.10).  I'll test the unattended backup server a few days before I pack it into a dust cover and place it in the shed, hopefully to leave it there, unattended, for a couple of years .... :)
Unfortunately the huge old CRT display hasn't gone to heaven yet, but I guess there's still some room for it .... :)

---

