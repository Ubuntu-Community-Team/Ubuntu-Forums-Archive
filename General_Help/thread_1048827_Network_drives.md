---
title: "Network drives"
date: 2009-01-23
forum: General Help
---

### Post by CentiZen on 2009-01-23
Hello everybody, my name is CentiZen and my predicament is such;

I have two laptops. One is running windows vista (which I hate, but I don't have any choice), the other, is broken, and cannot use a built in hard drive or the DVD part of the CD burner. 

I have my second laptop running Ubuntu 8.10 off of a 2 gigabyte flash drive. I also have a 250gb Seagate External HD plugged in via USB.

This computer will be primarily used as a download station. I have to take my other laptop to school every day, which makes it difficult to download large torrents, so I figured that I would rig my other laptop up like this.

Is there anyway that I could map my External hard drive like a virtual drive for my Windows machine? That way I wouldn't have to unplug the device and scramble any other torrents that are still downloading when I want to put it on my windows machine.

Any help is appreciated.

Thanks, 

      CentiZen

---

### Post by HereInOz on 2009-01-23
The first thing you will need to do is to install Samba on your Ubuntu machine.  I personally do not like the "Nautilus share" which is the default in 8.10.  Just search for samba in Synaptic and install:

samba
system-config-samba

The rest of the needed libs and things should be installed along with these two (hope I am right).

Once samba is installed, you then need to share the folder(s) on your Ubuntu system for access by Windows - this is where you use system-config-samba which will install a menu item in the System > Administration menu.  Make sure that you create the share as writable.

After you have shared the folders, you need to create a Samba user.  Open a terminal, type:

sudo smbpasswd -a the_username_on_the_windows_system

You will be asked for your Ubuntu password, and then you will be asked to create the SMB password (use the same one as on the Windows system), and this will create the user and the password.  Make sure that your username and SMB password is the same between the two systems.  You may have to create the same password on the Windows system if you don't have a password on it.

Once you have installed it all, shared the folder(s) and created the username and password, you will need to open the SMB ports (135 - 139) in the firewall.  Install firestarter to manage this.

---

### Post by CentiZen on 2009-01-24
thank you so much, worked like a charm

---

