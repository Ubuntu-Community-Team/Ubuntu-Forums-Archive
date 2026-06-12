---
title: "cant make new items in main menu"
date: 2013-11-15
forum: Desktop Environments
---

### Post by payam30 on 2013-11-15
hi, i just installed xubuntu 13.10  however it was a real disappointement. the  sound icon doesnt wor
k but after searching on google i finally found the trick to fix it. however i have a trouble with the main menu. i tried to make a new item but had some problems :
impossible to choose a custom icon 
doesnt make the item anyway.


anybody having same problem?

---

### Post by Bucky Ball on 2013-11-15
If you right click on the sound icon>Properties, there is a drop down list and you can assign it to control whichever sound device you wish. Tried that?

---

### Post by payam30 on 2013-11-15
> **Bucky Ball said:**
> If you right click on the sound icon>Properties, there is a drop down list and you can assign it to control whichever sound device you wish. Tried that?

Hi Bucky, As I mentioned in my first post I solved the problem with sound. The main issue is making a new item in Main menu which doesnt seem to be possible.

---

### Post by Bucky Ball on 2013-11-15
Please explain in more detail what you are doing to create the item in the main menu and any errors or other actions you're getting.

When you say 'main menu' I presume you mean the Apps menu ...

---

### Post by payam30 on 2013-11-15
Hi again Bucky,
It's in xubuntu 13.10

Now I'm in xubuntu 13.04 so I suppose it should be in the same way in the 13.10

Setting Manager > Main Menu > New Menu      Not possible to choose a icon and submit the changes , No error nothing happens
Setting > Main Menu > new Item  Same thing as above!

---

### Post by Bucky Ball on 2013-11-15
Hmm. I just tried it (I am using lxde menu editor in xfce4 but virtually the same) and no problem. Thinking ...

What group have you got marked in the left column when you are trying this? Perhaps some groups don't allow you to add a new menu or item, but it seems unlikely. Also, I don't have 'new menu', just new item.

An anomaly.

---

### Post by payam30 on 2013-11-15
No, Im totally positive im doing right. I have done this since 12.04 and it always worked. I dunno why

---

### Post by cristiantm2 on 2013-11-19
I´m having just the same problem on a default Xubuntu instalation as a VMWare Workstation 10 guest... I can create separators (?!?) but not new itens.

---

### Post by The Cog on 2013-11-19
I confirm the same problem here too. Xubuntu 13.10. Can't find a solution in google.

I checked with ps - it's definitely alacarte that's running to edit the menus.
Bucky Ball: what's the name of the Lubuntu menu editor?

---

### Post by garyzw on 2013-11-19
I found the work around to the problem of making new items.

Right Click on desktop and then Create Launcher

This will create the new launcher on the desktop from there move it to your /home/user/.local/share/applications/ folder.

It does not create the Categories for the launcher but just open the launcher with mousepad and add the  Categories=blank; to the bottom. Where blank is specify Category

---

### Post by Frogs Hair on 2013-11-19
The new menu option in the main menu hasn't worked since Gnome 3 AFAIK and this includes gnome panel sessions as well . It's also not possible to hide items in dash from the main menu by removing the check next to the application.

---

### Post by garyzw on 2013-11-19
> **Frogs Hair said:**
> The new menu option in the main menu hasn't worked since Gnome 3 AFAIK and this includes gnome panel sessions as well . It's also not possible to hide items in dash from the main menu by removing the check next to the application.

We are talking about xubuntu using the xfce desktop not ubuntu

---

### Post by Frogs Hair on 2013-11-19
Excuse me I missed The X :oops: ,   I have XFCE installed and will check back when I log-in.

Edit: The feature doesn't work in XFCE 4.12 .

---

### Post by garyzw on 2013-11-19
> **Frogs Hair said:**
> Excuse me I missed The X :oops: ,   I have XFCE installed and will check back when I log-in.

Edit: The feature doesn't work in XFCE 4.12 .

How is XFCE 4.12 installed mine says XFCE 4.10

---

