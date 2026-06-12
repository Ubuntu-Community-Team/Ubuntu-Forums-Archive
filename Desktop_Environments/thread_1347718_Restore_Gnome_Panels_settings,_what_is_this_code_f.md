---
title: "Restore Gnome Panels settings, what is this code for?"
date: 2009-12-06
forum: Desktop Environments
---

### Post by jcroot88 on 2009-12-06
Hello everyone!

I have an Acer Aspire One Netbook and few weeks ago I decided to remove Windows XP and install UBuntu Netbook Remix 9.10, everything seems to be working fast and easier with Ubuntu but yesterday I was playing with the gnome panels and everything was messed up. After searching this forum and google I found several suggestions in order to reset my gnome settings to their default.

**The first suggestion that I found was:**

[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

Which recommends to run this code from the terminal:

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

After running this code nothing changed, my problem was still there.

**The next guide that I found was:**

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

This guide worked really nice, it did the job, my panels are back to normal... but I was just wondering what was the first guide about? (the one with rm -rf .gnome .gnome2 .gconf .gconfd .metacity)? was is this code for? I am just afraid that this could messed up other settings...

---

### Post by VCoolio on 2009-12-06
The first one made you remove several hidden folders where gnome applications store their settings. If a problem has its cause in user settings, it's solved this way (though it is a rather harsh method). These folders should be recreated on your next login with default settings. But also for example gedit plugins are stored in ~/.gnome2/gedit, so if you had some, they are removed too. And nautilus scripts are in ~/.gnome2/nautilus-scripts. So the first method isn't really something to use often. No real harm done, I think.

---

### Post by jcroot88 on 2009-12-06
> **VCoolio said:**
> The first one made you remove several hidden folders where gnome applications store their settings. If a problem has its cause in user settings, it's solved this way (though it is a rather harsh method). These folders should be recreated on your next login with default settings. But also for example gedit plugins are stored in ~/.gnome2/gedit, so if you had some, they are removed too. And nautilus scripts are in ~/.gnome2/nautilus-scripts. So the first method isn't really something to use often. No real harm done, I think.

Thanks for your reply... so I should be fine then? I do not use gedit that often so I don't think I had download/installed any plugin for it, or the plugins comes with the Ubuntu installation? as I said before... the first method couldn't solve my problem, and I wasn't sure what it was, i was afraid that I messed up something in my system with the first method. What solved my problem was the second method.

---

### Post by VCoolio on 2009-12-06
Ok I guess you're good, except you're far too ignorant about gedit and its capabilities with plugins ;) I use it all the time. The default plugins are still there, somewhere in the system files; there are more to be installed with synaptic; only third party plugins you need to extract to the mentioned user folder. Check it out sometime. And never just delete folders because some obscure blogger said so.

---

### Post by jcroot88 on 2009-12-08
> **VCoolio said:**
> Ok I guess you're good, except you're far too ignorant about gedit and its capabilities with plugins ;) I use it all the time. The default plugins are still there, somewhere in the system files; there are more to be installed with synaptic; only third party plugins you need to extract to the mentioned user folder. Check it out sometime. And never just delete folders because some obscure blogger said so.

Hi! Thanks for your reply, I am new to Ubuntu Linux and I remember using Notepad ++ in Windows, now it looks like I will be using gedit instead of notepad... Yes, you are right, I think I am ignorant regarding this software, I should look more into it. Is there a way to re-install gedit or to check if the plugins are missing? sorry about my ignorance again...

---

### Post by VCoolio on 2009-12-08
If you didn't add plugins yourself then nothing is missing, but you can reinstall anything with "sudo apt-get --reinstall install anything". Some plugins come with gedit by default (edit > preferences > plugins; they are stored in /usr/share/gedit-2/plugins); some are combined in the package gedit-plugins and also the gedit-latex-plugin is available in the repositories. If you install those they will also go to the /usr folder. All those and several others can be found [here.]("http://live.gnome.org/action/recall/Gedit/Plugins") Only third party plugins go to ~/.gnome2/gedit/plugins. Choose what you need and you don't want an other programming / text / latex editor anymore.

---

