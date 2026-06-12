---
title: "Vmware 5.5 on Kernel 2.6.12-10-386"
date: 2005-12-10
forum: General Help
---

### Post by Gandalf on 2005-12-10
Hello

I had an installed and fully working VMware 5.5 on my breezy, when i upgraded to the new kernel my computer started to behave very weirdly, everytime GDM starts it hold for 5 maybe 10 seconds then the whole system just freeze, the only way to restart is to turn my Laptop off...

I logged in as Recovery mode, and i gave a-x permission to /etc/init.d/vmware (i knew it's vmware because i formatted and everything was all fine untill i installed again vmware) then my system is working properly now, i tried to reconfigure it (still in recovery mode) by running /usr/bin/vmware-config.pl and when it achieved the end of the configuration the screen was filled with error messages and kernel panics and PC hanged....

is there a way i can copy/paste to you the error messages since my PC hangs when i reboot dmesg (got overwrited ?)

Thanks for any replies

---

### Post by Gandalf on 2005-12-10
am i the only one with VMware not working :O

---

### Post by sunset on 2005-12-11
I have the same problem with VMplayer.  Went back to kernel 2.6.12-9-386 so it would work.  Am also surprised not to have seen more complaints.

---

### Post by Gandalf on 2005-12-11
Glad that im not the only one :( :(

---

### Post by ajaustin on 2005-12-19
In addition to the GDM freezing with kernel 2.6.12-10-386 I was also unable to launch my Windows XP guest as it crashed on bootup.  Kernel 2.6.12-9-386 allows the XP guest to boot, I am not sure about the GDM freeze yet.

I have a support request open with VMWare on this at the moment.

Tony

---

### Post by loupy on 2005-12-19
I know that the gcc compiler with 5.10 (gcc-4.0) is different than the compiler of the kernel (2.6.12-9 or 2.6.12-10 use gcc-3.4).  I've read people have been doing an export CC=/usr/bin/gcc-3.4 prior to running vmware-config.pl and it has worked for them, but for me it never did and I always got a kernel panic.  Finally I compiled my own 2.6.14-3 kernel using gcc 4.0 and it works fine.

---

### Post by Gandalf on 2005-12-19
[QUOTE=ajaustin]In addition to the GDM freezing with kernel 2.6.12-10-386 I was also unable to launch my Windows XP guest as it crashed on bootup.  Kernel 2.6.12-9-386 allows the XP guest to boot, I am not sure about the GDM freeze yet.

I have a support request open with VMWare on this at the moment.

Tony[/QUOTE]
Compile & install the [Vanilla kernel 2.6.14](http://ubuntuforums.org/showthread.php?t=84174) it will work just fine

Good Luck

---

### Post by xraycharlie on 2005-12-19
I had the same problem.
Running the vmware-config utility again got it working for me.

Regards

---

### Post by shadow07 on 2005-12-19
I have been running 2.6.12-10-386 along with Vmware Workstation 5.5, and have not had any issues.  Well, I did when I rebuilt my laptop, and attempted to restore my VM from a ghost image (did a ghost image within the VM), changed the size of the virtual disk from 10GB to 6GB and upon reboot after the restore of the clone, WinXP would crash.  So, I just simply rebuilt it and have not had any issues with GDM freezing.

---

### Post by flargen on 2005-12-19
I experienced lockups with vmware 5.5 on kernel 2.6.12-10-k7. When i first installed vmware i was able to run it and attempt to install solaris 10, but when there was any network activity from the guest OS, the virtual machine closed itself with no warnings or errors. I am using a BT voyager network card (broadcom chipset with ndiswrapper) if it makes any difference. I found that if i disabled networking in a VM i was able to use it properly (obviously without networking though).

---

### Post by shadow07 on 2005-12-19
@flargen:

Well, I haven't seen too much success using wifi cards and workstation 5.5.  Have you posted this on VMware's user forum?

---

### Post by rjpa on 2006-01-04
I have installed VMWare 5.5 and VMWare Player both on kernel 2.6.12-10-686 and both freeze my computer and with random lockups. I have a wifi card (ipw2100) and never had the problems before. What can I do about it?

---

### Post by shadow07 on 2006-01-05
Well, I don't know what to say.  Other than I would suggest you post your issue on VMware's [forum.]("http://www.vmware.com/community/forum.jspa?forumID=19")

---

### Post by stevea1210 on 2006-01-05
I've got the same problem on one pc, but on another it works fine.  Both are running the 686 kernel.  

As posted earlier, if I reconfigure vmplayer withjout networking it works fine.  The problem pc is a wireless laptop.  That seems to be a common thing for several people.  I couldn't find anything on the vm forums about it.

I know it isn't the actual vm's. because I run the same ones on both pc's.  For some reason though, networking crashes the pc hard.  If I am logged in, and then configure vmplayer to use networking, the vm's will boot up untill they reach the point of configuring network devices, and then vmplayer crashes hard.

---

### Post by techflavor on 2006-02-09
It sure does seem like VMware is the culprit.  I have been browsing through these forums while in class and have come across many threads with people's laptops randoming freezing.

See my post in thread:  [http://ubuntuforums.org/showthread.php?p=719501#post719501](http://ubuntuforums.org/showthread.php?p=719501#post719501)

I am running VMPlayer, not VMware Workstation.  When I get home tonight, I'm going to uninstall VMPlayer and see if the problem goes away..

---

### Post by KRiSX on 2006-02-11
i figured out a very quick solution to getting VMWare 5.5 to install correctly..

i was getting the gcc problem (that the kernel was built with 3.4.5 and not 4.0.2 which was installed)...

so all i did was install gcc-3.4 in synaptic...

type "export CC=/usr/bin/gcc-3.4"

run the "vmware-config.pl" script

works great :) i am currently installing Windows XP x64 in VMWare 5.5 in Kubuntu 5.10 :D

---

