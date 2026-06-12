---
title: "Ubuntu 14 Composite issue"
date: 2014-04-20
forum: Desktop Environments
---

### Post by Bigpat on 2014-04-20
I have no idea what happened but after I upgraded to 14 my Docky has been acting up. For some reason I cannot enable metacity and it not even sowing up in the config Editor section. I'm I the only one having this issue. I even tried to install compiz and I still cannot enable composite even thought I have it checked and restarted everything. Has metacity been removed in Ubuntu 14?. I also check the installed applications and it says metacity is already installed. But it is not showing up anyware else. Can someone help me enable metacity if possible.

Thanks in advance

---

### Post by Bigpat on 2014-04-20
ok It sems that I was able to correct the issue by removeing gnome flashback. This upsets me greatly as I like the gnome classice feel and look. So to eveyone I say this. How do I get a work gnome classice look in ubuntu 14 along with Docy Composite to work.

---

### Post by grumblebum2 on 2014-04-20
What session do you login to.
Don't understand ... "But it is not showing up anyware else. Can someone help me enable metacity if possible."
Is compiz your window manager or metacity???

---

### Post by grumblebum2 on 2014-04-20
> **Bigpat said:**
> ok It sems that I was able to correct the issue by removeing gnome flashback. This upsets me greatly as I like the gnome classice feel and look. So to eveyone I say this. How do I get a work gnome classice look in ubuntu 14 along with Docy Composite to work.

Enable metacity compositing via terminal...
```
gsettings set org.gnome.metacity  compositing-manager true
```

There are 2 flashback sessions with different window managers.
[LIST]
[*]Flashback(Compiz)
[*]Flashback(Metacity)
[/LIST]

Compiz is a compositing window manager.
By default compositing in metacity is not enabled.

---

