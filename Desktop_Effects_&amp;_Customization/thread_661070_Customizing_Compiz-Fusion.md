---
title: "Customizing Compiz-Fusion"
date: 2008-01-07
forum: Desktop Effects &amp; Customization
---

### Post by gamelord12 on 2008-01-07
My answer probably lies in another thread, but I don't really know what I'm looking for.  I can't seem to figure out how to edit some specific options in Compiz-Fusion beyond telling it to enable "Extra" effects.  Also, how do I put my workspaces into cube view?

---

### Post by jryprt on 2008-01-07
> **gamelord12 said:**
> My answer probably lies in another thread, but I don't really know what I'm looking for.  I can't seem to figure out how to edit some specific options in Compiz-Fusion beyond telling it to enable "Extra" effects.  Also, how do I put my workspaces into cube view?
Here is a great guide [Forlong's Guide](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion#)


After you get thur Forlong's guide click the link in my Signature for more plugins.

---

### Post by gamelord12 on 2008-01-07
When I click on his link to download ccsm, it gives me a "Could not find file" error box.  I tried using a command in the terminal (which I'm not very good at, but this wasn't exactly a blind shot in the dark).

I typed in "sudo aptitude install compiz-config-settings manager" as an educated guess for how to do it.  "sudo" to give administrative privelages, "aptitude" for the program that downloads packages, and "install" with the rest of his link.  It gave me some good messages back in the terminal, but trying to run ccsm still does nothing.

---

### Post by jryprt on 2008-01-07
> **gamelord12 said:**
> When I click on his link to download ccsm, it gives me a "Could not find file" error box.  I tried using a command in the terminal (which I'm not very good at, but this wasn't exactly a blind shot in the dark).

I typed in "sudo aptitude install compiz-config-settings manager" as an educated guess for how to do it.  "sudo" to give administrative privelages, "aptitude" for the program that downloads packages, and "install" with the rest of his link.  It gave me some good messages back in the terminal, but trying to run ccsm still does nothing.

Try ```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by gamelord12 on 2008-01-07
It says it couldn't find the package.

---

### Post by dannyboy79 on 2008-01-07
do you have the extra repositories enabled? see here: [http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories](http://monkeyblog.org/ubuntu/installing/#enabling_extra_repositories)

---

### Post by jryprt on 2008-01-07
> **gamelord12 said:**
> It says it couldn't find the package.

Go to System>Administration>Software Sources, Ubuntu Software tab are the boxes checked

---

### Post by gamelord12 on 2008-01-08
Thanks a lot guys, it worked!  Now I just have to figure out why Firefox marks every word I type as misspelled, and I'll be set.

---

