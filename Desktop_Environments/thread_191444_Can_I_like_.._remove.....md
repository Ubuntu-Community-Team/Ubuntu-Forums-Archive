---
title: "Can I like .. remove...."
date: 2006-06-07
forum: Desktop Environments
---

### Post by MrGreen on 2006-06-07
HI,

I have installed ubuntu then kubuntu & now I have xubuntu running which is real sweet 

Now I want to remove kunbuntu & ubuntu to lighten my latop even more

Is this possible?

Already run apt-get remove *-desktop but kde & gnome apps are still there is this normal....

TIA

---

### Post by bluevoodoo1 on 2006-06-07
[http://www.ubuntuforums.org/showthread.php?t=96048](http://www.ubuntuforums.org/showthread.php?t=96048)

[http://www.ubuntuforums.org/showthread.php?t=96046](http://www.ubuntuforums.org/showthread.php?t=96046)

Hope those help.

---

### Post by Hanj on 2006-06-07
> is this normal....Yes. These packages are so-called meta-packages, that only depend on a bunch of other packages without actually doing anything themselves. When you remove the meta-package, the packages it depends on remain.

Maybe this will help? [http://ubuntuforums.org/showthread.php?t=96046&]("http://ubuntuforums.org/showthread.php?t=96046&")

---

### Post by mannheim on 2006-06-07
[QUOTE=MrGreen]HI,
Already run apt-get remove *-desktop but kde & gnome apps are still there is this normal....

[/QUOTE]
That's normal, because the *-desktop packages are "meta-packages": they are like "empty" packages which have other packages as dependencies. So when you install *-desktop with apt, you pull in all the dependencies also. Uninstalling a package does not uninstall its dependencies.

If you started with an ubuntu install, it's going to be hard to figure out what you can remove.

---

### Post by bionnaki on 2006-06-07
read this: [http://www.psychocats.net/ubuntu/purexfce.php](http://www.psychocats.net/ubuntu/purexfce.php)

---

### Post by MrGreen on 2006-06-08
Thanks guys for your replies ... guess I should have searched a bit harder

tried all three desktops .... xfce4 is lighter but prefer kde which is installed

What I may do (as I have only had install a few days !!) is install edubuntu if thats possible for my youngest child

 I was blown away by how easy ubuntu was to install... very easy to do

Thanks again

---

