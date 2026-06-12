---
title: "Msttcorefonts"
date: 2006-06-07
forum: Desktop Environments
---

### Post by 3zero2 on 2006-06-07
after installation of MSTTCOREFONTS some websites, even ubuntuforums, start to look really ugly in firefox

on the other hand, websites like box.net improve dramatically!

why is that?

---

### Post by Rackerz on 2006-06-07
I noticed this, I'm not sure really. There are ways to edit your font configuration to improve it, but I don't know how exactly.

---

### Post by 3zero2 on 2006-06-07
basically after some messing around i founf out that Arial is responsable for all this.

the question is now: how can i make arial look half decent on my TFT?

anyone?

---

### Post by Rondonjin on 2006-06-07
[QUOTE=3zero2]basically after some messing around i founf out that Arial is responsable for all this.

the question is now: how can i make arial look half decent on my TFT?

anyone?[/QUOTE]

The last couple of days there have been numerous posts and replies asking how to improve the look of font rendering in Ubuntu and a link has been posted so many times now I've lost count ;) 

Wayne

---

### Post by 3zero2 on 2006-06-07
really...must have missed that then...

any links?

---

### Post by LeeM on 2006-06-07
Help! I'm trying to install the msttcorefonts package. (I'm running Dapper). I've included "multiverse" in the  /etc/apt/sources.list file. 

(Following lines added to /etc/apt/sources.list:
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper multiverse
)

But when I do 
apt-get install msttcorefonts,
I get
[INDENT]Package msttcorefonts is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package msttcorefonts has no installation candidate
[/INDENT]

Any ideas of what I'm doing wrong???:( 

Thanks!

---

### Post by Rondonjin on 2006-06-07
[QUOTE=3zero2]really...must have missed that then...

any links?[/QUOTE]

[http://www.ubuntuforums.org/showthread.php?t=180647&highlight=fonts+x11](http://www.ubuntuforums.org/showthread.php?t=180647&highlight=fonts+x11)

---

### Post by oobuntoo on 2006-06-07
After I installed msttcorefonts, I've always run this command:

sudo dpkg-reconfigure fontconfig

and choose a combination of settings that makes Firefox font display look good. A good test page is Yahoo front page. You can just rerun the command until you find the combination you like.

---

### Post by 3zero2 on 2006-06-08
[QUOTE=oobuntoo]After I installed msttcorefonts, I've always run this command:

sudo dpkg-reconfigure fontconfig

and choose a combination of settings that makes Firefox font display look good. A good test page is Yahoo front page. You can just rerun the command until you find the combination you like.[/QUOTE]

will try that out and report. thanks

---

### Post by 3zero2 on 2006-06-08
[QUOTE=Rondonjin][http://www.ubuntuforums.org/showthread.php?t=180647&highlight=fonts+x11](http://www.ubuntuforums.org/showthread.php?t=180647&highlight=fonts+x11)[/QUOTE]

followed your suggestion and it's much better now. thanks!!

---

