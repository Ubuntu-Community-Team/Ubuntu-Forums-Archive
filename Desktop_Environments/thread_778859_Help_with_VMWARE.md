---
title: "Help with VMWARE"
date: 2008-05-02
forum: Desktop Environments
---

### Post by The_Big_D_GFK on 2008-05-02
Hi all,

I am seeking help with installing Windows XP Professional on a virtual machine in Kubuntu Hardy Heron. I have no problem creating the virtual machine. When I go to power it on, Windows XP Professional setup begins from my CD drive, as I would expect. However, once all the drivers and other files are loaded and the installation want to begin, the system informs me that it could  not find any hard drives on my computer, and that setup cannot continue. Has anyone else experienced this problem, and how did you solve it? Thanks in advance for your assistance.

This being my very first post to ubuntuforums, I apologize if I have posted this question in the wrong forum.

Regards to all


Jesus paid a debt he did not owe because I had a debt I could not pay,

---

### Post by Kokopelli on 2008-05-02
Welcome!  (This should probably be in the Virtualization forum but it is fine.  Hopefully a moderator will see it and move it.)

By any chance is the virtual hard drive for your XP install SCSI?  For XP you are best off using vurtual IDE drives.  In VMWare server open (but do not start) your vm.  On the right you should see:
```
 Hard Disk (IDE 0:0)
```

or 
```
 Hard Disk (SCSI 0:0)
```

I am not sure if you are working in VMWare server, workstation, or player but the principle should be the same.  If you do not see an IDE hard drive then edit the virtual machine setings and add one.

If you **do** have an IDE drive already then post your <vmname>.vmx file please. It will be in the directory where the virtual machine sits.

---

### Post by The_Big_D_GFK on 2008-05-02
> **Kokopelli said:**
> Welcome!  (This should probably be in the Virtualization forum but it is fine.  Hopefully a moderator will see it and move it.)

By any chance is the virtual hard drive for your XP install SCSI?  For XP you are best off using vurtual IDE drives.  In VMWare server open (but do not start) your vm.  On the right you should see:
```
 Hard Disk (IDE 0:0)
```

or 
```
 Hard Disk (SCSI 0:0)
```

I am not sure if you are working in VMWare server, workstation, or player but the principle should be the same.  If you do not see an IDE hard drive then edit the virtual machine setings and add one.

If you **do** have an IDE drive already then post your <vmname>.vmx file please. It will be in the directory where the virtual machine sits.
Hi Kokopelli,

Thank you for your quick response to my question. I have wondered if this was an issue of IDE as opposed to SCSI. However, I have tried it both ways, and the problem is the same. The creation of the virutal machine defaults to an IDE drive and, as you suggest, when I check the disk type, it does show up as IDE (0,0). I'll post you my .vmx file as soon as I can. In the mean time, can you tell me what I might look for in the .vmx file? Thanks again for your help.

---

### Post by The_Big_D_GFK on 2008-05-02
> **The_Big_D_GFK said:**
> Hi Kokopelli,

Thank you for your quick response to my question. I have wondered if this was an issue of IDE as opposed to SCSI. However, I have tried it both ways, and the problem is the same. The creation of the virutal machine defaults to an IDE drive and, as you suggest, when I check the disk type, it does show up as IDE (0,0). I'll post you my .vmx file as soon as I can. In the mean time, can you tell me what I might look for in the .vmx file? Thanks again for your help.
Hi again Kokopelli,

Forgot to mention that I am using VMware server.



Regards

---

### Post by Kokopelli on 2008-05-02
Assuming your host is linux the vmx file should be in either

~/vmware/<image name>

or 

/var/lib/vmware/Virtual Machines/<image name>

Just a note I am heading out so won't be responding till tomorrow at earliest. If you are using an IDE drive as the only hardrive though I am not sure what is going on.  There are a bunch of bright people here though so hopefully we will figure it out.

---

### Post by XemeX on 2008-05-02
Try [http://easyvmx.com](http://easyvmx.com) :)

---

### Post by The_Big_D_GFK on 2008-05-02
Hi Kokopelli,

Once again, much appreciation for your response to my post. Actually, what I meant about the .vmx file is, not where do I find it (its in /var/lib/vmware/Virtual Machines), but can I open it, and what do I look for in it? I do have only a single IDE hard disk; but it has two partions on it. I've been dual booting Windows XP and Kubuntu. Could this be part of my problem?




Regards and thanks

---

### Post by The_Big_D_GFK on 2008-05-02
Hi XemeX,

Thank you for responding to my post. I neglected to say that I'm using VMware server. Your link has to do with creating virtual machines in VMware Player. However, I'll check it out to see if it offers me any guidance. 




Reagrds and thanks

---

### Post by XemeX on 2008-05-02
> **The_Big_D_GFK said:**
> can I open it, and what do I look for in it? I do have only a single IDE hard disk; but it has two partions on it. I've been dual booting Windows XP and Kubuntu. Could this be part of my problem?




Regards and thanks

You can open it with any text editor you like.
Look for something like this:
```
ide0:0.present = "TRUE"
ide0:0.deviceType = "disk"
ide0:0.filename = "Windows XP Professional.vmdk"
```

(this is my config)

For Vista with SCSI it would be:

```
scsi0:0.present = "TRUE"
scsi0:0.fileName = "Windows Vista.vmdk"
ide1:0.present = "TRUE"
```

That's all...

Anyway, machines created by easyvmx can be used with VMWare server although I strongly recommend using Player on Ubuntu since it is less complicated and can be installed  easily.

EDIT

Of course remember that you need to have the files *.vmdk created in advance.

---

