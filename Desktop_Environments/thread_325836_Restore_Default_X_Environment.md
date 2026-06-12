---
title: "Restore Default X Environment"
date: 2006-12-26
forum: Desktop Environments
---

### Post by Tookelso on 2006-12-26
Hello,

I was interested in installing Compiz on my Dapper machine, which has an older Nvidia card in it.  However, I've encountered problems, and really just want to restore to the original Dapper window manager / X window setup.

I managed to restore the Metacity window manager.  However, now my problem is that text in my windows will often vanish.  If I drag a window off the screen, then drag it back, the text will show up again.

Can anyone help me restore my settings?  I suspect there are some files in my .gnome or .gnome2 directories that were modified when I tried to install Compiz.  I used this web page [http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-dapper](http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-dapper) as a guide, but I backed out before I modified my Xorg.conf file, because frankly, it just got too scary.

Here are details of the commands I ran.  If anyone can help me restore the default Dapper settings I would greatly appreciate it.

I put this entry in my sources.list file:
    ```
deb http://gandalfn.club.fr/ubuntu dapper .
```

Then I ran
   ```
 sudo apt-get update
    sudo apt-get dist-upgrade

    sudo apt-get install linux-dri-modules-common linux-dri-modules-`uname -r`
    sudo apt-get install xserver-xorg-air-core
```

Finally, I ran this install, and after I ran it, the Update Manager (or whatever it's called)
suggested that I reboot.

```
sudo apt-get install gnome-compiz-manager compiz-freedesktop compiz-freedesktop-gnome

```

---

### Post by Tookelso on 2006-12-26
I found *perhaps* what the problem was.

I used Synaptic Package manager to uninstall the xorg-air-core drivers, which then made my system crash.  Yay!

I went to the /etc/X11 directory, and found that X was pointing to /usr/bin/Xorg.  
Then, I went to /usr/bin/Xorg, and found that Xorg was a link that pointed to /etc/alternatives/Xorg.  Right next to the Xorg link, I found a file called "Xorg.official". 

I *assume* that /etc/alternatives/Xorg was created when I tried installing Compiz. 
I took a wild guess and made a copy of the Xorg link, then copied Xorg.official over the Xorg link.  I rebooted, and this seems to have fixed the problem with the text disappearing on my screens.

I will update this thread if I encounter any problems.  Please post a reply I did something really stupid by changing the Xorg link.

Thanks,
--Took

---

