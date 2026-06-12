---
title: "Conky 1.10.8 does not start properly during autostart"
date: 2019-06-15
forum: Desktop Environments
---

### Post by &amp;wP*!) on 2019-06-15
When Conky started using Autostart feature of LXQt, it does not show the window.

I have defined conky in LXQt as an Autostart. I have logged out and logged in and conky window is not shown.

conky is defined as autostart in /usr/bin/lxqt-config-session. following file was created:
```
[Desktop Entry]
Version=1.0
Name=Conky
Exec=conky -d
Terminal=false
Type=Application
```

I see that conky was started during autoststart as daemon successfully. I have killed that process and then started **conky -d** manually in terminal  again and then Conky windows is shown.

There is something wrong with LXQt settings.

Is there anyone who has conky running on Lubuntu? If yes, how does the Conky.desktop file above look like on your side?

---

### Post by &amp;wP*!) on 2019-06-15
I have taken exactly the same conky.desktop file in the [Conky page in Arch Linux]("https://wiki.archlinux.org/index.php/conky"), also changed background=true in **.config/conky/conky.conf**. No success, i.e. autostart starts the process correctly (I can see in the process list), but the window is not drawn. If I kill the process and start in command line again, it works.

There is something wrong with the Autostart of Conky.

---

### Post by #&amp;thj^% on 2019-06-15
In Lubuntu, but I don't  use Lubuntu.(FTR)
I run mine with a 30 sec delay>>>sleep 30s<<<
Run the following commands in a terminal:
```

mkdir -p ~/.config/lxsession/Lubuntu/
touch ~/.config/lxsessions/Lubuntu/autostart
leafpad autostart
```

Add this line to the autostart file:
```

@conky
```
Once you have achieved your desired config, you then add multiple scripts also:
To set multiple Conky to run at startup, create a folder called .conky.
```

mkdir ~/.conky
```

Save your different Conky config files in there. You may want to name them .conkyrc_top, .conkyrc_bottom, etc. You should save all your Conky config files there. Next create a script that will execute all these Conky files. Something like the following:
```

 #!/bin/bash
conky -c ~/.conky/.conkyrc_top &
conky -c ~/.conky/.conkyrc_bottom
```

Note that all commands except the last must be appended with an ampersand (&) so that the script will not stop at the first command.
The "conky -c random_file" command simply tells conky to use random_file for configuration instead of the default ~/.conkyrc. Save this file as conky_start in ~/bin; if the folder does not already exist, create it. 
All this is found here: [https://help.ubuntu.com/community/SettingUpConky](https://help.ubuntu.com/community/SettingUpConky)

---

### Post by &amp;wP*!) on 2019-06-15
No, that doesn't work, either. With the guidance of the help you mentioned, It even cannot start the conky process, much worse.

It's because I have Lubuntu 19.04, which looks at **.config/autostart** (because I see that the process is started by autostart). The Help page of Ubuntu for Conky you mention belongs to very old versions of Lubuntu (**.config/lxsession/Lubuntu**). This is another proof that help pages of Ubuntu are not updated frequently...

For more about this, take a look at [https://askubuntu.com/questions/1108138/where-is-autostart-in-lubuntu-18-10](https://askubuntu.com/questions/1108138/where-is-autostart-in-lubuntu-18-10)

I have tried [https://unix.stackexchange.com/questions/458427/conky-auto-startup-in-fedora-28](https://unix.stackexchange.com/questions/458427/conky-auto-startup-in-fedora-28) , even a Japanese page (with Google translation) [http://www.fuukemn.biz/page82-lubuntu-1005pe.html](http://www.fuukemn.biz/page82-lubuntu-1005pe.html) . None of them work.

Anybody tried  conky with a recent Lubuntu where .config/autostart is used?

---

### Post by #&amp;thj^% on 2019-06-15
Well it dose work at least here anyway, maybe have a look at the conky.rc script your using.
And autostart on Lubuntu 19.04: [https://manual.lubuntu.me/3/3.2/3.2.13/session_settings.html](https://manual.lubuntu.me/3/3.2/3.2.13/session_settings.html)
You seem very frustrated, and this will not help you in gaining users to help here.
Good Luck though.
BTW: If needed Conky Manager is a little more straight forward, and has an option for AutoStart.
You can install it with a .run file from GitHub.
You will need to install "realpath" first:
```
sudo apt install realpath
```
**For Conky Manager For 64 bit:**
```

wget --no-check-certificate https://github.com/teejee2008/conky-manager/releases/download/v2.4/conky-manager-v2.4-amd64.run
chmod +x conky-manager-v2.4-amd64.run
sudo ./conky-manager-v2.4-amd64.run
```

**For 32 bit:**
```

wget --no-check-certificate https://github.com/teejee2008/conky-manager/releases/download/v2.4/conky-manager-v2.4-i386.run
chmod +x conky-manager-v2.4-i386.run
sudo ./conky-manager-v2.4-i386.run

```
I have also used the .deb with:
```
sudo apt install conky-all
sudo apt install realpath
wget https://github.com/teejee2008/conky-manager/releases/download/v2.4/conky-manager-v2.4-amd64.deb
sudo dpkg -i conky-manager-v2.4-amd64.deb
```
The pre-packaged software is found here: [https://github.com/teejee2008/conky-manager/releases](https://github.com/teejee2008/conky-manager/releases)

---

### Post by ajgreeny on 2019-06-15
At cold boot you really need to add an option to pause the actual start of conky (as shown in ***man conky***)
>        -p | --pause= SECONDS
              Time to pause/wait before actually starting Conky. as it will not start properly if the DE is not fully up and running.  I personally use a 20 second delay with command ***conky -p 20*** and that is fine for Xubuntu-18.04 but I have no real experience of Lubuntu with LXQt. However, it must use a command at some place in the startup of conky where you could add the necessary pause, such as that desktop file you show in your opening post.

---

### Post by &amp;wP*!) on 2019-06-17
> **ajgreeny said:**
> At cold boot you really need to add an option to pause the actual start of conky (as shown in ***man conky***)
 as it will not start properly if the DE is not fully up and running.  I personally use a 20 second delay with command ***conky -p 20*** and that is fine for Xubuntu-18.04 but I have no real experience of Lubuntu with LXQt. However, it must use a command at some place in the startup of conky where you could add the necessary pause, such as that desktop file you show in your opening post.

Thanks for this hint! At Lubuntu 19.04, conky 1.10.8 finally works with the option you mentioned above. I have given **conky -p 60** in Autostart. 

For documentation purposes: Someone who wants to run conky on LXQt (and at Lubuntu), copy-paste **/etc/conky/conky.conf** to **$HOME/.config/conky/conky.conf** (create the directory if there isn't any). And set following variables in this file:
```
alignment = 'top_right',
own_window_argb_visual = true,
own_window_transparent = true,
own_window_hints = 'undecorated,below,sticky,skip_taskbar,skip_pager',
double_buffer = true, -- works at Openbox stacking window manager. To be checked whether it is also working for compositing window manager. 

```
I am setting this SOLVED.

---

