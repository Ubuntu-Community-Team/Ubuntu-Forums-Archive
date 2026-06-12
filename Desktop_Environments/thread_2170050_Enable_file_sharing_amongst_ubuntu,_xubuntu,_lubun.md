---
title: "Enable file sharing amongst ubuntu, xubuntu, lubuntu ?"
date: 2013-08-24
forum: Desktop Environments
---

### Post by vikram_kapoor on 2013-08-24
Hello, I will try to explain the scenario in a least complicated manner;

I have 20 computers in here,

14 &#8211; Xubuntu (pc1, pc 2, pc 3, pc 4, pc 5, pc 6, pc 7, pc 8, pc 9, pc 10 pc,11, pc 12, pc13, pc14)
5 &#8211; Lubuntu (pc15, pc16, pc17, pc18, pc19)
1 &#8211; Ubuntu (pc20)

All connected to the LAN (Local Area Network)

Now, is it possible to enable pure file sharing among all of these ?

**EVERY** computer will have a folder named &#8216;**shared**&#8217;  on their desktop which should be able to get **written and read by anyone on the LAN**.

There should be **NO** username and password or any kind of authentication while copying/pasting or accessing the **Shared** folder (I don&#8217;t care about the security)

Please can someone help me in a way to set this thing up ?

And please consider that I can&#8217;t afford any fancy surprises because the end users (operators) are used to winXP file sharing.

Until now I&#8217;ve tried using Samba and sometimes it works sometimes it says permission denied, connection refused, volume not mounted. I&#8217;ve installed thunar file manager on every computer.

Sometimes while copying just a 2 MB file it takes ages, it keeps on saying copying&#8230;.till my wit ends. And then I end up using a flash drive ](*,)

---

### Post by keith-k on 2013-08-25
Probably easiest way is to get yourself a cheap NAS. Is this a business, school or home? What router is on your LAN? Many home routers allow you to connect a USB drive. If you could skip the folder on the desktop thing it would be very easy to connect to server in nautilus via SSH or FTP. (I guess you could make a shortcut on desktop - soft link.) FTP and SSH server very easy to set up. I'd recommend proftp and install the gadmin-proftp tools. You could get it up and running in just a few minutes. The caveat is that what ever computer is hosting it will get bogged down if too many connections, also file transfer will suffer with too many connections with one drive. Also need drive(s) made to be on 24/7 with most cache or SSD. I never can get Samba to work right either but ftp or ssh connection have been pretty much flawless as long as your host has static ip. (The fastest transfers are said to be with NFS between linux computers but I've never been able to set my server up correctly to use it.I guess it's about time to try again.) I just bought a new  Alienware Area 51 pre-installed with Ubuntu and struggled for awhile transferring files between computers, tried ssh first which was very simple but the old computer was slow to encrypt data, didn't have my external drives at home at the time which would have been fastest, then used proftp and in like a  minute was transferring files. It will take you longer to set up a specific folder to share with no logon credentials.

Maybe something you could use besides thunar. But with FTP you could even use your web browser.

---

### Post by SeijiSensei on 2013-08-25
With that many computers, you really need to consider building a central server, presumably using one of the existing machines.  For an all-Linux system, you should be using [NFS]("https://help.ubuntu.com/community/SettingUpNFSHowTo").  Designate one machine as a server (it can also function as a workstation if necessary, though it's not recommended), attach sufficient storage either by installing a hard drive or attaching an external USB device, then create a folder where the shared files will reside.  Make the folder world-writable (sudo chmod uga+rwx /path/to/the/folder).  Next install **nfs-kernel-server** from the repositories and follow the instructions in the linked article above to create the /etc/exports file.  

On all the machines you will need to install the **nfs-common** package so they can communicate with the server.  You can add an entry into /etc/fstab on the client machines to mount the shared folder automatically at boot.

Files created in the shared folder will have the ownership and permissions of the person who created them.  That means that, by default, only the file's owner can edit the file. If you want to allow people to alter other peoples' files, [read this](http://deeson-online.co.uk/labs/setting-linux-server-group-write).

---

