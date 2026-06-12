---
title: "Xfce Networking"
date: 2005-03-19
forum: Desktop Environments
---

### Post by Ryujin on 2005-03-19
I am running a server install of hoary with Xfce4 and the file manager cannot acccses my samba network, it can see the computers but cannot get to the files, I know the samba works because it ran flawlessly in Gnome.  Any ideas?

---

### Post by Glanz on 2005-03-21
Is this Xfce 4.2? ...and is the File Manager you are using for this Xffm or Rox?

---

### Post by retype on 2005-03-22
[QUOTE=Glanz]Is this Xfce 4.2? ...and is the File Manager you are using for this Xffm or Rox?[/QUOTE]
 Will Xfce 4.2 make it into hoary?

---

### Post by Glanz on 2005-03-22
[QUOTE=retype]Will Xfce 4.2 make it into hoary?[/QUOTE]

Perhaps..., but until then, there's nothing preventing you from installing it simply by adding the correct sources to your /etc/apt/sources.list file. [Here is how to do it in detail](http://www.debianhelp.org/modules.php?op=modload&name=News&file=article&sid=3442&mode=thread&order=0&thold=0) I use Xfce 4.2 in Hoary and all works well, but for Samba stuff I use the xffm file manager instead of the default Rox. Since Ubuntu follows a strict verification policy (md5's etc) for packaging, you will get warning messages from APT / Synaptic when installing Xfce 4.2 but you may safely ignore them. All works well!

---

### Post by Dendagard on 2005-10-12
Hi, 

I have a problem runing samba under XFCE 4.2, perhaps you can help me (i hope so).

I`ve installed samba and smbfs with synaptic under gnome and configurated samba there. Everthing works fine under gnome, so i can get access to my xp-computer and from my xp i get access to my share-folder on my ubuntu-notebook.

If i now run XFCE 4.2, what i normally do, because my notebook is a very old one, i get access from my xp-computer to my share-folder on my ubuntu-notebook, but no acces from ubuntu to xp.

When i run the xfce-network server, xffm starts at //ubuntu/xfsamba4  and i can see smb-network and my win-workgroup.

--> doubleclick on my workgroup shows me my xp-computer
--> doubleclick on my xp-computer shows me my shared folders on my xp-computer
--> doubleclick on a shared folder, doesn`t open the folder and i get an error:

no such device  no smbfs support detected in kernel 

what`s there going wrong? Under gnome it works fine.

---

