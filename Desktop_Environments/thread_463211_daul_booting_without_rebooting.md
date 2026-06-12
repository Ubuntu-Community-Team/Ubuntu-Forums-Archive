---
title: "daul booting without rebooting?"
date: 2007-06-03
forum: Desktop Environments
---

### Post by savagenator on 2007-06-03
hello all

i am looking for someway to load 2 OS's on boot up, and only use one at at a time. Like if i wanted vista and ubuntu daul booted, but i didnt want to reboot, i could give like 1gb to ubuntu and 2 gb to vista (i have 3gb of RAM), and then switch.

The purpose is to switch between OS's so that i could use them to their full potential, which vmware lacks.

So is this possible? does this exist?

---

### Post by linfidel on 2007-06-03
That's actually very easy, especially with as much RAM as you have - use VM software.  I've only had experience with VMWare on Windows XP, although there is that and another option for linux.

VMWare makes two free products, VMWare player and VMWare server.  I use VMWare server at work, for testing installations using clean install, etc.  The difference is that VMWare player will run a virtual machine, but won't create one.  However, there are "VM Appliances" available, many right on their site.  Creating a VM is pretty easy, too, but you can download a ubuntu appliance that is already configured, then add to it just like any other ubuntu installation.

It may sound complicated, but it's really not, and it's really very cool.  You can take a snapshot of the system, make changes, then revert back to the snapshot.  There are various networking options, between the two systems, or individually - each can access the internet normally.

You can pause a VM, move it to a completely different computer, then start it up right where it stopped.  You can copy them (one main file, + one small index, + snapshot files, if any).

There's a fairly inexpensive VMWare workstation (< $100, I think) that can create and run VMs, with multiple snapshots.

Let me know if you have questions.  Like I said, I only have experience so far with the Windows side, but I will soon try it out with Ubuntu.

---

### Post by MentholLite on 2007-06-03
Adding on to linfidel, you can also try out MS Virtual PC 2007 or MS Virtual Server 2005 R2.

Both should be free, but I am not sure whether they can support Ubuntu as guest OS.
You may want to try out before spending money on VMWare.

For me personally, I am running a Ubuntu 7.04 on VMWare workstation (slightly older version).
Works perfectly.

---

### Post by savagenator on 2007-06-03
wow, thats sounds interesting. But if i install vista, and i have an existing ubuntu installation on another patition, is it possible to use vmware to boot it up in vista?

---

### Post by linfidel on 2007-06-04
> **savagenator said:**
> wow, thats sounds interesting. But if i install vista, and i have an existing ubuntu installation on another patition, is it possible to use vmware to boot it up in vista?No, not really.  You won't need a separate partition anymore.  VMWare is a virtual partition; you can install Windows, linux, etc in it, and it looks like the only partition on the disk.  If you were to install Windows, it would think it's on the C-drive with whatever size partition is defined in VMWare.

I have Windows XP, and I've installed more copies of XP in the VMWare running on that XP, one  I use only for Quicken, and one for testing unknown programs, and another just for a clean system to troubleshoot problems.  For Windows, you have to install it just like normal.  But for Linux, you can get preinstalled "Virtual Appliances" that you can download and run in VMWare player, server, or workstation (because it's legal).  You can get specialized functions like a firewall, a development machine, a server, a workstation, etc.

---

### Post by savagenator on 2007-06-04
well, ok. I htink i might go full time linux through vista, lol. I am currently trying out vista through vmware in linux, and its decently fast, except for the fact that aero is not working, its just a tiny bit slower than if i installed it on the comptuer physically.

But it is a bummer than i can not keep the full speed of the OS, which i originally would have liked.

---

### Post by linfidel on 2007-06-04
I just re-read your original post, and see a reference to VMware; was that there all along?  If it was, I must have somehow missed it.  I suppose that's possible, it was a little late, IIRC.

I thought your original intent was more to experiment with a second OS without having to keep rebooting, which makes it a pain.  If I misread, I apologize.

---

### Post by savagenator on 2007-06-04
no no its fine, i didnt know about the vm stuff, and i didn't realize linux would still be pretty fast under vmware

although i would like beryl to work, i think i got it down....

---

### Post by linfidel on 2007-06-05
Cool.  I was pretty impressed when I tried out VMWare, and one reason for getting a new faster system with more memory was to use it more.  I'm going to try to get it to run whatever Windows programs I need under Ubuntu.  I already run Quicken in a VMWare VM, and something like that doesn't need to be fast.

---

### Post by savagenator on 2008-03-05
let me get this thread alive again. I truly think if I can boot linux, and have another operating system boot at teh same time (much like andLinux, which boots into ubuntu full fledged in windows) Then we can use maybe ubuntu, and boot BSD inside it (like wine).

Now lets say that i dont like wine, and I want to have a windows compatable software with all my settings and files (like a seperate drive with windows on it?) THen i would like to boot that while I am in linux, and open photoshop. So its like wine except its big and bulky and on another drive/partition

ranting thought....

---

### Post by dark_phantom on 2008-03-06
That andLinux looks interesting and it says it's a little different than VMware or Virtual PC.  It's sort of like wubi in a way.  Personally, I would just have Linux and use either VMware or VirtualBox to have Vista running at the same time.  Well that's what I'll do in the near future.

---

### Post by manctf8 on 2008-03-06
Microsoft ...now wash mouth ....has a site that details, step by step,  the answer to this exact question. Go to MSN website ask same question.

Worked for me. Two OS, same drive both bootable.

VMware I use now because I also needed Fortran compiler and other kinds of stuff, but I initially looked at the MSN site.

---

### Post by savagenator on 2008-03-06
Can you lead me to a link please? i hate using live.com, it never gives me what i need to know.

EDIT: do you mean [this]("http://oopsilon.com/Running-a-Windows-Partition-in-VMware")?

---

