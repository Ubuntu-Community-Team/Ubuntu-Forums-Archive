---
title: "synaptic option in System menu is gone! disappeared!"
date: 2008-05-07
forum: Desktop Environments
---

### Post by hurinth on 2008-05-07
:mad: I recently upgraded over the Internet from 7.10 to 8.04, days after I realize Synaptic is not present in the System>Administration submenu. 

I go to System>Preferences>Main Menu and I see the checbox un-checked, so I check it, but 1 second later I can see how it unchecks by itself... This happens with any item from the Administration submenu.

Now, if I got to ~/.local/share/applications and double click the Synaptic icon, I get the error in the attached image. 

Please anyone can help me here?

---

### Post by Bubba64 on 2008-05-07
> **hurinth said:**
> :mad: I recently upgraded over the Internet from 7.10 to 8.04, days after I realize Synaptic is not present in the System>Administration submenu. 

I go to System>Preferences>Main Menu and I see the checbox un-checked, so I check it, but 1 second later I can see how it unchecks by itself... This happens with any item from the Administration submenu.

Now, if I got to ~/.local/share/applications and double click the Synaptic icon, I get the error in the attached image. 

Please anyone can help me here?

Open the terminal and type sudo synaptic it will then ask for your password which will not show when you type but is being input. and see if it opens. Beyond that I am not sure what else to do.

---

### Post by hurinth on 2008-05-07
It won't open > hurin@Asfaloth:~$ sudo synaptic
[sudo] password for hurin: 
hurin@Asfaloth:~$ 

It stays there and never opens a thing, any other idea please!?!?

---

### Post by Nesai11 on 2010-01-25
Same problems after the last system update... Synaptic dissapeared as well as Administrative tools. I used the commands below, and was able to do a sudo synaptic to access it again... now i'm trying to reinstall the system updater (update-manager), since that seemed to dissapear as well.  i did, however, get these error messages 

(synaptic:17532): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

(synaptic:17532): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

(synaptic:17532): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

any thoughts?

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install ubuntu-desktop

---

### Post by gadolinio on 2010-01-25
Mmmm have you tried reinstalling synaptic?
Go to [http://packages.ubuntu.com/search?synaptic](http://packages.ubuntu.com/search?synaptic) and choose your version, then click on any server to download the package. Then try reinstalling it to see if it makes any difference...

---

