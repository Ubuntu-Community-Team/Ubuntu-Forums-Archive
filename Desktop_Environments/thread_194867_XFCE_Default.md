---
title: "XFCE Default"
date: 2006-06-12
forum: Desktop Environments
---

### Post by Stambo00 on 2006-06-12
I recently installed the XFCE Environment with the command:

sudo apt-get install xubuntu-desktop

Unfortunately it has made it my default environment. Even when I change it to the gnome default in the login screen it reverts back to xfce next time I log in. It also displays the xfce boot down screen annoyingly even when I'm logging out of gnome.

How can I have gnome as my permanent default without uninstalling xfce?

---

### Post by aysiu on 2006-06-12
Can you try editing the /home/stambo/.dmrc file?

---

### Post by Stambo00 on 2006-06-12
Yes, I can edit .dmrc and it is set as Gnome.

When I log out of Gnome the xfce logout splash screen appears which is very annoying.

How can I fix this?

---

### Post by aysiu on 2006-06-12
[QUOTE=Stambo00]Yes, I can edit .dmrc and it is set as Gnome.[/quote] Hm. That's weird. Maybe the permissions on the ~/.dmrc file are off?

Type ```
cd
ls -al
``` Part of the output should read ```
**-rw-------**  1 stambo stambo     24 2006-06-12 00:16 .dmrc
```

> 
When I log out of Gnome the xfce logout splash screen appears which is very annoying.

How can I fix this? [This may help](http://www.ubuntuforums.org/showpost.php?p=1104903&postcount=6).

---

### Post by Stambo00 on 2006-06-12
The permissions are correct for the file.

Ive made some progress on the extrenal link. I needed to type "config" rather than "configure" as directed in the post.

I'll tell you how it goes

---

### Post by aysiu on 2006-06-12
Sorry! I appear to be causing more problems than I help you solve.

Maybe you can just uninstall it... ```
sudo aptitude remove xubuntu-artwork-usplash
```

---

### Post by Stambo00 on 2006-06-12
The following solved my problem: 

1. "sudo update-alternatives --config usplash-artwork.so"

2. Choose usplash-default.so

3. "sudo dpkg-reconfigure linux-image-`uname -r`"

The other posts suggestion no longer works. Maybe the code input changed from configure to config.

Thanks for helping me work through it.

---

### Post by aysiu on 2006-06-12
But XFCE is still your default desktop environment...?

---

### Post by Stambo00 on 2006-06-12
No, Gnome is my default desktop environment but I still have xfce available if I want to boot into it.

---

### Post by aysiu on 2006-06-12
Great. So problem solved, then.

---

