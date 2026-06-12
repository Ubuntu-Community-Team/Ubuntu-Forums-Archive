---
title: "Sharing an external hard drive help."
date: 2009-04-08
forum: General Help
---

### Post by lawentzel on 2009-04-08
Running Ubuntu 8.04.  I've plugged in the hard drive, and it shows up fine.  In terminal, I launch Nautilus as root.
```
sudo nautilus
```
This bring up Nautilus.  I go to root, and then Media.  There I can see my external hard drive.  I right clicked it and choose "Sharing Options".  I set up the drive to share.  I enabled everything.  "Share this folder", "Allow others to write in this folder" and "Guest access".

The drive does show up on my Windows side, but when I try to access it, it indicates that I do not have permission to access the drive.  Suggestions?

---

### Post by lawentzel on 2009-04-09
bump

---

### Post by Nano_ext3 on 2009-04-09
If you are trying to access it from you windows side it could be that the username and/or permissions from Linux do not exist and cannot be referenced on windows.  Why arn't you just plugging in via usb on windows?  There should be zero issues there.  USB is USB, and should be accessible on either system by clicking on Places > USB_DRIVE in Ubuntu, or in My Computer in windows.  Make sure to also "safely remove" in windows and "unmount" after using the drive or the drives $LOG file will get messed up and you will have to force mount it.  Best to boot into windows and do a safe remove.  Not sure why you want to share an external when its this easy.

Cheers,

_Nano

---

### Post by Nano_ext3 on 2009-04-09
If you are trying to establish a "shared folder" you may want to look into using Samba folder/file sharing.  I do not know why you are not just plugging in the drive and accessing it, if you want it as a "permanent" mount, in linux this can be accomplished with /etc/fstab or in windows it just shows up in My Computer.  I think you might be making a mountain out of a mole hill so to speak.

Cheers,

_Nano

---

### Post by Th3Professor on 2009-04-09
I'm attempting to share an external drive as well, yet within a different context.

How do I share an external (USB) hard drive via SSH?

---

### Post by lawentzel on 2009-04-09
My Ubuntu system I use for development of web pages and stuff like that.  For the most part it is sitting there not being used.  I figured I could share the external hard drive on my network to give it additional functionality.  The external drive is 1 terabyte.  The internal hard drive I am using on my Ubuntu system is under 1 gig.  So... this is why I want to share the drive with everyone on my network.  Hope that helps.  Will look at whats been suggested and see if or how that helps.  Thanks.

---

### Post by Th3Professor on 2009-04-11
> **lawentzel said:**
> My Ubuntu system I use for development of web pages and stuff like that.  For the most part it is sitting there not being used.  I figured I could share the external hard drive on my network to give it additional functionality.  The external drive is 1 terabyte.  The internal hard drive I am using on my Ubuntu system is under 1 gig.  So... this is why I want to share the drive with everyone on my network.  Hope that helps.  Will look at whats been suggested and see if or how that helps.  Thanks.

I have a 1TB ext.drive too, would like to share over a server/ssh connection. How do I do that?

---

### Post by Th3Professor on 2009-04-17
> **Th3Professor said:**
> I have a 1TB ext.drive too, would like to share over a server/ssh connection. How do I do that?

bump
<thank you for any help on this>

---

### Post by weiersc on 2010-11-15
I have the same problem. Two Ubuntu machines connected to the same router. Would like both machines to be able to access the external usb hdd without having to move it between machines. 

I'm trying to access it via SSH, but get the message You do not have the permissions necessary to view the contents of "USB-HDD".

I have set myself up as a user with full administrative priveledges on the host machine.

Not quite sure what I'm doing wrong.

---

### Post by tredegar on 2010-11-15
> **Th3Professor said:**
> I have a 1TB ext.drive too, would like to share over a server/ssh connection. How do I do that?

This is easy on an unfirewalled LAN, more awkward on a network with firewalls (you'll need to open and forward some ports).

On the machine with the drive attached, install **openssh-server**
On the remote machine, enter **sftp://username@server** or **sftp://username@IP.OF.SER.VER** into the nautilus address bar and press return.

You will be asked if you consider it safe to connect. You will be asked for the password of the username on the server.

You will then see the root directory of the remote server in your nautilus window. Navigate to the drive you want to share. Bookmark it for future use. Drag files to and from the remote drive. That's it.

More fun is to be had if you now you set up public key based **ssh** authentication, because then you will not be asked for a password, but your secure login will be automatically authenticated and all traffic will still be encrypted by **ssh**.

Click and be connected.

Have fun.

---

### Post by axept on 2010-11-15
> **weiersc said:**
> I have the same problem. Two Ubuntu machines connected to the same router. Would like both machines to be able to access the external usb hdd without having to move it between machines. 

I'm trying to access it via SSH, but get the message You do not have the permissions necessary to view the contents of "USB-HDD".

I have set myself up as a user with full administrative priveledges on the host machine.

Not quite sure what I'm doing wrong.

Hm, I have a 1 TB external USB HDD that I share between 2 Ubuntu 10.10 machines. I just right clicked on the folder(s) on the external disk on the computer its in, and and clicked on share options, or what its called on english. (I have a norwegian Ubuntu rls) Then I had to install some plugins or something, set up a username and password and voila! Works! The computer its connected with is wired to the router and the computer get the same IP address everytime. Anyway, my point is, I've got no problem accessing my shared folders on my external USB drive from other computers on my network. And that is 1 Ubuntu (as written) and 1 Win7.

---

