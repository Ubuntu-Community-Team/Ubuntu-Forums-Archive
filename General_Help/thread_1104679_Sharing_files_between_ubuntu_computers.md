---
title: "Sharing files between ubuntu computers"
date: 2009-03-23
forum: General Help
---

### Post by orlox on 2009-03-23
Ive used ubuntu for quite some time now, but I had never been in a situation where I had two computers with linux connected to a network at home.

So i want to setup an easy way to share files between them over the network. Both of them are laptops and they get a non-static ip from a wireless router.

I read something about NFS, but all the examples used fixed adresses or domain names, so I wouldnt know how to do this that way...

Any suggestions?

---

### Post by bodhi.zazen on 2009-03-23
Shared services over wireless can be problematic depending on your router (my router allows clients but not servers, it is a security thing and really depends on your router).

On one computer, click on a directory you own, in /home -> from the pull down menu select sharing options. (DO NOT share your home directory).

From the next menus select either samba or nfs

log out and back in -> re-select the directory and set your share name and options.

I personally prefer samba. NFS is fine tool./

Go to your other box and browse to network shares.

---

### Post by Yashiro on 2009-03-23
If you want to pass files between machines occasionally:

Open Pidgin on both machines.
Create an account using the Bonjour protocol.
You SHOULD be able to chat and send files to each other over the lan without any compicated setup at all.

If that fails (it might if Pidgin is bugged) check the repositories for Giver and install that on both machines.

---

### Post by mb_webguy on 2009-03-23
Samba is probably the easiest way, and since it is an implementation of Windows' file sharing protocol, if you ever want to add a Windows machine to your network, it would also be able to access the files.

Just right-click on a folder in Nautilus, click Sharing Options, and set the options you want.  You may need to install Samba the first time you try to setup file sharing, in which case you'll have to go through this process a second time to actually enable the share.  You may have to restart Samba with the command "sudo /etc/init.d/samba restart" in the terminal before the changes take effect.

---

### Post by Yashiro on 2009-03-24
Samba really isn't the easiest way. Not by a long shot.
When it does work, it's fine. When it doesn't it takes way too much troubleshooting. Having to run a samba server just to share files between peers on a lan is not the way to do things.
Especially for people who are not well versed in the technicalities they will have to endure when it goes wrong.

If you just need to pass files around whenever you want I think trying the alternatives is worth it. Granted we often resort to Samba because it's 'what we know' but zeroconf file sharing as seen in giver or pidgin-bonjour is something that needs more use and support.
If you need a centralized file store of some sort though, then yes, Samba is the choice.

---

### Post by mocoloco on 2009-03-24
Samba didn't used to be the easiest way a few releases ago, but now it seems to be the preferred way. The app used before was shares-admin, and it's still there but no longer in the menus. Like bodhi.zazen and mb_webguy pointed out it's easy to set up samba, other than the quirk of having to select sharing twice if you initially need to install samba. I also found I had to share my son's home folder with a different name, so I did <user>-home.

Prior to doing that I would always just use ssh, but that only worked out because I have a user account on all the machines in the house, with sudo access of course :p

---

### Post by ahood on 2009-09-04
See [http://ubuntuforums.org/showpost.php?p=7896158&postcount=8](http://ubuntuforums.org/showpost.php?p=7896158&postcount=8)

Hope it helps.

---

### Post by blackhawkover on 2009-09-11
> **Yashiro said:**
>  Granted we often resort to Samba because it's 'what we know' but zeroconf file sharing as seen in giver or pidgin-bonjour is something that needs more use and support.
If you need a centralized file store of some sort though, then yes, Samba is the choice.


I agree that Giver needs more exploration. I am from a Windows background and at work we are using a main sharing area, which is great in windows, but what if I want to just send somebody one file. Wouldn't it be better to just send it with Giver? One file, boom. done. like a sophisticated way of emailing an attachment. 

I think we need to stop thinking like windows.

---

### Post by Whiffle on 2009-09-11
For me, the easiest way to occasionally transfer a file is to install ssh-server on both computers.  Then, when I want to connect, I do:

sftp://192.168.1.151 

where 192.168.1.151 is the ip address of the desired computer, in Nautilus.  Easy, it is.  Even easier if you get dns setup correctly, then you can do it by name:

sftp://blacktop

ta da!

---

### Post by fragos on 2009-09-11
You don't need to know the assigned IP on a local network, just the host names of the machines. For example my desktop is "Geo" and my laptop "dell". From the laptop I address the desktop as "Geo.local" and in the other direction "dell.local".

---

### Post by petermg on 2009-09-11
All I did was in Nautilus, right clicked on the folder I wanted to share, selected SHARING and it installed the service and I told if it if I wanted guest account or not, which I did enable for my windows boxes.  Then from my othe Ubuntu PC I went to PLACES, then NETWORK and found the PC there and the share and I was able to access it.  I just did this all for the first time yesterday and it was very smooth.

---

