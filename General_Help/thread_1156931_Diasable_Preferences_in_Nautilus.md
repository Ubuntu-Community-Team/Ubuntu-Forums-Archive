---
title: "Diasable Preferences in Nautilus"
date: 2009-05-12
forum: General Help
---

### Post by slank on 2009-05-12
Hey,
is there a way to disable Preferences in Nautilus??:confused:
I created a .hidden File to hide unix file structure ([http://ubuntuforums.org/showthread.php?t=76521).:](http://ubuntuforums.org/showthread.php?t=76521).:))
Is there an Option to disable the Options "Show hiden files" in Nautilus??:confused:

thy in advance

---

### Post by slank on 2009-05-14
no idea .... nobody :confused:

---

### Post by drs305 on 2009-05-14
> **slank said:**
> Hey,
is there a way to disable Preferences in Nautilus??:confused:
I created a .hidden File to hide unix file structure ([http://ubuntuforums.org/showthread.php?t=76521).:](http://ubuntuforums.org/showthread.php?t=76521).:))
Is there an Option to disable the Options "Show hiden files" in Nautilus??:confused:

thy in advance

Are you trying to remove the option to either hide or display the hidden files? I played with gconf-editor and can't find a way to remove the option entirely, either as a user or root.

If you can't hide the .files and that is what you are looking for, that is simply done by nautilus Edit, Preferences, View tab, Show Hidden and backup files, or ALT-H.

---

### Post by slank on 2009-05-15
thx for reply ;)

I'm trying to remove the option to either hide or display the hidden files. 
I dont want that users can go to "Edit, Preferences, View tab, Show Hidden and backup files", or press ALT-H.

No way to turn that off??

---

### Post by kirsis on 2009-05-15
The GoboLinux distro includes a kernel module that lets you hide files/folders from the userspace.

They're accessible as per usual, but won't show up in dir listings. Look into that.

[http://gobo.kundor.org/wiki/GoboHide](http://gobo.kundor.org/wiki/GoboHide)

---

### Post by roc.texas on 2010-12-02
Did anyone figure out how to remove the 'show hidden files' option in nautilus so that users that are using a public machine can not view hidden files so easily?

---

