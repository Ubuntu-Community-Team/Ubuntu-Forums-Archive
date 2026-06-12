---
title: "Cannot Launch Synaptic"
date: 2018-09-24
forum: Desktop Environments
---

### Post by gregory7 on 2018-09-24
I am on Gnome and seem unable to launch Synaptic. Others seem to have this issue in Wayland, but I am in Gnome, though I have the same problem in xfce.

---

### Post by gregory7 on 2018-09-24
I reinstalled, but to no avail

---

### Post by gregory7 on 2018-09-24
Strangely I can start up without administrative privileges by simply typing synaptic into the terminal.

---

### Post by gregory7 on 2018-09-25
Still a problem, cannot find a solution anywhere. How can it work without a sudo? Is the administration login failing?

---

### Post by oldfred on 2018-09-25
I use gnome-panel or fallback without issue. 
But it asks for password after I launch it from applications menu.

When you use terminal does it show any error messages?

If I use terminal I have to use sudo to allow changes. 
Without sudo it says I cannot install, but can export list of apps and a couple of minor things.

---

### Post by gregory7 on 2018-09-25
> **oldfred said:**
> I use gnome-panel or fallback without issue. 
But it asks for password after I launch it from applications menu.

When you use terminal does it show any error messages?

If I use terminal I have to use sudo to allow changes. 
Without sudo it says I cannot install, but can export list of apps and a couple of minor things.

Hi, thank you so much for your reply.

Maybe I misunderstand, but is this to do with not being able to fire up synaptic in administrator mode? If so my lack of knowledge is preenting me from seeing your solution. Could you please perhaps elucidate more clearly? For example, I am unable to type sudo synaptic as it gives this message:
No protocol specified
Unable to init server: Could not connect: Connection refused


(synaptic:7200): Gtk-WARNING **: 06:14:16.860: cannot open display: :0

I am also unable to type sudo nautilus which should surely work - same message.

---

