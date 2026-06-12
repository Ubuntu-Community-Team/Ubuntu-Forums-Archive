---
title: "SSH has some graphical key unlocker"
date: 2009-04-15
forum: General Help
---

### Post by endfx on 2009-04-15
I'm using 8.04. Whenever I try to ssh into a server I get a gui popup that prompts me to unlock my key. I don't want to use the gui to unlock my key, I want to use the regular openssh command line to unlock my key.

Can someone tell me how to get rid of this thing? I'd rather not uninstall any gnome keyring software, I just don't want ssh to be using it.

Thoughts?

Thanks.

---

### Post by Yashiro on 2009-04-15
You've probably got a broken setup on your machine.

Worst case scenario is you remove the SSH keys from the gnome applet and your .ssh folder and regenerate them using the command line NOT the gui.

Best case, you just need to cat your id_rsa to your local authorised_keys file.

---

