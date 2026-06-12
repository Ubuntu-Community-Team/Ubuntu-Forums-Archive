---
title: "corrupted root login profile"
date: 2006-06-02
forum: Desktop Environments
---

### Post by frogotronic on 2006-06-02
Hi,

When I login as root from the promt - The GNOME panel hangs.

Is there a way to "rebuild" or reconfigure this?

Logging on as regular user is totally okay.

---

### Post by PriceChild on 2006-06-02
Where are you logging in as root? :O The gnome greeter? :s

Why don't you use sudo inside terminals when needed? :S

---

### Post by frogotronic on 2006-06-02
[QUOTE=PriceChild]Where are you logging in as root? :O The gnome greeter? :s

Why don't you use sudo inside terminals when needed? :S[/QUOTE]

Bizarrely, the problem has fixed itself.  I love Linux :-)

Why?  I had to install a program and this was in the first few days of my using Ubuntu (from a MS windows background).  I didn't understand the directory structure, file permissions, etc.  It was a major NOOB mistake.  Now that I have gained knowledge, I went back in as root and fixed all the wierd file changes that I had made and reconfigured GNOME to be identical to my regular use login. (ie. gnome power manager, GTK WiFi, etc.)

It's all good now.

Thanks,
CH

---

### Post by Melvil on 2006-06-02
Never ever login as root!
If you need to perform some tasks as root then put "sudo" (or gksu for GUI) before your command and enter **your** password when asked.

---

