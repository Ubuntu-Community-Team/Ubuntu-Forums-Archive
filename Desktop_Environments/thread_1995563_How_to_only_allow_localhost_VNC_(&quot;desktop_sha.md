---
title: "How to only allow localhost VNC (&quot;desktop sharing&quot;) connections in 12.04?"
date: 2012-06-03
forum: Desktop Environments
---

### Post by jsbmsu on 2012-06-03
In older releases, there was once an Advanced tab in the Remote Desktop Preferences Dialog (per this older tutorial: [http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop](http://www.techotopia.com/index.php/Remote_Access_to_the_Ubuntu_Linux_Desktop)), but now (12.04, perhaps recent releases too) it is renamed Desktop Sharing Preferences and only the basic settings remain.

Because I only intend to connect via SSH tunnel, I wish to deny all but localhost connections for security's sake. How do I access the Advanced settinsg? (Or at least, how do I set the deny localhost preference?)

---

### Post by adenbley on 2012-06-14
according to [this link]("https://help.ubuntu.com/community/VNC/Servers") you can just type:```
gsettings set org.gnome.Vino network-interface lo
```i have done that, but need to wait until i am away again to try it.

---

### Post by fabianofcarlos on 2012-06-18
it worked for me once I changed the comand line to

```
gsettings set org.gnome.Vino network-interface local
```

is it some king of bug? did I really narrow connections from local network computers?

---

### Post by figure002 on 2012-08-30
> **fabianofcarlos said:**
> it worked for me once I changed the comand line to

```
gsettings set org.gnome.Vino network-interface local
```is it some king of bug? did I really narrow connections from local network computers?

According to Ubuntu bug [#275340]("https://bugs.launchpad.net/ubuntu/+source/vino/+bug/275340") the "Localhost only" feature was removed from Vino, probably because it wasn't working properly. This features has indeed been replaced by the "network-interface" option and setting that to localhost should indeed limit to connections from localhost only. As mention in the upstream bug by Jonh Wendell:

 > local_only preference is now obsolete. Now you are able to select a network interface which vino must listen to.However, the bug I linked to talks about setting "network-interface" to "lo" instead if "local". But they are using "gconf-editor" and the "network-interface" option is missing there in Ubuntu 12.10. Using dconf-editor, however, you can find the option under: desktop > gnome > remote-access. The description for that option is as follows:

> If not set, the server will listen on all network interfaces. Set this if you want that accept connections only from some specific network interface. eg: eth0, wifi0, lo, ...Unfortunately I can't test this myself at the moment, but if you have access to a second computer in the network, you should be able test this yourself.

---

