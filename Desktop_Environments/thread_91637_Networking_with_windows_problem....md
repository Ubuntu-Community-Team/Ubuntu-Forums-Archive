---
title: "Networking with windows problem..."
date: 2005-11-17
forum: Desktop Environments
---

### Post by slimfrinky on 2005-11-17
Hi all, I've got a slight problem and I was hoping that you guys could help me.

I have a home network set up at my house, one Ubuntu (W00T!) machine, and one Windows XP machine.

After some doing I was able to mod my smb.conf file properly so that the Windows machine was about to access my shares with no issues.

However, no such luck on the Linux machine. When I use Nautilus to attempt to browse the network by going to Places->Network Servers->Windows Network, it doesn't come up with my remote Windows box.

I have performed a smbclient -L <hostname> from terminal, and the Windows shares are visible through there, and can be mounted with no major problems. It's just that they are not browseable through Nautilus. 

Normally I wouldn't care, but my wife needs to be able to use file-sharing as well, and refuses to learn anything but the basics.

Is there something I can do to fix this, or will I have to upgrade wives? <g>

---

### Post by matthewv on 2005-11-17
Maybe Places --> Connect to server...

---

### Post by HermanAB on 2005-11-17
Here is something that should get you going:
[http://www.aerospacesoftware.com/samba-debug-howto.html](http://www.aerospacesoftware.com/samba-debug-howto.html)

Cheers,

Herman

---

