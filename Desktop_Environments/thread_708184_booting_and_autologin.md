---
title: "booting and autologin"
date: 2008-02-26
forum: Desktop Environments
---

### Post by keratos on 2008-02-26
Hi

I use Grub to boot linux and at boot time append " autologin=yes" to the kernel line. This defines an environment variable "autorun" and sets it to "yes". 

I would like my system to pick up this setting and start gnome with autologin as user "fred". 

If "autologin"is not set at boot time (e.g. another Grub boot line) then the system boots as normal (i.e. to GDM and then user has to log in manually)

How can I accomplish this auto login depending on the value of "autologin"

Thanks in advance.

---

### Post by keratos on 2008-02-26
jut found out that the run level can be specified at the end of the grub kernel line.

So, I need to create a new runlevel, autostart gnome, and autologin.

How do I do this?

thanks.

---

### Post by Victormd on 2008-02-28
I was wondering the same thing.

---

### Post by keratos on 2008-03-01
Can anyone on the Ubuntu forums please help.

---

### Post by cecilpierce on 2008-03-01
In gnome goto System>Administratiion>Login Window>Security>Auto Login.

---

### Post by keratos on 2008-03-02
Thanks muchly.

---

