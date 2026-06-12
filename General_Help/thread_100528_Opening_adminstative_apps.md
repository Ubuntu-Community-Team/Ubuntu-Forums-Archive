---
title: "Opening adminstative apps"
date: 2005-12-07
forum: General Help
---

### Post by dougwolfe on 2005-12-07
Hi Yall!  I just installed Ubuntu, so I am new to Ubuntu but not to debian based linux.  I have a small problem.
I can't open any administative applications from the gnome menu.  After I click on the item (for instance, Synaptic), a dialog appears asking for my password.  I give my user password, and then the dialog closes, but nothing happens.  I can open the applications from the terminal using su and my root password.  Thanks for your help in advance.

---

### Post by aysiu on 2005-12-07
What about when you launch the app from the terminal? What happens after you enter your password? This is what happens for me: ```
gksudo synaptic
(synaptic:11770): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:11770): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
``` By the way, that's what happens when it opens successfully.

---

### Post by teaker1s on 2005-12-07
there is a bug,
change launchers to use 'gksudo' for gui or 'sudo' for terminal

---

### Post by dougwolfe on 2005-12-07
in terminal, when i enter
gksudo synaptic
nothing happens

---

### Post by dougwolfe on 2005-12-07
I ran the debug command.   I don't know what to do after this.

doug@Ubuntu:~$ gksudo -d synaptic
buffer: -Sorry, user dou-
We won't need a password, it seems!
xauth: /tmp/libgksu1.2-Ec09gh/.Xauthority
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: synaptic
buffer: --
Oops... what's up?
xauth: /tmp/libgksu1.2-Ec09gh/.Xauthority
xauth_env: /home/hari/.Xauthority
dir: /tmp/libgksu1.2-Ec09gh

---

### Post by dougwolfe on 2005-12-07
fixed my own problem. Yeah!

I added a line to the file /etc/sudoers
   username All=(ALL) ALL
and changed username to my username

---

### Post by syncme on 2005-12-07
mine works but I enabled the root password.

sudo passwd root

Syncme

---

