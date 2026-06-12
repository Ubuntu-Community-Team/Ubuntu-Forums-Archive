---
title: "Dust theme  not showing on some windows"
date: 2008-12-05
forum: General Help
---

### Post by nicholasbgr on 2008-12-05
I was using dust for quite a long time and it was working perfectly until today. I had a problem with some of my partitions, so I had to reinstall everything. Now that I have my notebook all set up again, I just installed the Dust theme, but its not working on some windows like synaptic. Here's a screenshot:

[http://img156.imageshack.us/img156/7254/screensdustjg5.png](http://img156.imageshack.us/img156/7254/screensdustjg5.png)

How do I fix it?

---

### Post by nicholasbgr on 2008-12-05
Solved. I Installed the theme to /usr/share/themes. Working fine now.

---

### Post by hotani on 2008-12-09
I tried copying the extracted "Dust" directory to /usr/share/themes but I'm still getting generic synaptic.

---

### Post by binbash on 2008-12-09
you can also link .fonts .icons .themes to your /root

---

### Post by MarblePanther on 2008-12-09
To fix root appearance type these lines in a terminal:
cd /root
sudo ln -s ${HOME}/.themes

OR BETTER YET

To fix this, run these three commands in a terminal. They will cause your own theme, font, and icon preferences to always be used by the root user.

    sudo ln -s ~/.themes /root/.themes
    sudo ln -s ~/.icons /root/.icons
    sudo ln -s ~/.fonts /root/.fonts

---

### Post by hotani on 2008-12-09
Thanks for the comments. I realized just after posting that I only copied over "Dust" and not any of the extras. Since I'm using "Sand" it wasn't working.

I did try the /root dir method to my machine at home but will have to test that later.

---

