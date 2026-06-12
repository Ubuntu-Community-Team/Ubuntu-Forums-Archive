---
title: "Beryl not working with xpress 200m screen garbled after startup"
date: 2007-07-15
forum: Desktop Effects &amp; Customization
---

### Post by lninjp on 2007-07-15
Look i have tried everything under the sun  I am using a toshiba m115 laptop with celeron m processor and 
ati radeon 200m Im also running kubuntu/ubuntu fiesty i just got finished wiping my hard drive so i can start from scratch ive tried all the tutorials but there not fitting my situation. I was able to bring up the splash screen and all is good intill i use my mouse and then everything scrambles what am i doing wrong if anyone could spare some time to help i would greatly appreciate it

---

### Post by edwin.e.johnson on 2007-07-16
ok look i got mine to work as of now i have beryl and compiz fusion... i suggest you use compiz fusion it looks alot better now and it seems to be getting updated everyday... it has everything beryl does and more..

i suggest if you do compiz after the install go to synaptic and search for compiz fusion...  then select the unsupported plugins for installation they got some cool stuff...

=====================with both compiz and beryl on 200m cards you will need the XGL session. so no matter what install it.=========================

hope this helps..

post your outcome





ATI Xpress 200M+ XGL + Beryl in Feisty


After installing Feisty, make sure your system is completely updated.

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

First step is getting your drivers set up. To do this use the Restricted Driver Manager.

```
System >> Administration >> Restricted Drivers Manager
```

and enable your ATI driver.
Reboot the computer. There should be an icon in the notification area telling you that you have restricted modules loaded. 


Now we need to install XGL.


```
sudo apt-get install xserver-xgl

```
the package in the Ubuntu repo works.

XGL won't load on its own so we need to write a few scripts to have it start.

```

sudo gedit /usr/local/bin/startxgl.sh
```

put this in your startxgl.sh file



```
#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
exec dbus-launch --exit-with-session gnome-session
```

now save and make the script executable


```
sudo chmod a+x /usr/local/bin/startxgl.sh
```

Now we need to create a way to login and launch that


```
sudo gedit /usr/share/xsessions/xgl.desktop
```

put this test into that file
```

[Desktop Entry]
Encoding=UTF-8
Name=GNOME with XGL
Comment=
Exec=/usr/local/bin/startxgl.sh
Icon=
Type=Application
```

now make that script executable

```

sudo chmod a+x /usr/share/xsessions/xgl.desktop
```

Now test your login. Logout, click sessions and chose GNOME with XGL




==================ok now this is for beryl=================




System >> Administration >> Software sources

now disable the universe repo and reload.
Now we need to add the beryl repo.

```

wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -

```

Now add this source to your Software sources via the Third party tab

```

deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) feisty main
```

reload sources and it's time to install!


```
sudo apt-get install beryl emerald-themes
```

Once that's finished installing you can launch beryl with

```
beryl-manager
```

to add to start-up go to 

```
system>preferences>sessions
```

add as name and as command=       ```
beryl-manager
```






=======================COMPIZ FUSION=====================





Open a terminal


```
sudo apt-get remove compiz-core desktop-effects
```


Leave the terminal open and go to System -> ```
Administration -> Software Sources
```, click on the second tab ```
(Third-Party Software)
```, then click on the "Add" button and paste the following code:


```

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

```



Don't close the Software Sources window yet!

In the terminal window, type:


```

wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg)
```



```

sudo apt-key add DD800CD9.gpg
```


Now click the "Close" button on the Software Sources window and you will be asked if you want to reload the information about available software, so click the "Reload" button and wait for the window to disappear.

Copy/Paste the following lines in the terminal window:

```

sudo apt-get update
```



```
sudo apt-get install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
```


Now, if everything was correctly installed and you didn't encounter errors, press ALT+F2 and type:

```

compiz --replace
```

to load at start up do same as the beryl above but it seems to load slow so id try the howto under this line.


-------------------------------------------------------------------------------------------------------------------------



make compiz fusion load fast at start up..


So you can just open your home directory with nautilus, right click anywhere in the window, select create folder and name it "bin".

    * open a terminal ```
'Applications>Accessories>Terminal'
```
    * in the terminal type



```
gedit ~/bin/startcompiz
```

    * In the text editor window paste



```
#/bin/bash
 sleep 10
compiz --replace
```

    * Save and close the file, you should now have a file named startcompiz in /home/<username>/bin
    * To make the script executable type the following;

```

sudo chmod +x ~/bin/startcompiz
```

    * Or you can open /home/<username>/bin in Nautilus, right click on 'startcompiz', select 'Properties', in the window which opens select the 'Permissions' tab, check the box which says 'Allow executing file as a program'
    * Now go to the System menu, select System>Preferences>Sessions
    * Select the 'Startup Programs' tab
    * click the 'New' button
    * type in 'Start Compiz' for the name (or whatever you like)
    * then browse to your /home/<username>/bin/startcompiz script
    * next time you login compiz should start shortly after everything else has started

---

