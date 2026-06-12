---
title: "how to upgrade to new version of firefox"
date: 2010-10-08
forum: Desktop Environments
---

### Post by tapas_mishra on 2010-10-08
How can I upgrade to new version of firefox on 64 bit Lucid.

---

### Post by PRC09 on 2010-10-09
If you are referring to Firefox 4 Beta........

[http://www.liberiangeek.net/2010/07/install-firefox-4-0-beta-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/07/install-firefox-4-0-beta-ubuntu-10-04-lucid-lynx/)

---

### Post by tapas_mishra on 2010-10-09
Well thanks I just needed to upgrade to new version of firefox.
Your link give useful information.
Here is a script I got to fix missing gpg key errors
```

for i in `sudo aptitude update 2>&1 | grep NO_PUBKEY | awk  '{print $NF;}'`; do sudo apt-key adv --keyserver keyserver.ubuntu.com  --recv-keys $i; done
```
The source for above script is a comment on 
[http://popey.com/blog/2009/06/05/Easy_Script_To_Get_And_Install_PPA_GPG_Keys/](http://popey.com/blog/2009/06/05/Easy_Script_To_Get_And_Install_PPA_GPG_Keys/)

---

### Post by lovinglinux on 2010-10-09
See the [[COLOR="Sienna"]**Installing Other Versions**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html) tutorial.

For Firefox 4 see [http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html](http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html)

---

### Post by tapas_mishra on 2010-10-09
> **lovinglinux said:**
> See the [[COLOR=Sienna]**Installing Other Versions**[/COLOR]]("http://firefox-tutorials.blogspot.com/2010/05/installing-other-versions.html") tutorial.

For Firefox 4 see [http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html](http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html)
Thanks for your link .
I would better be off with Chrome.

---

### Post by lovinglinux on 2010-10-09
> **tapas_mishra said:**
> Thanks for your link but I do not have the  patience to suffer all that ls,cp,rm non sense.
I would better be off with Chrome.

Then just use [FoxTester]("https://addons.mozilla.org/en-US/firefox/addon/141505/"). [See demo]("http://foxtester-extension.blogspot.com/").

---

