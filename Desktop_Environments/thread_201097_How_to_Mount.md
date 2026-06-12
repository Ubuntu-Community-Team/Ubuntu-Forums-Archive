---
title: "How to Mount"
date: 2006-06-21
forum: Desktop Environments
---

### Post by Kurt_Alan on 2006-06-21
**[SIZE="5"][COLOR="Black"][/COLOR][/SIZE]**


I successfully save a text document.  However, my floppy drive fails to open with this error message:

Unable to mount the floppy drive.
mount: /dev/fd0 is not a valid block device
could not execute pmount

What do I do? Please give exact steps.  Thanks.

I'm just learning about mounting devices. What is this error message telling me?

---

### Post by gborbolla on 2006-06-21
How are you mounting the floppy? Are you executing any command?

---

### Post by Kurt_Alan on 2006-06-21
**[COLOR="Black"][/COLOR]**

Thanks, G. Borbolla.
I am mounting from GUI (rt. click floppy menu).  And I've tried this mount command:

sudo mount /etc/fstab/floppy

And I get "Can't find."

When I do:

cat /etc/fstab

I find that there is no floppy drive listed.  Does this mean that I am missing a mount point and I need to execute a command to mount?

---

### Post by nkassi on 2006-06-22
if you type dmesg | grep fd you should see information about you floppy disk. You should the see on the second line (might be different for you) : 
 [4294691.884000] Floppy drive(s): **fd0** is 1.44M

fd0 is my floppy

the mount it like this :
mount /dev/fd0 /media/floppy

make sure /media/floppy exist. Then add this to /etc/fstab:
/dev/fd0      /media/floppy          vfat    defaults              0       0

Hope that works

Nic

---

### Post by tonyr on 2006-06-22
My **fstab** entry is
```

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

I think it has to be like this to allow any user to mount it. Otherwise I think
only **root** can mount it.

---

### Post by BobSongs on 2006-06-22
[QUOTE=nkassi]the mount it like this :
mount /dev/fd0 /media/floppy

make sure /media/floppy exist. Then add this to /etc/fstab:
/dev/fd0      /media/floppy          vfat    defaults              0       0[/QUOTE]That worked with my friend's system. Excellent! Thanks.

Question: how do I set it (if possible) for the floppy to mount on boot up? Or is keeping it unmounted a security issue?

I tried creating a launcher on the desktop with this code:```
gksudo mount -t vfat /dev/fd0 /media/floppy
```but that failed miserably. :-?

Does anyone know a way to keep the floppy mounted with each boot, or a way to create a launcher?

Thanks

---

### Post by Kurt_Alan on 2006-06-26
[QUOTE=nkassi]if you type dmesg | grep fd you should see information about you floppy disk. You should the see on the second line (might be different for you) : 
 [4294691.884000] Floppy drive(s): **fd0** is 1.44M

fd0 is my floppy

the mount it like this :
mount /dev/fd0 /media/floppy

make sure /media/floppy exist. Then add this to /etc/fstab:
/dev/fd0      /media/floppy          vfat    defaults              0       0

Hope that works

Nic[/QUOTE]


**[SIZE="5"][COLOR="Black"][/COLOR][/SIZE]**

I typed the dsmeg command. It appears that my floppy drive does not exist or is not recognized.  How do I do this at a terminal?

 Then add this to /etc/fstab:
/dev/fd0      /media/floppy          vfat    defaults              0       0

Do I first cd to /etc/fstab ??  Please give me the steps to add this drive.

---

### Post by tonyr on 2006-06-26
First, let's make sure Ubuntu thinks the floppy drive is really there.  Go to
**System->Administration->Device Manager**.  You get a split window,
with a list of hardware devices in the left side.  Scroll down the left side and look for
a line that says **Platform Device (floppy.0)**.  The next line should be indented,
showing **PC Floppy Drive**.  If neither of those lines are anywhere in the list,
look for anything that has **(floppy.0)**.  If it's still not there, either your machine
does not have a floppy drive, or it is broken or disconnected.  

It won't do any good to make entries for a floppy drive in any files if the system doesn't
see one.

---

### Post by bartbes on 2006-06-28
just drop the noauto and it will mount on bootup

Old fstab entry:```
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

