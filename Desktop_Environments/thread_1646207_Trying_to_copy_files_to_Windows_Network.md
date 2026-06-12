---
title: "Trying to copy files to Windows Network"
date: 2010-12-15
forum: Desktop Environments
---

### Post by iv76erson03 on 2010-12-15
Hi all,
  I have have ubuntu 10.10 at work hooked onto a Windows Server 2003. I have pretty much everything working peachy except I can't copy files onto the network drive.
  When I start my computer, i have to manually go to network places and navigate around until i find my company share drive and then its mounted for the rest of the day. I can read files from the share drive and oddly enough save documents through programs like gimp and open office, however if i go through nautilus to try and copy a file from my desktop to the company share, it won't let me. It just says "Error while copying 'yourfile'" and the details just say "invalid argument." 

any ideas? thanks

---

### Post by pfnorris on 2010-12-18
In making this reply I am assuming that you have a valid account on the Windows Server 2003 machine.

I have a similar set up at work I am using 10.04 on my desktop, and all of the network resources are shared from Windows servers in two different Windows domains. I have found that it is much more efficient to mount the shares that I need at boot time by putting them in my /etc/fstab file. I can put an option into each entry to ensure that it is mounted as read/write. I keep seperate credentials for each domain in credentials files located in my home directory, and then reference these in the options passed in fstab.

I find that this method works very well for me. The network shares are transparrently available to me all of the time. Let me know if you want me to be more specific as to how I have done this

---

### Post by iv76erson03 on 2011-01-12
I need further explanation. I did some google searches for mounting in /etc/fstab but nothing seemed to work for me. thanks for any help.

---

### Post by pfnorris on 2011-01-13
OK I'll try and give you some pointers to get to the bottom of the issue. 

In order to be able to write to the network share you will need to connect to it using an account with write permissions on the server. That may not be as simple as an account with the same name on the Linux client. E.G. I have a given netid on my corporate network. I have created a user with the same name on my Linux machine. But I have to logon to the Windows share by specifying the domain netid. I do this by creating a file called creds in my home directory (if you wish this file to be hidden you can precede it with a dot thus .creds) the content of this file is:

username=netid
password=password
domain=domainName

Substitute proper values for those I have shown here. 

Then you want to mount the share at boot time. Mounting a network drive is roughly equivalent to mapping a drive on Windows. You can do this in two ways either manually by running a command at the command line, or automatically at boot time by putting an entry in /etc/fstab. If you will need access to the share on a regular basis it is usually best to mount it automatically so that it is always available. A pre-requisite for this is that you will need to create a directory, preferably in your home directory on which to mount it. I my case the share I am mounting is called labdoc, and is hosted on a server called labfap. So, I created a directory called labdoc in my home directory, and then put the following entry in my /etc/fstab file 

//labfap/labdoc /home/netid/labdoc cifs credentials=/home/netid/creds,uid=netid,gid=yourgroupname 0 0

In each case replace the netid and yourgroupname with valid values. The first field identifies the share to be mounted, the second field identifies the local directory on which it should be mounted. The third field identifies the file system used on the server, (cifs) is the modern implementation of Windows SMB network file system. The next field is the mount options separated by a comma. The uid and gid are included to give you read/write access to the share. Normally because entries in fstab are mounted by the root account only that account will have read/write access. Everyone else will have read only. These options allow the share to be mounted using your credentials thus giving you full access. The last two fields identify if dump should backup this file system 0 = no, and if fsck should check the file system 0 = no.

This solution works for me. I believe your issue is related to permissions because you are able to reach the share, and read from it. The puzzling thing is that you say that some of your applications can write back to it, but nautilus cannot. However, I still think that this points to a permissions issue. 

If you are still having a problem I can recommend taking a look at [this article]("https://help.ubuntu.com/community/MountWindowsSharesPermanently").

---

