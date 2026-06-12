---
title: "HOWTO: Make Desktiop Effects work with ATI graphic cards"
date: 2008-02-17
forum: Desktop Effects &amp; Customization
---

### Post by kool_kat_os on 2008-02-17
I found out how to make Extra Desktop Effects work with ATI Graphics Cards....I have an ATI Mobility Radeon X700 and it worked with that.

So here it is:

go to terminal and type in:

```
sudo apt-get install xserver-xgl
```
(that make the effects work)
Then restart your system.

Then after it has restarted go to terminal and type in:

```
sudo apt-get install compizconfig-settings-manager
```
(that lets you add extra effects.)

I dont know if someone else already posted something like this but there it is. Quite Simple.

Hope it works...it did for me:)

---

### Post by K.Mandla on 2008-02-19
Moved to Desktop Effects and Customization.

---

### Post by vanadium on 2008-02-19
It indeed works, but you will find that 3D applications such as Google Earth or Celestia or 3D games will not anymore work. Thus, you will need to decide whether you want compiz or the other applications.

---

### Post by Kivech on 2008-02-19
I was about to post a thread like this myself. Good one! ;)

---

### Post by erfahren on 2008-02-19
don't you still need to make a startup entry for Compiz as well - like with the command "compiz --replace"?

anyway, XGL can be disabled by simply making an empty file named "disable" in ~/.config/xserver-xgl/disable - (".conf") is a hidden folder in the /home/<username> directorory - press Ctrl+H to view).

the file can be be created just with the command:
```

touch $HOME/.config/xserver-xgl/disable

```

so if you want to use a program that doesn't work well with Compiz you can disable the Compiz entry from the Startup Session, disable XGL and restart X (log out and log back in).

I made a little script to check whether or not that "disable" file existed and create or remove it (sometimes I'd forget - lol). it has a message saying what it did

- to use it just create a folder named "bin" in your /home/<username> directory (more info on that [here](http://www.linuxcommand.org/wss0010.php#path) ) 

make a new file there
```

gedit ~/bin/xgl_enable_disable

```
and put this in it
```

#!/bin/bash

XGL_DISABLE=$HOME/.config/xserver-xgl/disable

if [ -f "$XGL_DISABLE" ]
then
rm $XGL_DISABLE 
dialog --title "XGL Enable/Disable" --msgbox "XGL Enabled. Hit any key to continue." 6 50
else
touch $XGL_DISABLE 
dialog --title "XGL Enable/Disable" --msgbox "XGL Disabled. Hit any key to continue." 6 50 
fi

```
save the file and make it execuatble
```

chmod +x ~/bin/xgl_enable_disable

```
(or just right-click on the file and under the "Permissions" tab check the box to make it executable)

note: by default in Ubuntu the path to ~/bin is already set in the ~/.profile file - but I think you need to log out/in for bash to recognize the new ~/bin directory

anyway, then a launcher can be created [in the menu](http://ubuntuforums.org/showthread.php?t=533265) for that script - the command is just "xgl_enable_disable"

EDIT: oh - with that script the directory "~/config/xserver-xgl" already needs to exist - I can't remember if it did or not - so just create it if it doesn't

---

### Post by mimada on 2008-02-19
I just created a user account with Compiz enabled and one where it is disabled. That way, if an application breaks, I can just switch to the Compiz disabled account. Don't forget to put the two accounts in the same groups so you can access your data when you switch.

---

### Post by kool_kat_os on 2008-02-19
> **Kivech said:**
> I was about to post a thread like this myself. Good one! ;)

thanks:)

---

### Post by kool_kat_os on 2008-02-19
> **erfahren said:**
> don't you still need to make a startup entry for Compiz as well - like with the command "compiz --replace"?

anyway, XGL can be disabled by simply making an empty file named "disable" in ~/.config/xserver-xgl/disable - (".conf") is a hidden folder in the /home/<username> directorory - press Ctrl+H to view).

the file can be be created just with the command:
```

touch $HOME/.config/xserver-xgl/disable

```

so if you want to use a program that doesn't work well with Compiz you can disable the Compiz entry from the Startup Session, disable XGL and restart X (log out and log back in).

I made a little script to check whether or not that "disable" file existed and create or remove it (sometimes I'd forget - lol). it has a message saying what it did

- to use it just create a folder named "bin" in your /home/<username> directory (more info on that [here](http://www.linuxcommand.org/wss0010.php#path) ) 

make a new file there
```

gedit ~/bin/xgl_enable_disable

```
and put this in it
```

#!/bin/bash

XGL_DISABLE=$HOME/.config/xserver-xgl/disable

if [ -f "$XGL_DISABLE" ]
then
rm $XGL_DISABLE 
dialog --title "XGL Enable/Disable" --msgbox "XGL Enabled. Hit any key to continue." 6 50
else
touch $XGL_DISABLE 
dialog --title "XGL Enable/Disable" --msgbox "XGL Disabled. Hit any key to continue." 6 50 
fi

```
save the file and make it execuatble
```

chmod +x ~/bin/xgl_enable_disable

```
(or just right-click on the file and under the "Permissions" tab check the box to make it executable)

note: by default in Ubuntu the path to ~/bin is already set in the ~/.profile file - but I think you need to log out/in for bash to recognize the new ~/bin directory

anyway, then a launcher can be created [in the menu](http://ubuntuforums.org/showthread.php?t=533265) for that script - the command is just "xgl_enable_disable"

EDIT: oh - with that script the directory "~/config/xserver-xgl" already needs to exist - I can't remember if it did or not - so just create it if it doesn't
What do you mean by "startup entry:confused:"???

---

### Post by erfahren on 2008-02-20
> **kool_kat_os said:**
> What do you mean by "startup entry:confused:"???I thought that you still had to put a startup entry for Compiz in System > Preferences > Sessions 

maybe that doesn't need done in Gutsy. I stopped using Compiz actually, and it's been awhile since I've done all that, so I may be wrong.

---

### Post by kool_kat_os on 2008-02-21
> **erfahren said:**
> I thought that you still had to put a startup entry for Compiz in System > Preferences > Sessions 

maybe that doesn't need done in Gutsy. I stopped using Compiz actually, and it's been awhile since I've done all that, so I may be wrong.

i didnt and it works...:)

---