New one:```
/dev/fd0        /media/floppy0  auto    rw,user  0       0
```

---

### Post by Kurt_Alan on 2006-06-29
**[SIZE="5"][/SIZE]**

My floppy drive failure to access on 3 out of 4 Ubuntu installs is very frustrating and I'm returning to this problem.  As a teacher, this failure continues to prevent me from using Linux in the classroom, which I'm trying to do . . .

To recap:

Re: tonyr's comment, yes, when I go to Device Manager, I DO FIND unindented:
Platform Device (floppy.0) and I DO FIND indented:
PC Floppy Drive.

However, when I go to terminal* cat /etc/fstab* no floppy device is listed.
And when I try to mount the floppy from the GUI floppy menu, I get:
mount: /dev/fd0 is not a valid block device

error: could not execute pmount

Where do I go from here? Please give exact steps. . .  Thanks.

---

### Post by tonyr on 2006-06-29
Forgive me for sounding ignorant or stupid, but I want to make certain of my footing here.

What kind of machine are you using? Is your floppy drive internal or external?

When you say **I am mounting from GUI (rt. click floppy menu)**, what floppy
menu are you talking about?  Did you get there from some other menu? From
some other GUI?  From a file browser? Is there a floppy icon on your desktop?

In a terminal do
```

ls -l /dev/fd*

```
Mine shows
```

lrwxrwxrwx 1 root root     13 2006-06-29 05:50 /dev/fd -> /proc/self/fd
brw-rw---- 1 root floppy 2, 0 2006-06-29 12:50 /dev/fd0

```
What does yours show?

Is there actually a floppy in the drive when you try to mount?  Do you know what
is supposed to be on it, or is it new or blank?

With a floppy in the drive, in a terminal do
```

dd if=/dev/fd0 of=rawfloppy.dat bs=512

```
What happens?  This is supposed to read the floppy in a raw data fashion
without regard to filesystem or formatting.

---

### Post by Kurt_Alan on 2006-06-29
**[COLOR="Black"][/COLOR]**

Hi Tonyr.  I will answer all your questions and try your ideas.

1. I assembled my pc, running 32 bit AMD XP processor.  The floppy drive is internal.  I have also attached a USB external floppy drive, which does appear in Nautilus < Computer (I know this because it is designated "external."). It also fails with same error messages (See my earlier post).  To simplify matters, I have disconnected this drive and am troubleshooting the internal drive only.

2. When I say "I am mounting from the GUI" I am referring to:
Home Folder (Nautilus) < Computer < Floppy Drive < rt. click to menu "Mount Volume < left click on same.

3. **There is no floppy icon on my desktop.

4. When I do [Code]  ls -l /dev/fd*
 
     I get [Code] lrwxrwxrwx 1 root root     13 2006-06-29 04:24 /dev/fd -> /proc/self/fd
brw-rw---- 1 root floppy 2, 0 2006-06-29 04:24 /dev/fd0

5. When I do: [Code]  dd if=/dev/fd0 of=rawfloppy.dat bs=512

I get: [Code] /dev/fd0': No such device or address

---

### Post by Kurt_Alan on 2006-06-29
tonyr, one item to add:

BTW, in Device Manager, I do find UNINDENTED Platform Device (floppy.0) and INDENTED PC Floppy Drive

---

### Post by tonyr on 2006-06-29
What about the floppy disk (the media itself)?

---

### Post by Kurt_Alan on 2006-06-30
The media itself is a new floppy.  Access to the floppy fails when I try to Format from Nautilus.

---

