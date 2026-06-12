---
title: "auto-start programs at boot"
date: 2005-05-24
forum: Desktop Environments
---

### Post by Zelut on 2005-05-24
I'm having trouble auto-starting some programs at boot.  If someone could give me some detailed instructions I'd really appreciate it.

There are a couple programs I'd like to run in the background.  These are the folding@home ([http://folding.stanford.edu](http://folding.stanford.edu)) project & the Seti@home ([http://setiweb.ssl.berkeley.edu/tech_news.php](http://setiweb.ssl.berkeley.edu/tech_news.php)) project.  I've been looking into the init.d/ but I don't want to break anything :)

Appreciate any help.  thanks.

---

### Post by pdk001 on 2005-05-24
system - preferences - sessions - add " programs you want " on the "startup programs"tab
e.g enter the "gaim" in the blank after putting "add" botton and re-boot ur machine

---

### Post by grexk on 2005-05-25
try making daemon place in the /etc/init.d/ folder then make a symbolic to diffirent runlevel /etc/rc#... or better read about making daemon....

---

