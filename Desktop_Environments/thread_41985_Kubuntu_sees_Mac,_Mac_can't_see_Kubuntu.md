---
title: "Kubuntu sees Mac, Mac can't see Kubuntu"
date: 2005-06-15
forum: Desktop Environments
---

### Post by Uta on 2005-06-15
I am having a hard time sharing a folder from my Kubuntu laptop with my iBook laptop (Mac OS 10.3.9).
From my Kubuntu laptop I see my iBook shared folder without issue via Samba Share but when I try to see the folder I am sharing on my Kubuntu desktop nothing shows up in the iBook's Network Browser? I even tried to connect, from the Mac, via the Kubuntu's local IP. smb://xxx.xxx.x.xxx and [http://xxx.xxx.x.xxx](http://xxx.xxx.x.xxx), this didn't work.
I guess it's a permissions issue but I can't understand exactly what permissions have to be opened up that I haven't already done. The folder on the desktop is shared. Any suggestions? Thanks!

---

### Post by Digitallysick on 2005-06-15
i see in another form question"Macs can easliy work with Samba, and all you have to do to install samba on ubuntu is run

sudo apt-get install samba

and then follow your totrials on how to get it to work with mac OSX (though kubuntu comes witha a nice configurator for samba - not too sure if it's there in ubuntu, but read [http://www.ubuntuguide.org](http://www.ubuntuguide.org) and it should come up with details on how to samba working properly" 

But i could never get samba to work with mac, ?? so good luck

---

### Post by Uta on 2005-06-16
No forward progress with getting my Mac to see my Linux laptop. If anyone has successfully done this, I'd love to see  their config file for SAMBA. It's so strange that the laptop running Kubuntu can see and copy files to my Macs on my LAN but will not let the Macs see or access Kubuntu. I have done all the regular steps, created a shared folder, opened up access to that folder, created a user/password for my Mac and still none of my Macs can see my Kubuntu laptop in their network browser nor by smb:// the Linux Local IP? Has anyone done this?

---

### Post by ltmon on 2005-06-16
[QUOTE=Uta]No forward progress with getting my Mac to see my Linux laptop. If anyone has successfully done this, I'd love to see  their config file for SAMBA. It's so strange that the laptop running Kubuntu can see and copy files to my Macs on my LAN but will not let the Macs see or access Kubuntu. I have done all the regular steps, created a shared folder, opened up access to that folder, created a user/password for my Mac and still none of my Macs can see my Kubuntu laptop in their network browser nor by smb:// the Linux Local IP? Has anyone done this?[/QUOTE]

My girlfriend has ordered a Mac Mini, and we're picking it up tommorrow :) ... hopefully I'll have some success and be able to post back with a solution.

L.

---

