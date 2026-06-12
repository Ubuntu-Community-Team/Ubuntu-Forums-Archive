---
title: "mount a Windows ME share"
date: 2009-03-20
forum: General Help
---

### Post by naresh123 on 2009-03-20
Hello,
I'm using Ubuntu 8.10 and am attempting to mount a share present on a Windows ME computer using Nautilus.

I can browse the network, see my Windows ME machine, can drill further and see the several shares that I have on it. When I try to mount any of the shares, I of course, get prompted for a user name, domain and password.

I only have a password set up on my Windows ME machine (right click on directory -> Sharing -> Access Type = Full with a Full access pwd specified).

I do not have a login for the Windows ME machine set up. There is no domain that I am aware of since there is no network to speak of really. Just my router and the Windows ME plugged into it via Ethernet cable, and Ubuntu on my laptop. I do have a Workgroup on the Windows ME (I can see it via Control Panel -> Network -> Identification tab).

So I don't know what user name or domain name to put into Nautilus' prompt. I keep getting the following generic error dialog box:
"Unable to mount location Failed to mount Windows Share".

I know that I can mount Windows shares from my Ubuntu setup, because I've tried this at work, and there I do have a username, domain and password to fill in, so maybe things are more normal and therefore they work.

I can mount this Windows ME share when I boot using Windows XP using Windows Explorer's "Map Network Drive".

Any help is appreciated.

Thanks.

---

### Post by naresh123 on 2009-03-23
Hello folks,
Does anyone have any advice (other than ditch the Windows ME machine :) ) or solution for me?

---

### Post by thehouseofho on 2009-03-23
Have you tried entering the username and password you use to log into your ME machine?  If you're asked for a domain, the domain would just be the machine's name.

---

### Post by naresh123 on 2009-03-23
I don't have a user name or password set up on my Windows ME, when it comes to logging into it.

I boot up and start using...so basically no users set up on it.

The only password that I have is what I configured while creating the shares on the Windows ME.

I don't believe I've tried using the Windows ME machine name as the domain name....I can try that I suppose.

I wonder if it has anything to do with the fact that the file system on the Windows ME is FAT32.

---

### Post by crokett on 2009-03-23
google the man page for mount and/or mounting Samba shares.  Then try mounting via mount.  The error messages you get are much more descriptive than the GUI.

---

### Post by naresh123 on 2009-03-23
Am I wrong in thinking that I need to set up a Samba share only if I want to share a drive on my Ubuntu machine and have a Windows machine see it?

If so, then what I'm trying to do is the opposite: I have a Windows ME share that I want to mount in Ubuntu. Don't care whether the Windows ME has any knowledge of the Ubuntu machine.

And like I'd mentioned I didn't have any problems mounting shares based on Windows NTFS.

I am going to try mount commands from the shell prompt though and see what happens.

Thanks.

---