### Post by Frogs Hair on 2013-11-19
I have been using the ppa which is use at your own risk. With the exception of a glitch regarding the wallpaper folder location in the new desktop settings GUI I have had no problems.  [https://launchpad.net/~xubuntu-dev/+archive/xfce-4.12](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.12)

---

### Post by garyzw on 2013-11-19
I have never figured how to add PPA's from Launch pad. how would i go about that in 13.10?

---

### Post by Frogs Hair on 2013-11-19
[http://www.webupd8.org/2013/10/xfwm4-4110-released-with-sync-to-vblank.html](http://www.webupd8.org/2013/10/xfwm4-4110-released-with-sync-to-vblank.html)

---

### Post by Bucky Ball on 2013-11-19
> **The Cog said:**
> 
Bucky Ball: what's the name of the Lubuntu menu editor?

'Lxde Main Menu Editor' = 'lxmed' from a terminal. Actually a little odd because I am using a minimal install with xfce4 as the DE and I don't remember installing lxmed manually ... maybe I did. *shrugs*

---

### Post by The Cog on 2013-11-20
Making a little progress. 
The menu editor does indeed create new entries. They are all in ~/.local/share/applications/alacarte-made*.desktop.
But it doesn't put a category in the file, so they all appear in the "Other" folder. You can manually edit the resulting file (and rename it) to add the "Categories=" line to put it where you want.

---

### Post by vasa1 on 2013-11-20
> **Bucky Ball said:**
> 'Lxde Main Menu Editor' = 'lxmed' from a terminal. Actually a little odd because I am using a minimal install with xfce4 as the DE and I don't remember installing lxmed manually ... maybe I did. *shrugs*
And Java as well? That's one reason I avoid lxmed.

---

### Post by The Cog on 2013-11-20
Yes - it's ugly, but it works a treat. 
Working but ugly is far better than pretty but useless.

---

### Post by vasa1 on 2013-11-20
> **The Cog said:**
> Yes - it's ugly, but it works a treat. 
Working but ugly is far better than pretty but useless.
It makes sense if Java is used for other things as well but installing Java just to edit menus? I wonder what happened to Menu Libre. That worked pretty well without needing Java.

---

### Post by Bucky Ball on 2013-11-20
Java? Huh? So you're saying lxmed uses Java? I wouldn't know. Like I say, don't even remember installing it.

---

### Post by vasa1 on 2013-11-20
> **Bucky Ball said:**
> Java? Huh? So you're saying lxmed uses Java? I wouldn't know. Like I say, don't even remember installing it.

That's what it says here:
> 
How to install lxmed?

Make sure you have java installed. Then follow these steps:

    To install lxmed, first download a .tar.gz file.
    Unpack archive in your home or desktop folder.
    In terminal, enter the lxmed folder and type chmod +x install.sh to make install script executable.
    Install lxmed by typing sudo ./install.sh
    Go to main menu -> Preferences -> Main Menu Editor

Source: [http://lxmed.sourceforge.net/help.html](http://lxmed.sourceforge.net/help.html)

Since I don't need Java and manage most of my apps with keyboard shortcuts, I'm not too particular about menus.

---

### Post by Bucky Ball on 2013-11-20
> **vasa1 said:**
> 

Since I don't need Java and manage most of my apps with keyboard shortcuts, I'm not too particular about menus.

I only use Java for Libreoffice functions and use shortcut keys for everything. Blank desktop, no 'clickable' icons for anything. I really don't remember doing any of that to install, or even installing lxmed. I've never even used it or been aware it was there until looking into finding a fix for this thread. Truly weird ... :-k

---

### Post by The Cog on 2013-11-20
> I wonder what happened to Menu Libre.
Hmm. I had to google for that one.  It wasn't easy to install. These commands did it:
```
sudo apt-get install gir1.2-gtksource-3.0  libgtksourceview-3.0-1 libgtksourceview-3.0-common python-distutils-extra
tar xzf menulibre_13.0.4.17.tar.gz
cd trunk
sudo python setup.py install
```

Nice. It seems to work pretty well.
I cannot for the live of me make it appear in both the settings "control panel" and the pull-down menu though. Is there some trick I'm missing?

---

### Post by vasa1 on 2013-11-20
> **The Cog said:**
> Hmm. I had to google for that one.  It wasn't easy to install. These commands did it:
```
sudo apt-get install gir1.2-gtksource-3.0  libgtksourceview-3.0-1 libgtksourceview-3.0-common python-distutils-extra
tar xzf menulibre_13.0.4.17.tar.gz
cd trunk
sudo python setup.py install
```

Nice. It seems to work pretty well.
I cannot for the live of me make it appear in both the settings "control panel" and the pull-down menu though. Is there some trick I'm missing?

Does this work on 13.10? I looked at the Launchpad page and didn't see mention of it being available for 13.10 :(

---

### Post by vasa1 on 2013-11-20
@The Cog, if you don't mind could you give more details on how you installed Menu Libre in a new thread? I don't get the *cd trunk* part and why you're using *sudo*.

---

### Post by The Cog on 2013-11-20
Barely worth a new thread. 
I forgot, you also need to install python-distutils-extra package. <Slaps head>
menulibre_13.04.17.tar.gz (from sourceforge) un-tars and creates a folder called trunk. All the stuff is in that folder.
I cd into that folder and run the install.py script in there. 
The install script tries to put things in /opt, /usr/bin and so on, so you need sudo.

I got an error while running install, 
```
Writing /usr/local/lib/python2.7/dist-packages/menulibre-13.04.17.egg-info
("ERROR: Can't rename", '/usr/local/share/applications/menulibre.desktop', ':', OSError(17, 'File exists'))
```
but menulibre did seem to work afterwards. It shows up in the settings manager control panel or can be run from command line.

P.S. While editing my install commands, I accidentally edited your quote of my commands instead. Doh! Hope you don't mind. They match again now.

---

### Post by payam30 on 2013-11-27
Anyone that fixed the problem? I still cannt make categories and items in main menu! 
Please don't make any offtopics. This is about Xfce and not Lxde and Java! 
thanks

---

### Post by vasa1 on 2013-12-01
> **payam30 said:**
> Anyone that fixed the problem? I still cannt make categories and items in main menu! 
Please don't make any offtopics. This is about Xfce and not Lxde and Java! 
thanks
To make an entry appear in the "main menu", try adding **X-Xfce-Toplevel;** to the **Categories** line in the relevant .desktop file. This works when I use the Xfce session at login time.
The attached image shows Geany in the "main menu" after modifying *~/.local/share/applications/geany.desktop* to look like this:
```
[Desktop Entry]
Type=Application
Version=1.0
Name=Geany
GenericName=Integrated Development Environment
Comment=A fast and lightweight IDE using GTK2
Exec=geany %F
Icon=geany
Terminal=false
Categories=Application;Utility;TextEditor;GTK;**X-Xfce-Toplevel;**
MimeType=text/plain;text/x-chdr;text/x-csrc;text/x-c++hdr;text/x-c++src;text/x-java;text/x-dsrc;text/x-pascal;text/x-perl;text/x-python;application/x-php;application/x-httpd-php3;application/x-httpd-php4;application/x-httpd-php5;application/xml;text/html;text/css;text/x-sql;text/x-diff;
StartupNotify=true

```

I haven't looked at creating new "Categories" as yet.

---

