---
title: "Add splash screen?"
date: 2009-06-01
forum: Desktop Environments
---

### Post by telmore007 on 2009-06-01
I know how to change the splash screen but how do you add one? What folder? 

Thanks

---

### Post by MichaelSammels on 2009-06-01
Try this post:

[http://ubuntuforums.org/showthread.php?t=11478](http://ubuntuforums.org/showthread.php?t=11478)

---

### Post by telmore007 on 2009-06-01
That did not really help, where is the gmone foler? Under file system where is that folder?

Thanks

---

### Post by MichaelSammels on 2009-06-01
.gnome is in your home folder. Press Ctrl+H to see it. Your filesystem is located at /

(Open Computer to get there).

---

### Post by telmore007 on 2009-06-01
From the home folder I don't have .gmone I have .gnome2. Where should I paste splashscreen image?

---

### Post by MichaelSammels on 2009-06-01
I am not too sure, have you tried this from terminal:

```
sudo gconftool-2
```?

Or checked the login settings?

---

### Post by telmore007 on 2009-06-01
I'm new to ubuntu so what I do after I type that in I don't know..

---

### Post by MichaelSammels on 2009-06-01
Try this:

In terminal type: ```
sudo gconf-editor
```

Once there browse to:

/apps/compiz/plugins/splash/allscreens/options

:)

---

### Post by telmore007 on 2009-06-01
command not found.

---

### Post by MichaelSammels on 2009-06-01
Are you not using GNOME? If you are using something such as Xfce, I am not sure.

---

### Post by MichaelSammels on 2009-06-01
Try here:

[http://ubuntuforums.org/showthread.php?t=377681](http://ubuntuforums.org/showthread.php?t=377681)

---

### Post by telmore007 on 2009-06-01
Xfce

---

