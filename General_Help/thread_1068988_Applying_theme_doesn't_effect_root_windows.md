---
title: "Applying theme doesn't effect root windows"
date: 2009-02-13
forum: General Help
---

### Post by jonlemur on 2009-02-13
I've got a sweet theme from gnome-look, and it works great for most windows.  But if I run one certain programs that needs root privileges (like synaptic), they use a really old looking button and icon theme.  Any ideas on what can be done?  I'm using GNOME in Intrepid.

---

### Post by kanikilu on 2009-02-13
What theme are you using? I'm using the Shiki-Colors theme and that appears to apply to "root windows".

---

### Post by mcduck on 2009-02-13
The problem is simply that the themes are installed in your own home directory instead of installing them system-wide. Since Synaptic and other admin apps run as root user, and root doesn't have those themes available, the apps use default theme instead.

There's an easy solution to the problem: link your theme directory to root's theme directory:

sudo ln -s /home/*yourusername*/.themes /root/.themes
sudo ln -s /home/*yourusername*/.icons /root/.icons

Now root will always have same themes available as your own user has, and apps running as root will use same theme you are using.

---

### Post by geirha on 2009-02-13
When you install a theme, it is put under a hidden folder .themes in your home-directory, and will only apply for your user. The root user has it's own homefolder at /root. Copying your user's .themes folder to root's homefolder should make root windows themed too. 

```
sudo cp -r ~/.themes /root/
```

EDIT: mcduck beat me to it with a better answer :)

---

### Post by jonlemur on 2009-02-13
Thanks guys!

---

