---
title: "startup without monitor probelms."
date: 2009-04-03
forum: General Help
---

### Post by raedbenz on 2009-04-03
Hi,,

Why when i start up the pc without connecting the monitor to it, it does not start normally. in the middle of the boot displays a message that says "screen and graphic card could not be detected."

coz i wana acces this pc remotlely using vnc.
how can i get round this?
cheers

---

### Post by cariboo on 2009-04-03
This happens because of "Bulletproof X" the way to work around the problem is to stop gdm from starting, then using X forwarding to run your applications. to stop gdm from starting open a terminal and type:

```
sudo update-rc.d -f gdm remove
```

this  will stop X from starting automatically. You can still start X by typing at the prompt:

```
startx
```

THe next thing you will need to do is to install the openssh-server package, openssh is in the repositories and can be installed using Add/Remove Programs, Synaptic Package Manager and of course the command line. To remotely run and graphical application in a terminal type:

```
ssh -X user@server
```

then once you are at the prompt on the remote computer type the name of the application you want to run, for example if you want to run the file manager you would type:

```
nautilus
```

Jim

---

### Post by raedbenz on 2009-04-07
hi,,,

The pc is connected via USB wireless adapter installed with ndiswrapper to the network.
The network will not setup unless i enter keyring password.

assume i dont have the monitor& keyboard, how could i connect the remote pc to netowrk. how can i disable the keyring 
authenticate.??
cheers

---

