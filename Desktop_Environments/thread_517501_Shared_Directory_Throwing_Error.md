---
title: "Shared Directory Throwing Error"
date: 2007-08-04
forum: Desktop Environments
---

### Post by Ingla on 2007-08-04
Hello.

I've finally succeeded in setting up a Linux-Linux network between two machines which sit side by side, using NFS. One machine is running Feisty and the other Dapper.

I shared the home folders on both machines and everything seems to be running fine, with the share mounting automatically on boot on the Feisty machine, but requiring manual mount on Dapper (for some reason).

However, on logging in to Feisty (my main computer) I get an error notice:

"User's $HOME/.dmrc file is being ignored, preventing default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users."

While the notice is pretty much self explanatory, I really don't want to create a special folder for shares. Only my internal network IP's are allowed access, and I don't really want to have to first move files to another directory before sharing with myself.

Is there any way I can tell Ubuntu to let me share my home folder with write privileges without arguing? Dapper didn't bring any error but, as mentioned the automount didn't work. (This is my first restart of both boxes since creating the network).

What are the ramifications of letting .dmrc to continue to be ignored? Is that a problem (when I first booted in I had lost my screen resolution and only had the option of 800x600, but a reboot returned the original settings ... has that got something to do with this file)?

Anybody able to advise?

Thanks

---

