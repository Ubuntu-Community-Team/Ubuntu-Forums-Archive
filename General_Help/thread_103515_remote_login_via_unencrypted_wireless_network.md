---
title: "remote login via unencrypted wireless network"
date: 2005-12-14
forum: General Help
---

### Post by Hotchilli on 2005-12-14
I want to set up a remote login to my box at the moment I connect through
a unencrypted wireless network with 3 people are on the network including
myself. they are in xp boxes. tHERE is a firewall on the ip address as it times
out during a traceroute.

What probems might I have via remote conection to my box with regard to xp
firewall?


HC:???: :???:

---

### Post by Mr. Electric Wizard on 2005-12-14
You talking remote connection VNC or what?
And are you talking remote connection from the internet, or just internally?
If from the internet, then you'll probably just have to Forward the VNC port to your machine.
There is a tweak you have to do in System--> Sessions also I believe.

---

### Post by Hotchilli on 2005-12-14
Its just  to connect from another location via the internet so I can work on projects on my machine whils away from home, not local.
Is there a howto on this setup please. remote access to my linux
box from a windows box .

HC:smile: :smile:

---

### Post by Hotchilli on 2005-12-14
I going to connect via putty on ssh on a windows box 
nedd to know how


hc:smile: :smile:

---

### Post by RAOF on 2005-12-14
Well, you can install the ssh-server.  It's the package called "openssh-server".  Installing that will set up a ssh server on the default port of 22.  That is all you need, software wise.

---

### Post by Hotchilli on 2005-12-15
Thanks for your posts.

I have installed  openssh-server.

Is there a gui for ssh I did a search and found gtunnel wondered
if anything else exists

hc:smile: :smile:

---

### Post by Mr. Electric Wizard on 2005-12-15
There is a front end if you use WinSCP.
It is set up like an FTP program, two panes - one for the host machine, and one for the remote machine.
You can drag-drop files, and edit files directly through the GUI.  I use a combination of putty and WinSCP to administer my boxes.
It's a beautiful thing!
;)

---

### Post by Hotchilli on 2005-12-15
many thanks for your post.

One point putty is for windows?

hc:smile: :smile:

---

### Post by Hotchilli on 2005-12-15
WinSCP for windows also as putty Perhaps I have lost the plot I was thinking
about a gui for breezy b 5.10

hc:???:

---

### Post by RAOF on 2005-12-15
What would you want the gui to do?  If you want a gui for copying files over ssh, then I believe that you can use Gnome to sort-of-mount over ssh.

From memory, from nautilus (the file manager) it's something like:
Map network drive->ssh
and then you can copy to/from the remote computer as if it was a local drive.

---

