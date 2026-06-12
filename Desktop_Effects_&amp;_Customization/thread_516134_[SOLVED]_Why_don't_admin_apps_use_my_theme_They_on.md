---
title: "[SOLVED] Why don't admin apps use my theme? They only ever use the Human one"
date: 2007-08-02
forum: Desktop Effects &amp; Customization
---

### Post by rainwalker on 2007-08-02
I'm currently using the Feisty New Human theme (the original, not version 2), and I'm wondering why it doesn't apply to administrative stuff (like Synaptic, or when using an application to do something with admin privileges)? 
The default Human theme is the only one out of the many ones themes I've tried that ever worked with these things.

---

### Post by AlexenderReez on 2007-08-02
you need manually set it


> sudo ln -s /home/<USERNAME>/.themes /root/.themes

sudo ln -s /home/<USERNAME>/.fonts /root/.fonts

 sudo ln -s /home/<USERNAME>/.icons /root/.icons


---

### Post by rainwalker on 2007-08-02
> ln: target `/root/.themes' is not a directory
ln: target `/root/.fonts' is not a directory
ln: target `/root/.icons' is not a directory

Any ideas?
I haven't seen this "root" folder anywhere

---

### Post by kkellner on 2007-08-02
try this:

```
sudo gnome-theme-manager
```

and then set the theme you want for the admin applications.  this worked for me.

---

### Post by vexorian on 2007-08-02
the commands were wrong, basically :

```

sudo ln -s /home/<USERNAME>/.themes /root/
sudo ln -s /home/<USERNAME>/.fonts /root/
sudo ln -s /home/<USERNAME>/.icons /root/

```

is what you want to do.

sudo gnome-theme-manager doesn't help, unless you manually install the themes again...

---

### Post by SkiesOfAzel on 2007-08-03
Just sudo nautilus and copy your .themes  folder from your /home/yourname folder to the /root folder.
[EDIT]
 Ups ,  sorry Vexorian, i didn't pay attention to your post, and it seems a more elegant solution too.

---

### Post by rainwalker on 2007-08-04
> **vexorian said:**
> the commands were wrong, basically :

```

sudo ln -s /home/<USERNAME>/.themes /root/
sudo ln -s /home/<USERNAME>/.fonts /root/
sudo ln -s /home/<USERNAME>/.icons /root/

```

is what you want to do.

sudo gnome-theme-manager doesn't help, unless you manually install the themes again...

Aha! Thank you very much! :)

---

