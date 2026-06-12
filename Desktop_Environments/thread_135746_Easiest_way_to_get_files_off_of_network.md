---
title: "Easiest way to get files off of network"
date: 2006-02-24
forum: Desktop Environments
---

### Post by linds on 2006-02-24
What is the easiest way for me to get some pictures off of my network (windows) and onto my laptop ubuntu 5.10?

---

### Post by wylfing on 2006-02-24
Install Samba. I think the package name you probably need is called smbclient, but it won't hurt to install the "samba" package as well. Just search for it in Synaptic, right click it, and select Mark for Installation, then click Apply.

Once that's all installed, you will be able to access your Windows network shares.

---

### Post by AgenT on 2006-02-24
There are many different ways, but the most used and the one that requires no command line after install is Samba.

Once you configure Samba you can share files between a windows computer and linux permanently. Search the forum and/or read the [MountWindowsSharesPermanently]("https://wiki.ubuntu.com/MountWindowsSharesPermanently") wiki page.

---

### Post by jchau on 2006-02-24
or you can install ssh on your ubuntu computer and upload the files with scp or sftp from the windows machine.  The ssh server may also come in handy for a lot of other things like accessing your computer securely remotely.  

But if you're looking for the easiest way, I'd suggest emailing them to yourself. No setup necessary & pictures are normally small enough to attach.

---

### Post by mustang on 2006-02-24
I suppose the *easiest* way would be to setup a ftp server on your windows box (tons of software such as g6 or whatever--search around download.com) and then use firefox on your ubuntu system to log into it.

So I'd disagree that Samba is the easiest method...

---

### Post by lamego on 2006-02-24
In my oppinion installing an FTP server on you windows box would be the easiest and best performing option. (Samba has some protocol overhead)
My suggestion for the windows ftp server goes to [URL="http://sourceforge.net/project/showfiles.php?group_id=21558&package_id=21737"]
FileZilla FTP Server[/URL].

To connect to your windows box you can use nautilus,
just go to the menu Places -> Connect to server
and choose FTP with login...

---

### Post by jchau on 2006-02-24
I tried Filezilla before.  While it is a good idea, I don't think it is ready to be used reliably yet.  (eg. sometimes when I transfer a lot of files, the server messes up badly. weird file names often make filezilla put files in the wrong directory, and at times, it refuses to let people connect even though the configs did not change since the time it allowed people to connect).  I'd wait for a few more versions to come out before I'd use it as my primary method of transferring files.  

(But then again, the last time I used filezilla was w/in a month after I installed Ubuntu last year, so a lot could have changed since then). 

On the other hand, I love the Filezilla client.

---

### Post by Treebeard on 2006-02-24
I've had some bad experiences with samba and window shares..
I found the easiest way is to install ssh (sudo apt-get install ssh) on the linux box and use "winSCP" on your windows box (use scp as protocol).

---

### Post by linds on 2006-02-27
Treebeard,  would you mind going into more detail about why you don't like Samba,

And what this winSCP is.   

I really need to be able to map network drives to my linux box from windows.  Is this possible with winSCP and ssh?

---

