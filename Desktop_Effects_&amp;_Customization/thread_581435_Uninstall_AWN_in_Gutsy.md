---
title: "Uninstall AWN in Gutsy"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by dmber on 2007-10-19
Well I upgraded to Gutsy and I'm pretty disappointed so far.  I don't know, it's like Feisty and Gutsy didn't talk to each other during the install.  

If some stuff from Feisty is not compliant with Gutsy or whatever (AWN) it should be totally removed from the system and the user should be told this.  For example, AWN does not work in my new Gutsy upgrade.  But it's still there in my Accessories folder.  The AWN manager works fine but AWN doesn't.  I want to completely uninstall AWN but I don't know how to at this point.  I went to synaptic and removed all the AWN associated files.  But it's still up in my Menu chugging away.  

Now I'm stuck with a non-working AWN and when I try to install a working one, it's a no go.

Please help me uninstall AWN.  I found the folder where I believe AWN has been installed from source in.  I cp'd to that  folder in the terminal and did a sudo make uninstall and i got:

make: *** No rule to make target `uninstall'.  Stop.

I don't know what that means.

Thanks.

---

### Post by jbdev on 2007-10-19
I would just go to the AWN site and get the info to Install a .deb for Gutsy .. 

I did an upgrade and everything works great.

If you originally installed AWN on feisty yourself and did not use a package manager then the upgrade process will not remove it for you. Although I am not sure if it will still give you a prompt to let you know it is not compatible. 

If you go install a .deb of awn it should update what you currently have and if you are still havening problem I would make sure to delete any config files for AWN

Hope this helps

---