### Post by tonyr on 2006-06-30
You should look in /var/log/messages and all of its brothers. There are several. In my 
/var/log directory:
/var/log> ls -l mess*
-rw-r----- 1 root adm 589651 2006-06-30 07:55 messages
-rw-r----- 1 root adm 841241 2006-06-26 10:13 messages.0
-rw-r----- 1 root adm  22765 2006-06-19 15:18 messages.1.gz
-rw-r----- 1 root adm  40316 2006-06-12 18:05 messages.2.gz
-rw-r----- 1 root adm  49358 2006-06-05 19:14 messages.3.gz

If there ever was a floppy drive recognized, in there somewhere should be a line like the
one that you looked for in the **dmesg** output:
```

Floppy drive(s): fd0 is 1.44M

```

Are you dual booting with Windows? If so, does Windows see the floppy drive (and the external drives) and access it ok?

---

### Post by Kurt_Alan on 2006-06-30
****

1. This is my dmesg output:

[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179573.064000] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=1
[17179593.368000] Floppy drive(s): fd0 is 1.44M
[17208659.632000] end_request: I/O error, dev fd0, sector 0
and I/O error continues for about 50 lines.

2. I am not dual-booting with Windows.

3. I will get back to you on the /var/log directory.

---

### Post by Kurt_Alan on 2006-06-30
I have searched /var/log directory and can't find anything related to a floppy drive; on the other hand, I don't know exactly what I'm looking for.

At this moment I do not know what the problem is or how to solve it.

---

### Post by tonyr on 2006-07-01
[QUOTE=Kurt_Alan]I have searched /var/log directory and can't find anything related to a floppy drive; on the other hand, I don't know exactly what I'm looking for.

At this moment I do not know what the problem is or how to solve it.[/QUOTE]

You would be looking for the words **floppy**, **Floppy** or **fd0** in any
file whose name starts with **messages**.  Some of them may be "gziped", (name
ends with **gz**, in which case they would need to be "gunziped" with a terminal
command line, for example: **sudo gunzip  messages.1.gz**.

I have been searching the forums for any information on this problem and not
finding very much.  

Some suggest that power management (acpi) sometimes interferes with floppy device
operation.  This can be tested by editting the file **/boot/grub/menu.list** as root, 
finding the lines that start with **kernel**, adding "acpi=off" to them, and rebooting.

Some suggest that the floppy drive could be bad or that
the floppy cable is poorly connected.  Has the floppy drive ever worked? 
You would have to open the machine and check the floppy cable  to
check this and/or replace the drive.

Some suggest that there may be a problem in some versions
of the operating system.  What kind of machine do you have and what version of 
the operating system do you have? (in a terminal do **uname -r**).  The relevant
OS version names would have **x64** or **smp** in them.  The only way I know
to deal with this is to reinstall Ubuntu with the **x86** version (I am assuming
that you are running this on an x86 based machine and not a Mac).

I'm sorry that I can't be more help.   There does not seem to be a standard
answer to this problem, and the only way to figure it out that I know is to go
through this kind of investigation/debug process.

---

### Post by Kurt_Alan on 2006-07-01
**[SIZE="5"][COLOR="Black"][/COLOR][/SIZE]**

tonyr, even though I do not have a solution now, thanks for all your help.  Before following up your suggestions (Yes, my machine is 386), I'm trying a different strategy.  Since I have floppy drive failure on 3 out of 4 clean installs of Ubuntu, this suggests a shared OS problem of some kind.  

To find out if it's an Ubuntu OS problem, I'm doing a clean install of Damn Small Linux, which I want to try anyway, and RHEL and check my drive functionality then.  If I still have any floppy drive access problems, then I'll swap hardware.  I'll let you know what happens.

I could use a USB flash drive but, as a teacher, my students can only use floppies, so I have to have fdd functionality.

---

### Post by Kurt_Alan on 2006-07-01
I can also try a clean install of "Dapper Drake" from cd, which I have from linuxcd.org, rather than from .iso, which are my present installs.

---

### Post by tonyr on 2006-07-01
Good luck.  I'd be interested to hear the solution, should you discover one.

---

