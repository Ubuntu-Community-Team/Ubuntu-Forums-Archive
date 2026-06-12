---
title: "sudo_autopasswd: command not found"
date: 2022-11-27
forum: Desktop Environments
---

### Post by prusso555 on 2022-11-27
After following the documentation here to start gnome with the windows subsystem for linux 2:[URL="https://x410.dev/cookbook/wsl/running-ubuntu-desktop-in-wsl2/"]

Running Ubuntu Desktop in WSL2 - X410.dev[/URL]

I have the following notifications coming out from the Ubuntu 22.04.01 LTS terminal on startup:


    sudo_autopasswd: command not found
    [sudo] password for prusso:
    * Starting system message bus dbus                                                                              [ OK ]
    network-manager: unrecognized service
    sudo_resetpasswd: command not found
    prusso@SurfacePro8:~$


I tried to add my username to the sudoers file but I still have the same notifications coming out. Does anyone know if there is a way to get these notifications to go away? That network-manager is an unrecognized service has it moved to a 
new name or is there maybe some other difficulty. I got these notifications to come up after folling the WSL2 gnome
desktop setup instructions at X410.dev for Ubuntu. A few bash scripts are added to bash so the GUI desktop environment 
can start up which is working.


Thanks...

---

### Post by Holger_Gehrke on 2022-11-27
Linux rewards careful readers. You didn't follow the instructions given in the link in step 2 to create a file '~/.bash_sysinit' which would include definitions for the functions 'sudo_autopasswd' and 'sudo_resetpasswd'. And the service is probably a misspelling: on Ubuntu 22.04 it's 'NetworkManager', not 'network-manager'.

Holger

---

### Post by yancek on 2022-11-28
I have not used WSL but see frequent posts here regarding it and it is definitely not the same as a full install of Ubuntu so things are not going to work the same as Ubuntu.  It's a microsoft creation and you might have better luck on a windows forum, or maybe not.  I agree with the post above, a lot of times careful reading prevents problems.  Good luck.

---

