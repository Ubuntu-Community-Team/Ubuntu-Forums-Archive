---
title: "Citrix Install in Dapper"
date: 2006-07-12
forum: Desktop Environments
---

### Post by used2win32 on 2006-07-12
I have been searching here and on the Internet trying to find a set of instructions on installing the Citrix client software in Dapper.

I have found information for previous versions of Ubuntu, but not this one.  I do not know if the steps are the same.

Does anybody know where a guide is?  Can you direct me to some more information?

Thank you.

---

### Post by elj4176 on 2006-07-12
Well as far as I know there is a terminal services client installed by default in Ubuntu. You can use that and RDP to your Citrix box and it should work fine. I say *should* because that is the way I do it.
You can also check the downloads section on the citrix site for the linux version at [http://www.citrix.com/site/SS/downloads/details.asp?dID=2755&downloadID=3323](http://www.citrix.com/site/SS/downloads/details.asp?dID=2755&downloadID=3323)

or you could also use gnome-rdp and enter the citrix box IP. That works for me as well.
Here's a link to more info about this: 
[http://aros-exec.org/modules/newbb/viewtopic.php?topic_id=1541&forum=7&post_id=12385](http://aros-exec.org/modules/newbb/viewtopic.php?topic_id=1541&forum=7&post_id=12385)

Hope that helps!
EJ

---

### Post by used2win32 on 2006-07-12
Thank you for the information.  I do use the RDP client to connect to Windows Servers, unfortunatley I have to connect to a Citrix box as a client without desktop access.  I need to use the nFuse type plugin that lets the Citrix connection appear in a web browser.  

I know that I need the ICA Client software, I just want to make sure that I install it correctly.  Do I just download and install?  Are there dependencies to be aware of?  Can I apt-get ?

Thanks for any assistance.

---

### Post by elj4176 on 2006-07-13
It sounds like your setup might be slightly different than ours. We use a pass-thru connection if that makes any sense - that's what I was told. Apps are publshed for certain users and when they browse to the IP of the citrix server they can choose which apps to run - it basically looks just like an rdp session. 
I have not heard of the nfuse plugin before so I assume we do not need it here. I did not install the ICA client - the client that comes with ubuntu worked fine for me.
Sorry I cannot be of more help.

---

### Post by gungaden on 2006-07-13
I also am interested in properly configuring the Citrix ICA Client in Dapper. 
   I do not believe that the RDP solution will permit Citrix to encrypt the data, map local printers, or map local drives. 
   Of course these features are the reason that I wish to use the Citrix proprietary software instead of a simple RDP connection.

---

### Post by jgcamp99 on 2006-07-13
I wound up installing it thru the citrix.com tarball. Put it in /usr/lib in it's own folder and ran the setupwfc file as root. From there it puts it in the default directory. The terminal window that it runs in has a Eula that you have to go thru and agree to, it takes a while to enter after each line, but be careful, cause if you start pressing the enter button too fast and happy, you go by the place where the "Y" is entered. Then you have to go thru it again by rerunning it.

When it's finished you should get a menu item under Applications, Internet tree/menu on the top panel.

I don't recall, but I think I had to also install the Open Motif "2.2.3-1.2ubuntu2" version from the Ubuntu repositories too ? That's Synaptics Package Manager under the System pull down menus.

What you are looking for is "libmotif3" and anything else that implies motif. I did this prior to running the setupwfc file.

It's a pretty simple procedure, I did it as root, as I recall sudo didn't make me feel good that it installed cleanly or properly. Besides, as I recall too, I needed to be root to copy the extracted folders of the tarball to /usr/lib. From there, both root and the ubuntu created user were able to use the shared application in /usr/lib/ICAClient/

Have you ever used Citrix in a non Microsoft Windows OS ?, the Linux version is very similar to the way OS X sets up published applications.

---

### Post by jgcamp99 on 2006-07-13
Gungaden, isn't that something the host server has more control over. I know when I configure a published application, I have to do it a certain way that the employer that I work for has set it up to work. We went from a TCPIP to the TCPIP/Http configuration last weekend, so I had to change that aspect of the default configuration. But again, that was mandated by a change at the host server, not from my end. Had I selected that option it would have rejected me.

---

### Post by sidd-tx on 2006-07-29
I installed ICA Citrix client 9 on my Dapper machine using the Breezy HOWTO at:

[http://www.ubuntuforums.org/showthread.php?t=85398&highlight=citrix+ica+client](http://www.ubuntuforums.org/showthread.php?t=85398&highlight=citrix+ica+client)

Works fine. Local drives mapped correctly, but I had to set that up with "/usr/lib/wfcmgr.bin"   Logged out, and connected back up, and presto...! $C_Client mapped to my /home/user directory...

Still cannot get local printer to work with Citrix though, but I've managed a work-around for now...

Sidd...

---

### Post by mozetti on 2006-08-01
I'll be installing Citrix on Dapper pretty soon, myself, but I have a question first: When you use Citrix to connect from a Linux machine to a Windows machine, is there still the problem of Linux (not) writing to NTFS , or does that go away because you use Citrix as a go-between?

---

### Post by etank on 2006-08-08
I would think that Citrix would take care of that since you are accessing an app that is running on the server.

---

