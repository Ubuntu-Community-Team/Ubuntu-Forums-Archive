---
title: "something like Microsoft Remote Desktop?"
date: 2017-02-26
forum: Desktop Environments
---

### Post by naomibrown on 2017-02-26
Hi,

We used to be able to log into our network from outside work (that's probably not the technical term) and use files and programs. It's changed and now I'm trying to get to work something like Microsoft Remote Desktop (I think). I'm using 16.04 LTS, the 64 bit version. So far I've looked at teamviewer but when I installed it I got errors, I think dependency problems:

Selecting previously unselected package teamviewer:i386.
(Reading database ... 674390 files and directories currently installed.)
Preparing to unpack teamviewer_12.0.71510_i386.deb ...
Unpacking teamviewer:i386 (12.0.71510) ...
dpkg: dependency problems prevent configuration of teamviewer:i386:
 teamviewer:i386 depends on libjpeg62.

dpkg: error processing package teamviewer:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Errors were encountered while processing:
 teamviewer:i386

I wasn't sure whether I should install libjpeg62 or not ... so I thought I'd ask.

I then tried remmina. I typed in all the information I could find from the [mac instruction video]("https://whitleyacademy-my.sharepoint.com/personal/n_wilkes_whitleyacademy_com/_layouts/15/guestaccess.aspx?docid=076d62f65b00042d581d92f84cd870658&authkey=AbdReEvY17fEOqBpEf-aBeY") ITS provided but it keeps reporting that it can't connect and then the application crashes and disappears. Is it that I'm using the wrong information in the wrong boxes?

The only other thing I could think of was using a windows application as there is a file to download that will allow you to connect by just double clicking it.

Thanks,
Naomi

---

### Post by TheFu on 2017-02-26
Does your work allow remote connections through their firewall?
What type of computer/OS is running there?

For Linux-to-Linux, you can use ssh, sftp, scp, x2go, openvpn, and pretty much any other remote X/Windows method assuming the security requirements you have are met.  The 1st group of options use ssh tunneling and are considered secure.  VNC, RDP, and CIFS file sharing ARE NOT secure, so setting up a full VPN is needed.  OpenVPN is the normal solution for that and every protocol/port can be tunneled to provide the most security. There are issues with using broadcast-based file sharing like CIFS over a VPN. Not recommended.

Also, do you care if a 3rd party gains access to your work machine(s)?  Teamviewer and similar solutions let those companies have access, plus we all know that HTTPS isn't really secure.

Also, if work IT/networking didn't setup something to allow remote access, then you could be fired/terminated/sacked for circumventing security protocols by using something like teamviewer.  That might not be desirable.  Best to ask IT about it before you do it to check on corporate policy.

So if you can answer the top questions, we might be able to recommend something.

---

### Post by Autodave on 2017-02-26
Teamviewer is a good program. How did you install it? I always download the newest version and then use *gdebi *(in the repositories) to install it: it will handle the dependencies.

I have Teamviewer on 11 machines with no hassles on any of them.

---

### Post by howefield on 2017-02-26
> **naomibrown said:**
> I wasn't sure whether I should install libjpeg62 or not ... so I thought I'd ask.

The package you need is libjpeg62:i386

```
sudo apt install libjpeg62:i386
```

---

### Post by fulinhyu on 2017-03-01
> **naomibrown said:**
> Hi,

We used to be able to log into our network from outside work (that's probably not the technical term) and use files and programs. It's changed and now I'm trying to get to work something like Microsoft Remote Desktop (I think). I'm using 16.04 LTS, the 64 bit version. So far I've looked at teamviewer but when I installed it I got errors, I think dependency problems:

Thanks,
Naomi

The easiest for me at least was using Remote Desktop Viewer and selecting the RDP connection type. Connect to the VPN and then log in using the machine's IP address. Works well for a couple different places I remotely manage (and works just like Microsoft Remote Desktop).


FuLinHyu

---

### Post by Habitual on 2017-03-01
I use rdesktop with a dozen switches. :)

---

