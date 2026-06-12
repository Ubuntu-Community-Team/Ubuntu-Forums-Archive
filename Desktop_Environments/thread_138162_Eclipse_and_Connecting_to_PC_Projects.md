---
title: "Eclipse and Connecting to PC Projects"
date: 2006-03-01
forum: Desktop Environments
---

### Post by MindlessMuse on 2006-03-01
Greetings,

I am new to ubuntu and to linux, but successfully converted my laptop to dual boot into both xp and linux last night.

I have almost everything configured the way I need...least I think I need at this moment to work just on the linux side and not have to xp at all.

The one problem I am having is I use eclipse for my development environment, and have several projects that I connect to via XP on a windows server with no problems.  I can't seem to figure out how to get the Linux side to connect and see those projects.

Just curious if any other eClipse users out there were able to connect to existing projects that reside on XP servers?

Thanks in advance!

-Kevyn

---

### Post by MindlessMuse on 2006-03-08
Just wanted to bump this to see if anyone can shed any light on this subject.  I am able to connect just fine to the windows servers using bluefish, but am needing to be able to connect via eclipse so I can eliminate the xp on my laptop. ;-)

Thanks in advance!

-Kevyn

---

### Post by adamkane on 2006-03-08
Detail the steps you take to connect with Bluefish. You may need to mount the Windows share to connect with Eclipse. Apologies for not being very helpful.

---

### Post by MindlessMuse on 2006-03-08
Hi and thanks for the response!  One thing I am loving about this change, the community!!!

I have mounted the shares, which bluefish sees with no problems, as they are listed when I hit browse in the connections area wear the hda's show.  Eclipse does not see anything but my local hda's and no shares at all.  I think it has to be a bug or something with eclipse, since bluefish sees them with no problems.  I think I read that bluefish supports smb, which I am thinking eclipse might not?

Either way, thanks for trying to help me through this.

---

### Post by adamkane on 2006-03-08
Is your Windows share mounted under /media? You should be able to browse to /media/<sharename>/. Post the contents of your /etc/fstab file.

```

sudo gedit /etc/fstab

``` 
Ubuntu is insanely enjoyable to use, if you don't mind learning new things.

---

### Post by MindlessMuse on 2006-03-08
Yes, the local drives are listed under /media.

Now, that you bring that up, I am not sure if I am actually mounting the windows server share correctly.  I will have to check that at work tomorrow to see if I am doing it correctly.

The steps I had taken were using the connect to server, then browsing the work network, then creating a link by right clicking and create link.  Is there an actual mount command that I should use to make them appear as a mount and not just smb 'shortcut' link?

Thanks again for your help!

Yeah, ubuntu has been a lot of fun so far.  I am both a pc and mac user, owning both, but I never really explored the potential on my mac as far as really diving in and trying to understand everything that it is capable of.

---

### Post by adamkane on 2006-03-08
Manual mount:
[http://easylinux.info/wiki/Ubuntu#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read.2Fwrite]("http://easylinux.info/wiki/Ubuntu#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read.2Fwrite")

Mount at boot:
[http://easylinux.info/wiki/Ubuntu#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite]("http://easylinux.info/wiki/Ubuntu#How_to_mount_network_folders_on_boot-up.2C_and_allow_all_users_to_read.2Fwrite")

Note:
Save your Windows name and password in the .smbcredentials file.

---

### Post by MindlessMuse on 2006-03-08
Thanks!

I will try this in the morning and let you know how it went.

Thanks again!

---

### Post by MindlessMuse on 2006-03-09
Hmmm....I do those commands and it tells me it can't find the IP address of the windows server in /etc/fstab

Bascially to summarize again real quick....I am trying to mount a windows share from a windows server on my network, rather than just using smb connection so that eclipse can find it.

Thanks again.

---

### Post by kaamos on 2006-03-09
Can you post the line from your fstab (change the ip to x:s if you want to) ?

---

### Post by adamkane on 2006-03-09
I'll get out of the way, but I wanted to contribute this:

Mounting shares and compiling programs are always difficult the first 10 times. :) At the end of it, you'll have a small toolkit of commands that you will use over and over. After you get tired of the command line, you will find shortcuts and scripts to do what you want. My brother is a graphic artist/web programmer on his Mac. Since Mac went to Unix, he uses the command line as much as I do.

Replace 192.168.0.1 with the actual IP address of your Windows machine and replace /linux with the name of the folder you are sharing on the Windows machine.

This:

//192.168.0.1/linux    /media/sharename smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0 

should look like this:

//192.168.0.10/mywindowsfolder    /media/mylinuxfolder smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0 

If you don't know the IP address of the Windows machine or the Windows share name of the folder, then try this:

On the Windows machine, go to Start -> Run -> cmd ->
```

ipconfig

``` 

You should get some information like this:

Connection-specific DNS Suffix : 192.168.0.10
Subnet Mask : 255.255.255.0
Default Gateway : 192.168.0.1

Then go to the folder you are sharing on the Windows machine, and right-click on it to open the Sharing tab. The Sharing tab will tell you the Windows share name of the folder.

---

