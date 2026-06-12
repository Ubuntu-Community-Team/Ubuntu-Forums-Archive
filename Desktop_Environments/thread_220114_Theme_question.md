---
title: "Theme question"
date: 2006-07-21
forum: Desktop Environments
---

### Post by Cable on 2006-07-21
I just installed [this]("http://www.gnome-look.org/content/show.php?content=40670") theme.  It says that it includes the GTK 1 theme as well as the GTK 2 theme.  However, some applications don't have the theme applied (Update Manager, Synaptic).  Why is that?

---

### Post by Jucato on 2006-07-21
The themes you installed are installed only for your user. Those apps you mentioned are apps that are run only by the administrator/root. So the theme change didn't affect them. As a principle, only the user that installed/changed the theme gets affected by the change.

I personally think it might be a good idea to keep those "administrative" apps in a different theme from your regular apps. This will provide you a sort of visual reminder that you are running those programs with administrative privileges and that they will have system-wide impact. 

If you want/need to change those apps' appearance, I think you need to run the gnome-theme-manager as root. Press Alt+F2, and type in
```
gksudo gnome-theme-manager
```
and change the theme. AFAIK this will affect only those apps that run as root. I'm not 100% sure, though.

---

### Post by adam.tropics on 2006-07-21
because they are run as sudo, to fix, in a terminal type
sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts

---

### Post by Saibot on 2006-07-21
SWEET!  Thanks a million.  I wondered why Synaptic looked like poo while the rest of my windows are themed.  My Ubuntu install just gets better every day.

---

### Post by Cable on 2006-07-21
Well, I did the symbolic links.  However, it's not working.  Synaptic and such still use the default GNOME theme.  It seems that there's some sort of problem.  When I type...
```

gksudo gnome-theme-manager

``` 
a warning pops up that says the following...

"Unable to start the settings manager 'gnome-settings-daemon'.  Without the GNOME settings manager running, some preferences may not take effect.  This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager."

If I go to /root, it shows that there are .themes and .icons links and it says "link (broken)" under the "Type" column for both.  

Also, as a bit of a side question...how does one remove symbolic links?

---

### Post by Skia_42 on 2006-07-21
very usefull, thanks alot adam.tropics

---

### Post by adam.tropics on 2006-07-21
> **Cable said:**
> Well, I did the symbolic links.  However, it's not working.  Synaptic and such still use the default GNOME theme.  It seems that there's some sort of problem.  When I type...


You did remember to replace <insert your username> with your username?

---

### Post by Cable on 2006-07-22
> **adam.tropics said:**
> You did remember to replace <insert your username> with your username?

Yep, I did.  :-P

---

### Post by jannol on 2006-07-22
You need to remove any current themes and such in the root folder or it wont make the symlinks so do this first

sudo rm -rf /root/.themes
sudo rm -rf /root/.fonts
sudo rm -rf /root/.fonts

and then the syumlinks with

sudo ln -s /home/<insert your username here>/.themes /root/.themes
sudo ln -s /home/<insert your username here>/.icons /root/.icons
sudo ln -s /home/<insert your username here>/.fonts /root/.fonts

and it should work

or you can ignore the removal and just force the symlinks to be created with -f

sudo ln -fs /home/<insert your username here>/.themes /root/.themes
 sudo ln -fs /home/<insert your username here>/.icons /root/.icons
 sudo ln -fs /home/<insert your username here>/.fonts /root/.fonts

---

### Post by Cable on 2006-07-22
Fixed the problem.  Thanks a lot!

---

