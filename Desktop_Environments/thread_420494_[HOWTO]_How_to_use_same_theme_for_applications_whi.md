---
title: "[HOWTO] How to use same theme for applications which is runned as root"
date: 2007-04-23
forum: Desktop Environments
---

### Post by avb on 2007-04-23
When i'm doing manual network configuration i always see network-admin is using default gtk theme. Not the one chosen by me. I write a simple script which will make config for root user to use 
your selected gtk theme.

here it is.
```

#!/bin/sh
rootcfg="/root/.gtkrc-2.0"
theme=`gconftool -g '/desktop/gnome/interface/gtk_theme'`
echo "Your theme is: $theme"
for theme_dir in ${HOME}/.themes/$theme /usr/share/themes/$theme;do
   if [ -d $theme_dir/ ];then
      theme_in=${theme_dir}
   fi 
done
echo "Theme location is: ${theme_in}"
echo "----"
echo "Now you need to enter your password to update root theme"
sudo sh -c "echo include \'\"${theme_in}/gtk-2.0/gtkrc\"\' > $rootcfg"

```

How to use it:
1. save this script with gedit to your home and name it change_theme.sh.
2. open gnome-terminal
3. run sh ~/change_theme.sh
4. When you will be prompted for a password enter your password.
5. Try to load network-admin and see that it use your selected theme.

Hope it will be useful for community.

---

### Post by mcduck on 2007-04-24
There's easier way:

```
sudo ln -s /home/YOURUSERNAME/.themes /root/.themes
sudo ln -s /home/YOURUSERNAME/.icons /root/.icons
```

..and now root apps will always have the same theme you are using ;)

---

### Post by avb on 2007-04-24
> **mcduck said:**
> There's easier way:

```
sudo ln -s /home/YOURUSERNAME/.themes /root/.themes
sudo ln -s /home/YOURUSERNAME/.icons /root/.icons
```

..and now root apps will always have the same theme you are using ;)


;) ~/.themes and ~/.icons is just a directories where custom themes is located. 
To use one of them you need to use gtkrc file.  So your code is not working.

---

### Post by mcduck on 2007-04-24
> **avb said:**
> ;) ~/.themes and ~/.icons is just a directories where custom themes is located. 
To use one of them you need to use gtkrc file.  So your code is not working.
Well, it sure works on every computer where I have installed Ubuntu. Did you even try it?

---

### Post by mh114 on 2007-05-01
> **mcduck said:**
> Well, it sure works on every computer where I have installed Ubuntu. Did you even try it?
Worked for me as well, perfect! :) I was having the same problem with Synaptic etc. being in different theme. Thanks!

---

### Post by ChiaJesus on 2007-05-01
I prefer to keep them somewhat different so that I know exactly which windows are being run as root. For new users, I recommend this method to reduce the risk of borking their system.

---

### Post by LuisGMarine on 2007-05-01
I didn't even know that this was possible!  This just proves how customizable Linux trully is!  Great posts, I tried the easy one with the symbolic link ( I believe that is what it is called ), great job!

-LuisGMarine

---

