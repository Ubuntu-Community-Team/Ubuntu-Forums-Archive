---
title: "get file from VMware to Kubuntu?"
date: 2006-06-24
forum: Desktop Environments
---

### Post by xoros on 2006-06-24
How do I get a file out of VMWare and into Kubuntu? 

I see this from another post: 

"to share files from vmware windows with linux you only have to set up shared folders on windows. Then from nautilus go to archive -> connect with server."

Where is "archive -> connect with server" in Kubuntu or its equivalent?

Thanks

---

### Post by Sye d'Burns on 2006-06-24
Assuming you have vmware tools installed, all you should have to do is (from the virtual machine settings) click **'Options.'** Look for **'Shared Folders'** on the left and click it. Click **'Add...'** Give it a name and under 'host folder' Find the folder you'd like to add, for instance: /home/sye/vmshare/

Be sure to click **'enable this share'** and you're done on the ubuntu side.
...then you just add it to your windows network in windows, it should pick it up.

---

### Post by xoros on 2006-06-24
[QUOTE=Sye d'Burns]Assuming you have vmware tools installed, all you should have to do is (from the virtual machine settings) click **'Options.'** Look for **'Shared Folders'** [/QUOTE]

There is no option for Shared Folders.  I have vmware tools installed.  Maybe I need to restart it or something?  That option is nowhere to be found.

---

### Post by Sye d'Burns on 2006-06-24
In the machine summary view, click **edit virtial machine settings** then **'options'**. It should be the third option down on the left.

---

### Post by incubus on 2006-06-24
Out of curiosity I started vmware here and I don't have shared folders either, but I remember having that in the old days of windows. 

What I would do is transfer the files through SSH.
(make sure you have the ssh daemon running in your host)

If you don't feel comfortable with command line, you could get this thing here (or something similar):
[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)

I'll give it a try myself.

incubus

---

### Post by Sye d'Burns on 2006-06-24
hmmm, I suppose it's worth noting that I am using vmware workstation. Are you two using something different? player? server?

---

### Post by xoros on 2006-06-24
[QUOTE=Sye d'Burns]In the machine summary view, click **edit virtial machine settings** then **'options'**. It should be the third option down on the left.[/QUOTE]

Nope. 
All that is there is this: 

General
Power
Snapshot 
Permissions
Startup/Shutdown
Advanced

Permissions is set to private, but when I changed that it didn't seem to make any difference. 

Where is that option? :(

---

### Post by incubus on 2006-06-24
xoros,

Try to install that program in your windows guest. I just did it here, it does the job. 

If you don't have sshd in your kubuntu, run:
$ sudo apt-get install openssh-server

incubus

PS: yeah, this is vmware server.

---

### Post by Sye d'Burns on 2006-06-24
Hmmm, I don't have any experience with vmware server incubus. I guess I should've asked for clarification earlier. I'm glad you found a workable solution though!

---

### Post by incubus on 2006-06-24
Sye, that was a very good point. I used to use vmware workstation in windows. Is the linux version "free" as well (like vmware server)?

Yeah, this solution is mostly for people who prefer a GUI to transfer files. I prefer to use good old scp.

For other people, by the way, if you don't like winscp's interface, there's a free version of SSH Secure Shell's client.

[http://www.ssh.com/support/downloads/](http://www.ssh.com/support/downloads/)

incubus

---

### Post by xoros on 2006-06-24
[QUOTE=incubus]Sye, that was a very good point. I used to use vmware workstation in windows. Is the linux version "free" as well (like vmware server)?
incubus[/QUOTE]

Thank you for all the information.  I am also curious if workstation is free too?

Thanks!

---

### Post by Sye d'Burns on 2006-06-24
No, it's not I'm afraid. Still an excellent program though.

---

### Post by xoros on 2006-06-24
After more digging around would this also possibly work; using Samba?

> In general configuration of the files shared with windows select the name you want for you computer but for the workgroup put MSHOME, and select not to use a wins server.
then you have to add an user to samba, with the command:
sudo smbpasswd -a user_name
After that in windows go to net folders and there you will see on the microsoft windows net the workgroup of the folders you have shared.

---

### Post by scxtt on 2006-06-24
i've got samba working from an Ubuntu host to either an VM XP samba share or an SSH connection to a VM Xubuntu [haven't tried samba b/t 2 *buntu boxes since SSH is a breeze) ...

---

### Post by xoros on 2006-06-24
> On a Linux host computer, VMware Server can automatically install and configure a Samba server to act as a file server for Microsoft Windows guest operating systems. You can then use Windows Explorer in the virtual machine to move and copy files between virtual machine and host — or between virtual machines on the same network — just as you would with files on physical computers that share a network connection. The lightly modified Samba server installed by VMware Server runs over the VMware Server virtual Ethernet, and the Samba traffic between different operating systems is isolated from actual local area networks. The source code differences for the changes (in diff format and based on Samba 2.0.6 are available from VMware. For more information, see [www.vmware.com/download/open_sources.html](www.vmware.com/download/open_sources.html).
If you already have Samba configured on your Linux host, the recommended approach is to modify that configuration so it includes the IP subnet used by the VMware Server virtual Ethernet adapter, VMnet1.

From the vmware server manual doc,  it sounds like it should have been easy.  I didn't see anything about it installing its own samba server during the install..  maybe it was some option I missed during the install of vmware?
Or maybe its just not implemented in the free beta version?

---

### Post by scxtt on 2006-06-24
it's not an "option", doesn't have anything to do w/ VMware itself ... XP does samba on it's own, for "free", and you can download samba for linux. for free ... all you have to do is enable it for both the host and the VM ...

but if you're using 2 *nix OSes, just use SSH ...

i use a bridged connection for my VMs and assign them static IPs as if they were boxes plugged into my router, host is 192.168.1.100 and VM is 192.168.1.101 ...

---

### Post by ifokkema on 2006-06-24
I always use samba to share files. It's really quick (if you know how :)) and you've got your home folder shared in just a minute or two.

---

### Post by xoros on 2006-06-24
If vmware has nothing to do with it how do you explain this? 

> VMware Server can **automatically install and configure** a Samba server to act as a file server for Microsoft Windows guest operating systems.

How do I get vmware to do that??

---

### Post by scxtt on 2006-06-24
i didn't do what you quoted - i haven't even installed VMware tools (no need) - and samba works fine w/ my Ubuntu host and XP VM ...

i'm sure it has that feature, but it's not necessary ...

Kubuntu is your host?  what OS is the VM?

---

### Post by xoros on 2006-06-24
> Sharing Files by Connecting to a Windows System from a Linux System

To share files on a Windows system with a Linux system (by connecting to a Windows host from a Linux guest or connecting to a Windows guest from a Linux host or guest), you can mark a folder as shared on the Windows system, then use the smbmount utility in the Linux system to mount the shared folder. For example, if you want to share the folder C:\docs on a Windows 2000 system called win2k with a Linux system at /mnt/docs, follow the steps below. You may want to set up a shell script to run these commands.

1. Set up the folder or folders to share on the Windows system.

2. Create a user account on the Windows system for the Linux system user name that you are using to connect to the Windows system.

Otherwise, if you know the user name and password for a user account that can access the Windows system, you can specify that account on the command line.

3. From your Linux system, log on as root.
su -

4. Add the Windows system's host name and IP address to the hosts file, if the system cannot be found by name.

5. Mount the Windows share on your Linux system. Enter the following command all on one line.

mount -t smbfs -o username=<Windows system user account>,password=<password> //win2k/docs /mnt/docs

(Substitute the appropriate host name, share and mount point for your systems.)

Note: If you do not want to expose this password on the command line or in a script, leave out that option and provide the password when prompted after you run the command.

Now you are connected to the shared folder on the Windows system from your Linux system and can begin to share files between the two. 

Not sure if that works yet but sounds like it might.  Found it here: [http://www.vmware.com/support/gsx3/doc/running_fileshare_lin2win_gsx.html](http://www.vmware.com/support/gsx3/doc/running_fileshare_lin2win_gsx.html)

---

