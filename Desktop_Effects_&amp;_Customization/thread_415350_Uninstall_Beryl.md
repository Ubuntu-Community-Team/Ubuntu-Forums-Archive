---
title: "Uninstall Beryl?"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by Flaystus on 2007-04-20
How would I remove it? I Installed it via the command line. Kinda new to this still.

---

### Post by Kobalt on 2007-04-20
Fire up Synaptic package manager and search for any package having beryl in it's name as well as emerald, and remove it... 
Via command line it would be ```
sudo aptitude remove beryl emerald-themes
```

---

### Post by ubukool on 2007-04-20
if you're using Feisty, Beryl is in the repositories, so you can just use synaptic package manager, search for beryl and remove the files in the usual way

---

### Post by Flaystus on 2007-04-20
Thanks a million guys. I figured I'd give it a try since the fancy menu stuff built in wasn't working. Having the no title bars issue like many others.

Funny thing is I can see the far left and right of the title bar and where the buttons are suppose to be you can click but its like they are inviisble. I figure I'll remove it until there is a greater concensus on hwo to fix the problem.

---

### Post by 5735guy on 2008-01-11
Many thanks. :):):)

---

### Post by j800r on 2008-06-03
anyone know how to install and use Beryl in Hardy? I've only seen help and advice for Feisty and Gutsy.

---

### Post by Joeb454 on 2008-06-03
Beryl is discontinued, hence why there is no guides on how to use beryl in Hardy.

You should use Compiz-Fusion instead, which is installed by default. You can tweak the settings if you install the settings manager ```
sudo apt-get install compizconfig-settings-manager
```

---

