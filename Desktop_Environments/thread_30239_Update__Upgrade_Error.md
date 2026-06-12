---
title: "Update / Upgrade Error"
date: 2005-04-27
forum: Desktop Environments
---

### Post by -TayloR- on 2005-04-27
Hey all, well im fairly new to using Kubuntu and i browsed the ubuntuguides website and noticed two commands to up date, they were:

```

sudo apt-get update
sudo apt-get upgrade

```

so i ran these two commands and got the following error:

```

Preconfiguring packages ...
(Reading database ... 62450 files and directories currently installed.)
Preparing to replace kdelibs-data 4:3.4.0-0ubuntu3 (using .../kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf
Preparing to replace openoffice.org-bin 1.1.3-8ubuntu2 (using .../openoffice.org-bin_1.1.3-8ubuntu2.3_i386.deb) ...
Unpacking replacement openoffice.org-bin ...
Preparing to replace openoffice.org-l10n-en 1.1.3-8ubuntu2 (using .../openoffice.org-l10n-en_1.1.3-8ubuntu2.3_all.deb) ...
Unpacking replacement openoffice.org-l10n-en ...
Preparing to replace ttf-opensymbol 1.1.3-8ubuntu2 (using .../ttf-opensymbol_1.1.3-8ubuntu2.3_all.deb) ...
Unpacking replacement ttf-opensymbol ...
Preparing to replace openoffice.org 1.1.3-8ubuntu2 (using .../openoffice.org_1.1.3-8ubuntu2.3_all.deb) ...
Unpacking replacement openoffice.org ...
Preparing to replace openoffice.org-kde 1.1.3-8ubuntu2 (using .../openoffice.org-kde_1.1.3-8ubuntu2.3_i386.deb) ...
Unpacking replacement openoffice.org-kde ...
Preparing to replace openoffice.org-thesaurus-en-us 1.1.3-8ubuntu2 (using .../openoffice.org-thesaurus-en-us_1.1.3-8ubuntu2.3_all.deb) ...
Unpacking replacement openoffice.org-thesaurus-en-us ...
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What do the following parts mean or whats gone wrong and how do i solve it?

```

Preparing to replace kdelibs-data 4:3.4.0-0ubuntu3 (using .../kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb) ...
Unpacking replacement kdelibs-data ...
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/default.kde', which is also in package knetworkconf

```

```

Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Anyone know whats wrong?

---

### Post by philipacamaniac on 2005-04-27
Shoot, that happened to me and I can't remember why. The only way I got it to work again was to remove kde, and then reinstall it with apt-get.

Not that I recommend that, because I had to reinstall all of my universe packages that depended on kde. Maybe someone else has a solution?

---

### Post by dave9191 on 2005-04-27
kdelibs are messed up at the moment. I installed kubuntu the other day, updated and bang things went wrong. You need to install the previous version of kdelibs. The command is on the forums somewhere, thats where i found it. But Im too tired to look for it now.

---

### Post by ow50 on 2005-04-27
I don't use KDE, so I don't know if "kdelibs are messed up at the moment", but as a general note:

The "trying to overwrite... which is also in package..." can usually be solved by installing the deb package with --force-overwrite.

So you'd do:
cd /var/cache/apt/archives
sudo dpkg -i --force-overwrite packagename.deb

I'm not sure if it's always wise to force overwriting, but in your case it seems to just an icon file that will be overwritten, which shouldn't be dangerous.

For more info:
dpkg --force-help

---

### Post by dave9191 on 2005-04-28
Ok, try this 

sudo apt-get install kdelibs=4:3.4.0-0ubuntu3 kdelibs-data=4:3.4.0-0ubuntu3

And this is the thread I mentioned 

[http://www.ubuntuforums.org/showthread.php?t=28678&highlight=kdelibs](http://www.ubuntuforums.org/showthread.php?t=28678&highlight=kdelibs)

Dave

---

### Post by -TayloR- on 2005-04-28
Ok thanks for the info people, ill give it a try tonight and will keep you posted on how it goes..

---

### Post by zolookas on 2005-04-28
[QUOTE=fdoving] ```
'sudo dpkg --force-overwrite -i /var/cache/apt/archives/kdelibs-data_4%3a3.4.0-0ubuntu3.1_all.deb'
```

That should do it.


- Frode[/QUOTE] Try this after that right click on taskbar select add to panel and add taskbar, K button, system tray, etc.

---

### Post by epb613 on 2005-04-28
zolookas, I just tried your way and it worked fine - it didn't even destroy my taskbar! Can you just explain though what exactly the problem was and how your fix solved it. Thanks.

Edit: Err.. nope. After restarting KDE, I lost my taskbar et all.

---

### Post by Ruediger on 2005-04-28
I had this problem too and now got it fixed. Is it safe to do an apt-get upgrade now?

---

