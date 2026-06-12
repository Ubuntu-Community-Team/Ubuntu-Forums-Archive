---
title: "Display Ubuntu version on desktop"
date: 2009-05-08
forum: General Help
---

### Post by mjitkop on 2009-05-08
Hello all,

I was just wondering now if it was possible to display the version of Ubuntu on the desktop. It can be done in Windows and the question just came to my mind about Ubuntu.

Other related question: anywhere in the menus, where can you see the current version of Ubuntu that you are using? What about the patch level? 

Thank you.

---

### Post by x C0MMAND0 x on 2009-05-08
Go to Your Menu, then "System Tools" then "Sysinfo".

If you don't have it, install by using the following command.

```
sudo apt-get install sysinfo
```

---

### Post by 73ckn797 on 2009-05-08
Go to System/Administration/System Monitor. The first tab will list basic info.

---

### Post by x C0MMAND0 x on 2009-05-08
Are you familiar with conky?  If not, there is a nice frontend for it in the screenlets app.

Install screenlets by the following command, and then enable "Sysmonitor".  You get an output somewhat like the following screenshot.  You can have this as a panel on your desktop essentially, or however you'd like.

```
sudo apt-get install screenlets
```

[http://img158.imageshack.us/img158/9744/conky.png](http://img158.imageshack.us/img158/9744/conky.png)
^^Screenshot^^

---

### Post by mjitkop on 2009-05-08
Very nice. Thank you all for the quick replies and the suggestions. I will see this when I get home tonight. :)

---

### Post by codywohlers on 2009-05-16
> **mjitkop said:**
> 
I was just wondering now if it was possible to display the version of Ubuntu on the desktop. It can be done in Windows and the question just came to my mind about Ubuntu.


I haven't been able to find a way to do this yet.  Does anyone know how?  I would like to do this also.  I run many virtual machines and remote desktop sessions and I find it is useful.

---

### Post by wanchai on 2009-05-16
As it was mentioned before, conky (it's in the repository, see here for more infos: [http://conky.sourceforge.net/](http://conky.sourceforge.net/)) is a nice tool to display things on the screen background. In order to find out what version you are running, try the following:

cat /proc/version
cat /proc/version_signature
cat /etc/lsb-release

You can use conky to display the contents of these "files" on your screen background. Or write a perl or awk script that formats this info nicely and then you call that script from conky.

---

### Post by codywohlers on 2009-05-17
Thanks alot.  I will try that.

---

### Post by hyperdude111 on 2009-05-17
Conky does it in a nice text on the desktop

---

