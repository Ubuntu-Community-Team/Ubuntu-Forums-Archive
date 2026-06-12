---
title: "uninstall virtualbox"
date: 2009-05-12
forum: General Help
---

### Post by stuart.reinke on 2009-05-12
I recently Installed VirtualBox 2.2.2 to give it a try. I've decided to set up a dual-boot instead (not enough ram for two os). 

I used Synaptic to uninstall VirtualBox and it is gone from the Applications-System Tools menu, however. When I go to terminal and print a list of all files and directories it's still there.

Is it sitting there waiting to be overwritten?

Do I need to manually delete it? If so, how can i delete a directory that isn't empty?

This is probably a simple question, but I'm a little confused. 

Thanks for any answers you have.

---

### Post by whoop on 2009-05-12
What files remain?

---

### Post by stuart.reinke on 2009-05-12
I don't know about specific files. The directories that are there include the main VirtualBox, Windows 98 (three of them ) and at least one virtual hard drive. There are files left in the directories.

---

### Post by Uzi304 on 2009-05-12
Well if you set up virtual hard drives, in my experience I've had to delete those before uninstalling Virtualbox. Other than that, they're probably just config files.

---

### Post by whoop on 2009-05-13
> **Uzi304 said:**
> Well if you set up virtual hard drives, in my experience I've had to delete those before uninstalling Virtualbox. Other than that, they're probably just config files.

I think you are right. It's comparable to removing openoffice for example, removing openoffice won't remove all the documents you created with it.

stuart.reinke: You can remove them if you want. To remove a directory with it's contents as root you can use this command (BE VERY CAREFULL WITH THIS):
```

sudo rm -rf <DIRECTORY>

```
If you are uncomfortable using the rm command you can also install virtualbox again, delete the guest os's using virtualbox and uninstall virtualbox again.

---

### Post by plamen_todoroff on 2009-05-13
Just delete the *.VirtualBox* folder in your home dir, no need to install and remove virtualbox again just to delete your virtual machines.

---

### Post by whoop on 2009-05-13
> **plamen_todoroff said:**
> Just delete the *.VirtualBox* folder in your home dir, no need to install and remove virtualbox again just to delete your virtual machines.

I don't use virtualbox but I am not 100% certain he is talking about the .VirtualBox directory. You can off course easily remove that with nautilus, I have a feeling that he is talking about files outside of his home dir. I use vmware and it stores my guests in /var/lib, so was under the assumption that VirtualBox has a similar setup.

---

