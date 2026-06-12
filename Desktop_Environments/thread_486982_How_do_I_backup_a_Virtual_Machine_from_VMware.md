---
title: "How do I backup a Virtual Machine from VMware?"
date: 2007-06-28
forum: Desktop Environments
---

### Post by diablo75 on 2007-06-28
I am wanting to wipe my hard drive clean and reinstall Ubuntu from scratch.  But I have an XP virtual machine stored on here that I'd like to backup, and then once I have Ubuntu reinstalled, I'd like to reinstall VMware and then add the previous virtual machine back into the VMware inventory.

I guessing this is probably as simple as copying a file from here to there, but I wanted to double check and see if there were any other precautions to take.

Thanks!

---

### Post by PilotJLR on 2007-06-28
You got it... back up the directory containing your VM (multiple files) and then later just copy it back and open the VM.
Once you open it on a new machine, VMware will ask you to create a new UID... which is fine. All's you have to do is click the default "Create" button when prompted.

---

### Post by Yoooder on 2007-06-28
> **PilotJLR said:**
> Once you open it on a new machine, VMware will ask you to create a new UID... which is fine. All's you have to do is click the default "Create" button when prompted.

I would recommend **not** creating a new UID if you're just backing up and restoring the VM.  Creating a new UID could/will cause the XP OS on the VM to think it's installed on a different computer, and will want to reactivate (which if done across enough machines will eventually mark your XP key as dirty).

If you are just going to preserve the vm (copy it to a backup, then back again) keep the VM's UID key.

If you are going to take 1 VM and copy it to another computer for use by 2 or more machines at once, then create a new UID.

---

### Post by diablo75 on 2007-06-28
Do I have to do anything extra to keep the UID?

Other than that little question, it looks like all I'd really have to do is copy:

/var/lib/vmware-server/Virtual Machines/*.* (Windows XP)

...to some backup folder (I'm going to use Gparted to make a temp drive to copy some stuff over to, and then wipe the boot, and reinstall.

Then copy the virtual machine files back to the folder they came from after I reinstall vmware.  Sound right?

---

### Post by Yoooder on 2007-06-29
Pretty much, sounds right.

Basically VMWare (and every other VM product I know of) creates a small number of files that hold your Virtual Machine's configurations and disks.  All you have to do is keep those files preserved, and then when you run VMware again just go to File | Open and find your backed up files.  Your VM should jump right back to life (after prompting you to change/keep the machine's ID and some other little things.

---

### Post by yssim on 2007-12-18
I tried that method above, but when I want to run the virtual machine, the server prompted me this error message:

"Cannot open the disk '/var/lib/vmware/Virtual Machines/Windows XP Home Edition/Windows XP Home Edition.vmdk' or one of the snapshot disks it depends on.
Reason: Insufficient permission to access file."

I didn't get any UID message before. What should I do?

---

