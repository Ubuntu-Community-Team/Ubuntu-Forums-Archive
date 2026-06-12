---
title: "Should I downgrade to 8.04?"
date: 2009-03-28
forum: General Help
---

### Post by fmw on 2009-03-28
8.1 is fairly useless for me since after connecting to the network and showing icons for all the nodes, I can't access any of them.  Nobody here apparently knows how to deal with it.  Before I start, would you think killing this version and installing the older version might resolve the problem?

---

### Post by jmszr on 2009-03-28
fmw,

       Have you tried the Ubuntu Forums Networking & Wireless Subforum? Worth a try:[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336) . Ubuntu 8.10 has improved wireless but one never knows, 8.04 might work for you. Jaunty (9.04) Beta is out also. Hopefully someone with more knowledge than I have can help you.

---

### Post by Neo_The_User on 2009-03-28
I can help. XD

whats the problem?

---

### Post by fmw on 2009-03-28
During the 8.1 installation, the network set itself up automatically.  When I go to the network, I see icons for every node and the Windows workgroup that encompasses it all.  However, none of the nodes is accessible and I need to use the NAS, which also shows up among the other icons.  When trying to access a node, the system returns an error saying that it can't mount the location and can't find a share list.  I should mention that the Ubuntu workstation doesn't show up on the other nodes of the workgroup, but I haven't gone that far yet.  The book I bought is of no help at all.  Thanks for any help.

---

### Post by Neo_The_User on 2009-03-28
You need NAS? What is NAS?

---

### Post by fmw on 2009-03-29
Network attached storage.

---

### Post by la3875 on 2009-03-29
Did you set up your machine with the same work group name?

---

### Post by fmw on 2009-03-29
Good question.  I did if the installation asked me to.  Honestly I don't remember.  Is there a way to check?  The computer does recognize the Windows workgroup and shows icons for all the nodes within it.

---

### Post by coffeecat on 2009-03-29
> **fmw said:**
> I should mention that the Ubuntu workstation doesn't show up on the other nodes of the workgroup, but I haven't gone that far yet.

That may be because you still need to install some bits of samba that don't come with a default installation and also create a share. (I'm assuming you're using Windows smb/cifs shares.) Go to your home folder and create a folder. Call it what you will. Right-click on it and select 'Sharing Options'. (It might be called something else - I'm in Jaunty atm - but it'll be about shares.) Click on "Share this folder" and a window will pop up saying 'Sharing service not installed'. Click on the 'Install service' button and whatever needs to be installed will be. You'll then be prompted to restart your session.

Some of the details may be different in Intrepid, but from memory that's more or less the Intrepid procedure. I've just done this in Jaunty to remind myself.

With any luck this may solve the other problem as well, where you can't browse shares on your NAS device.

---

### Post by fmw on 2009-03-29
That got the Ubuntu workstation visible from the Windows workstations. This computer is now part of the workgroup as far as the other workstations are concerned. It did require the package download as you suggested.  It didn't allow me access from the Ubuntu machine to the others, however.  The problem persists.

The network is operating as it should.  The problem has to be on this workstation.

---

### Post by coffeecat on 2009-03-29
> **fmw said:**
> The problem has to be on this workstation.

Maybe not.

First, I made sure I'd got the samba bits installed that I mentioned in my previous post in machines 1 and 2. Then I set up a share called "Fred" in Machine 1 running Jaunty Beta and put a couple of files in it. Then from machine 2 running Intrepid I was able to log into share "Fred" (using Nautilus > Network), access the two files and write a file to the share. So I can confirm that at least smb networking is working in Intrepid. Which leads to your particular problem...

Could it be a firewall issue? Intractable networking problems often turn out to be so. When you say 'nodes' are you referring to Windows machines, network servers, or what? If Windows machines, check you firewall settings on each. They may be blocking the local network IP address of your Intrepid machine.

---

### Post by fmw on 2009-03-29
No, not a firewall issue.  The NAS, as an example,  is not a full computer.  It is little RAID that sits on the network for storage and backup.  It has no firewall.  It has no operating system.  It is not a windows computer,. It is just a storage device that communicates with the network automatically.  All the other windows machines have firewalls but I don't get far enough to run afoul of it.  Ubuntu complains that the they are not "mounted" and that it can't find a share list.  The windows machines all have their drives shared with the network.  The NAS, of course, doesn't have or need any of that.

---

### Post by la3875 on 2009-04-07
Don't discount or disregard the firewall issue. If you are behind a hardware router you may need to adjust some settings in the router for all machines on your network to be seen. Ubuntu machines as far as I know don't install firewall software by default.

---

