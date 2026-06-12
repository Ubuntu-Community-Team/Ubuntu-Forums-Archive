---
title: "rm -rf"
date: 2009-02-04
forum: General Help
---

### Post by utnubuuser on 2009-02-04
Hi -- I came across a posting on how to restore a messed up desktop. This is what they suggest:> cd /home/username
rm -rf .gnome2 .gconf .gconfd .metacity 
and then a reboot.

Anybody know if this would have the desired effect of restoring default settings as the poster suggests?  

Original blog-post:> [http://www.cahilig.org/restore-broken-ubuntu-desktop](http://www.cahilig.org/restore-broken-ubuntu-desktop)

Thanks

**The above commands DO restore desktop to original state**

---

### Post by ibutho on 2009-02-04
I think you should backup any files first before running "rm -rf". AFAIK deleting those files should restore GNOME back to the defaults.

---

### Post by Mostly Harmless on 2009-02-04
any files in the /home/username/ directory are either your files or preferences specific to your account, so deleting them would do exactly that (and rm = remove = delete), however you do not need to reboot, instead (I think) you can just kill gnome.

---

### Post by abn91c on 2009-02-04
before you run that **[COLOR="Blue"]rm -rf[/COLOR]** command read **[COLOR="Red"]this first[/COLOR]** [http://ubuntuforums.org/showthread.php?t=911613&highlight=harmful+commands](http://ubuntuforums.org/showthread.php?t=911613&highlight=harmful+commands)
to reinstall the desktop```
sudo aptitude reinstall ubuntu-desktop
```

---

### Post by Dies on 2009-02-04
> **utnubuuser said:**
> 

Anybody know if this would have the desired effect of restoring default settings as the poster suggests?  



Yes, it will. The command is safe to run if you want to delete your preferences, nothing malicious about it. 

Also, don't waste your time re-installing the entire desktop since that will NOT reset you personal preferences.

---

### Post by utnubuuser on 2009-02-06
Thanks Guys

I had no intentions of using the command, I just happened to find it in a blog,  - wondered because I'd seen warnings about rm -rf, and wanted to make sure it wasn't some malicious blogger tricking people into deleting their Ubuntu installs.

---

### Post by movin on 2011-11-03
What would be the corresponding action now that Ubuntu comes with Unity instead?

---

### Post by oldos2er on 2011-11-04
Closed. Please start a new thread for your question.

---

