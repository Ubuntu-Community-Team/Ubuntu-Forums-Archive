---
title: "[SOLVED] unable to perform certain administrative tasks - no password prompt"
date: 2008-08-16
forum: Desktop Environments
---

### Post by carelesshx on 2008-08-16
Hi everybody

I can't use Update Manager or Add/Remove on Ubuntu because when I click on 'Apply' in either of these application, the box that normally appears asking for my password does not appear. The window eventually turns grey and hangs, and must be quit using System Monitor. This is quite annoying because the update manager is telling me there are 60+ updates to install.

I don't think I've made any significant changes to the system to cause this problem; the last changes I made were to install some HTML editing software, which was the last time these processes worked properly.

EDITED TO ADD:

Also, when I download .deb files from the internet, the Package Installer, but fails to do anything when I click 'Install Package'. Normally I would expect a password prompt here, so I suspect this is part of the same problem.

---

### Post by olejorgen on 2008-08-16
What happens if you try to execute ```

gksudo synaptic
``` in a terminal?

---

### Post by carelesshx on 2008-08-16
> **olejorgen said:**
> What happens if you try to execute ```

gksudo synaptic
``` in a terminal?
A tab appears on the panel at the bottom of the screen (next to Firefox etc.) saying "Starting Administrative Application", hangs around for about 10 seconds and then disappears. This also happens in the cases I mentioned above, which I forgot to mention. I also lose the user@hostname prompt in the terminal window.

---

### Post by olejorgen on 2008-08-16
Strange... no password prompt either? Or output in the terminal?
Try ```
sudo synaptic 
``` ?

---

### Post by carelesshx on 2008-08-16
> **olejorgen said:**
> Strange... no password prompt either? Or output in the terminal?
Try ```
sudo synaptic 
``` ?
```
<user>@<hostname>:~$ sudo synaptic
sudo: unable to resolve host <hostname>
[sudo] password for <user>: 
```
And then it runs as expected.

I've never used Syanptic to select what to install though so it would be better to have the built-in installer working - as well as the update manager of course.

It did throw up a couple of errors in the terminal while it was running, however:
```
(synaptic:8632): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

(synaptic:8632): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

(synaptic:8632): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed
```
If that is relevant.

I'm going to work now, so it will be a few hours before I'm able to respond again. Thanks for the help so far.

---

### Post by the yawner on 2008-08-16
> **carelesshx said:**
> ```
<user>@<hostname>:~$ sudo synaptic
sudo: unable to resolve host <hostname>
[sudo] password for <user>: 
```
And then it runs as expected.


I'm not sure if it's related but regarding this error, kindly type the following commands on the terminal.
```
cat /etc/hostname
```
and
```
cat /etc/hosts
```

I once encountered a couple of issues on an Ubuntu server when I did a hostname change and got the same error *unable to resolve host <hostname>*. Apparently, the hostname must also be declared under /etc/hosts to resolve to your machine.

---

### Post by randytuggle on 2008-08-16
The gray issues are usually caused by desktop effects. If anything turns gray, turn your desktop effects off and see if that helps.

---

### Post by olejorgen on 2008-08-16
Hm, it's strange it complains about the host.. Not really sure what that means though.

You can run the install/remove program, if you check what the command is and do ```
sudo <command>
``` Not sure what <command> is, (I don't use gnome) but you could check it in the menu editor. (alacarte I think it's called)

The update manager is worse, since it's an applet (I think?). I theory you could run gnome-panel with sudo, but I'm not sure if that's a good idea. And it doesn't really solve the problem either.

Try creating a new user with administrator priveliges and check if you have the same problem there. (You proabably have to locate the command name, and run it as sudo for this too)

---

### Post by carelesshx on 2008-08-16
> **the yawner said:**
> I'm not sure if it's related but regarding this error, kindly type the following commands on the terminal.
```
cat /etc/hostname
```
and
```
cat /etc/hosts
```

I once encountered a couple of issues on an Ubuntu server when I did a hostname change and got the same error *unable to resolve host <hostname>*. Apparently, the hostname must also be declared under /etc/hosts to resolve to your machine.
```
tim@ubuntubox:~$ cat /etc/hostname
ubuntubox
tim@ubuntubox:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 ubuntubox.home196

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
This is all correct as far as I am aware.

---

### Post by carelesshx on 2008-08-16
> **randytuggle said:**
> The gray issues are usually caused by desktop effects. If anything turns gray, turn your desktop effects off and see if that helps.
I assumed windows turned grey to indicate they were busy or unresponsive...

---

### Post by carelesshx on 2008-08-16
> **olejorgen said:**
> Hm, it's strange it complains about the host.. Not really sure what that means though.

You can run the install/remove program, if you check what the command is and do ```
sudo <command>
``` Not sure what <command> is, (I don't use gnome) but you could check it in the menu editor. (alacarte I think it's called)

The update manager is worse, since it's an applet (I think?). I theory you could run gnome-panel with sudo, but I'm not sure if that's a good idea. And it doesn't really solve the problem either.

Try creating a new user with administrator priveliges and check if you have the same problem there. (You proabably have to locate the command name, and run it as sudo for this too)
OK... found the command for the gnome installer and ran it, had the same problem. Ran it with sudo and it worked correctly:
```
tim@ubuntubox:~$ sudo gnome-app-install
sudo: unable to resolve host ubuntubox
[sudo] password for tim: 

** (gnome-app-install:6874): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:1255: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)
```
pretty much.

Going to create a new admin user now and see how that goes.

---

### Post by carelesshx on 2008-08-16
> **carelesshx said:**
> Going to create a new admin user now and see how that goes.
That didn't work. New user has the same problems as my current user.

---

### Post by Separ on 2008-08-16
Ok, I know how to sort this.

I'll find my other post to someone who had the same issue.

EDIT: Here they are:
1. [http://ubuntuforums.org/showpost.php?p=5308973&postcount=12](http://ubuntuforums.org/showpost.php?p=5308973&postcount=12)
2. [http://ubuntuforums.org/showpost.php?p=5309072&postcount=18](http://ubuntuforums.org/showpost.php?p=5309072&postcount=18)

Ignore the gksudo bit in the first one but follow the steps in the second post to save the file. In your case you will want to change "ubuntubox.home196" to "ubuntubox"

---

### Post by carelesshx on 2008-08-17
> **Separ said:**
> Ok, I know how to sort this.

I'll find my other post to someone who had the same issue.

EDIT: Here they are:
1. [http://ubuntuforums.org/showpost.php?p=5308973&postcount=12](http://ubuntuforums.org/showpost.php?p=5308973&postcount=12)
2. [http://ubuntuforums.org/showpost.php?p=5309072&postcount=18](http://ubuntuforums.org/showpost.php?p=5309072&postcount=18)

Ignore the gksudo bit in the first one but follow the steps in the second post to save the file. In your case you will want to change "ubuntubox.home196" to "ubuntubox"
Solved, thanks.

---

### Post by Separ on 2008-08-17
No problem ;)

Don't forget to mark this thread as [SOLVED] from Thread Tools :)

---

