---
title: "File server?"
date: 2009-01-30
forum: General Help
---

### Post by Adeang on 2009-01-30
Hey everyone I love Ubuntu and different versions of it, but I want to know if I can make a file server from it?

I have windows vista, and I have an old computer with xp on it, and I would like to use wubi installer on the older xp computer and install some version of linux on it to make a file server, media files to be exact, but all files would be better. 

I have heard about opensuse and samba, but I would like to stick with ubuntu or another version of it.

Please point me in the right direction on how to create a file server!

Thanks, Adeang

---

### Post by mb_webguy on 2009-01-30
Ubuntu can absolutely be used as a file server.  Ubuntu (or technically Linux, of which Ubuntu is one particular distribution among many) is an operating system that can do anything any other operating system can do.

Samba, however, is the Linux implementation of the Windows file-sharing protocol.  It's the same as when you share a folder in Windows.

There are many ways Ubuntu can be used as a file server.  It can use Samba to share files to other computers in the same way as a Windows computer.  It can be set up as an ftp or web server.  It can be set up as a UPnP server to stream multimedia files to UPnP clients like Windows Media Player, an XBox 360, or a Playstation 3.  (There are other ways of sharing files as well, but those are the most common methods.)

If you can tell us exactly how you'd like to share files, we can help you set it up.

---

### Post by Adeang on 2009-01-30
Okay I'm downloading xubuntu, will that work the same? and I have to download samba once I install xubuntu right? 

but xubuntu will work too right? I have chosen xubuntu b/c its an older slower computer.

Thanks for quick reply.

---

### Post by hl2040 on 2009-01-30
> **Adeang said:**
> Hey everyone I love Ubuntu and different versions of it, but I want to know if I can make a file server from it?

I have heard about opensuse and samba, but I would like to stick with ubuntu or another version of it.

Opensuse is just a different "packaging" of linux with other free software. Ubuntu comes with Samba just as it does in Opensuse, and other "distributions".

The main steps in getting what you want up and running are:
1. Configuring SAMBA using the /etc/samba/smb.conf file
2. Getting samba to run as a service under ubuntu and to start upon boot
3. Getting the client machines to mount the "exported" folders

The easiest thing to do would be to enable sharing of home directories. If you install samba and browse the /etc/samba/smb.conf file you can see examples of how to configure it that way.

---

### Post by mb_webguy on 2009-01-30
Yes, Xubuntu is the same as Ubuntu except that it uses a different desktop environment and default applications.  Unfortunately, I'm not familiar enough with the Xcfe desktop to know the "easy way" (i.e. one that uses the GUI, rather than manually editing configuration files) to set up Samba shares on Xubuntu.

You can find information about setting up samba [here]("https://help.ubuntu.com/community/SettingUpSamba").  While that page assumes you're using Ubuntu, it's essentially the same for Xubuntu.

---

### Post by Adeang on 2009-01-30
okay thanks I'm still downloading xubuntu, and once I have everything done, I'll tell you guys what happens, thanks for the help, and I may be back if I run into any problems!

---

### Post by slakkie on 2009-01-30
If you want to use that pc as a fileserver there is no reason to install xubuntu/kubuntu or the plain old ubuntu. Just download the server edition image, burn the CD and install it. 

You could also use the netinstall cd, that one even asks for what you will use your machine so it will preinstall a set of packages for you. 

For a fileserver you only need samba, this will make sure you can share your directories with Windows machines (and OSX).

---

### Post by Adeang on 2009-01-30
dang, links please!

and is same easy setup or what? isn't it command line?

please fast reply I would like to not install xubuntu unless I have to! thanks.

---

### Post by slakkie on 2009-01-30
Ubuntu server edition:
[http://www.ubuntu.com/products/WhatIsUbuntu/serveredition](http://www.ubuntu.com/products/WhatIsUbuntu/serveredition)

And if you go here [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

You can select which iso you want to download, the alternate installer can install a cli only system, which is what you want. 

From there you can install packages via the console (or even better via ssh, but you need to install openssh-server first).

This one is the netinstall, its called the minimalcd: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by mb_webguy on 2009-01-30
If you are new to Linux, keep downloading Xubuntu.  The Ubuntu server has no desktop environment, so you do everything through the command line.

---

### Post by Yashiro on 2009-01-30
All ubuntu's can be used as a 'file server'. There is nothing special about file servers.

Just install any ubuntu you want then install samba and samba control panel.

---

### Post by Adeang on 2009-01-30
Okay thanks for quick replies, and thanks, Im kind of new to ubuntu, and I think Ill stick with xubuntu so I dont have to worry about the hard stuff, but in the future once I learn more I will most definitely try the server edition! 

Thanks 

Okay Ima install xubuntu and tell you guys how everything goes!

---

### Post by Adeang on 2009-01-31
I have xubuntu installed and now I'm trying to install samba and get the file server working, but I am having problems setting it up. please help.

I have started this guide [https://help.ubuntu.com/community/SettingUpSamba#Ubuntu%208.04%20And%20Later](https://help.ubuntu.com/community/SettingUpSamba#Ubuntu%208.04%20And%20Later)

and I got to the first part "sudo aptitude install samba" for the server and installs fine, i think.

but can't do anything else the guide says, like right click on a folder and click share folder or anything.

quick replies would be bomb! thanks.

---

