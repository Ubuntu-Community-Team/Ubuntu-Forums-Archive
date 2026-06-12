---
title: "Plasma-desktop freezes on loss of network drive"
date: 2011-05-16
forum: Desktop Environments
---

### Post by john@ukgillies.com on 2011-05-16
Hi ,

I have a repeatable problem with the plasma-desktop.

If I lose the connection to an NFS drive then the plasma-desktop freezes.

This happens on a machine running Natty and on a machine running Lucid.
Both machines running kubuntu. Natty on an HP Laptop - Lucid on a standard PC.

Killing plasma-desktop and restarting makes no difference - the only way to recover the desktop is to put the NFS back on the network.

Any thoughts here, please?

Thanks,

John

---

### Post by NormanFLinux on 2011-05-17
Update the kernel to 2.39.0.

It should fix your freeze issue.

---

### Post by john@ukgillies.com on 2011-05-18
Thanks for this.

I have kernel 2.6.32-32-generic.

How do I get and install the kernel you suggest?

Thanks

---

### Post by NormanFLinux on 2011-05-18
Follow the directions given to install the kernel upgrade from the PPA:


1.) Add the kernel ppa and update your system:
sudo add-apt-repository ppa:kernel-ppa/ppa

sudo apt-get update

2.) Check available kernels with the command:
apt-cache showpkg linux-headers

kernel 2.6.39.0 should be in list.

3.) Run the command to install kernel 2.6.39.0:
sudo apt-get install linux-headers-2.6.39-0 linux-headers-2.6.39-0-generic linux-image-2.6.39-0-generic --fix-missing

Finally, reboot and check kernel version under System Monitor -> System tab.

Let us know if it fixes your issue.


> **john@ukgillies.com said:**
> Thanks for this.

I have kernel 2.6.32-32-generic.

How do I get and install the kernel you suggest?

Thanks

---

### Post by john@ukgillies.com on 2011-05-18
One of the delights of sharing in Ubuntu is the unexpected help you get.

Thanks for the details on updating the kernel - there was I wading through how to compile a kernel when up comes your reply! So easy!! You have saved me so much time and effort.

That's the good news - the not so good is that updating the kernel did not solve this issue.

But spurred on from your support here are some more explorations.

1. It does not seem to be plasma that freezes after all - its kickoff. Well maybe!! 

2. When I lose the nfs drive kubuntu still works. I can launch from kbd shortcuts or from a terminal (yakuake). Applications work - until I try to access the file system - then the app freezes. So for example Kate works until I try to load/save a file. Dolphin comes up grey and freezes. Plasma-desktop still works as long as I don't touch Kickoff.

3. Once the nfs drive is lost clicking on Kickoff freezes the Task bar - the kickoff menu freezes and all the items on the task bar and the plasma cashew do not respond. I still can use kbd shortcuts and terminal as in 2.

4. If I boot without connecting to the nfs drive all is well - perhaps this is obvious - but I mention here for completeness.

5. If I connect to the nfs resource *after booting* using sudo mount -a (ie nfs drive not available at boot) then I can access the nfs share and if this share then disappears my desktop functions perfectly! No freeze up!

Any further thoughts? 

Cheers,

John

---

### Post by NormanFLinux on 2011-05-18
Are you running KDE on a desktop or a netbook? They have different plasma shells for them.

I run the classic rather than the kickoff interface on my laptop.

So if its kickoff, revert to classic and see if you still get a freeze. If you don't, then keep that and don't switch it again.

Terminal - use konsole and avoid yakuake. Uninstall the latter if you don't need it. Use Dolphin to browse files mounted on your system.

Nfs - are you running Windows shares?

---

### Post by john@ukgillies.com on 2011-05-19
Both systems are desktop, and all shares are NFS not Windows.

Using the classical menu works fine - until I try to access the file system - then the app freezes.

Dolphin opens as a uniform grey block with no functionality at all. Alt F3 eventually gets a - dolphin is not responding - message. This then kills dolphin.

The question I have - what is being locked by the loss of the nfs share?

---

