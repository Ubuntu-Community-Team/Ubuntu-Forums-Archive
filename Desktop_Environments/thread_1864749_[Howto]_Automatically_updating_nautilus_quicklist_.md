---
title: "[Howto] Automatically updating nautilus quicklist in unity launcher"
date: 2011-10-19
forum: Desktop Environments
---

### Post by clemmy on 2011-10-19
Since Unity came out, several blogs have reported how to create quicklists for launcher icons. I like very much a quicklist containing my file manager bookmarks, to have quick access to the folder I use the most. Creating a nautilus icon with bookamrks quicklist is pretty easy, but editing a text file every time we would like to add a new bookmark to the quicklist, or remove an existing one.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=205028&stc=1&d=1319188243[/IMG]

I've created a small script to address this problem! :)
My script runs in background as a daemon: every minute it checks your nautilus bookmarks and updates the quicklist of an icon that you can place in your launcher. If you want it to update faster, or slower, you can easilly adjust this parameter.

**Current version is: 0.4** ([download]("http://ubuntuforums.org/attachment.php?attachmentid=205038&d=1319199624"))

Infos

**Installation:**
* Download archive
* Extract archive anywhere
* Double-click install.sh and choose "Run"

**Uninstallation:**
* Go to the folder where you had extracted the archive for installation
* Double-click uninstall.sh and choose "Run"


**Howto adjust change update rate:**
* Click the system icon in the top right corner of your desktop then click "Sturtup Applications"
* Select "Launcher Bookmarks" and click Edit
* The "Command" field will look like this:
```
bin/launcher-bookmarks.sh 60 &
```
* The numeric value is the update rate, in seconds (default is 60)



**ChangeLog:**
Version 0.4
* Fixed bug with bookmarks containing spaces
* Easier configuration of the update rate


Version 0.3
* automatic install/uninstall procedure
* automatic update of the quicklist every 60 seconds (parameter easily adjustable)
* new icon
* Update link removed since it is no more required


Version 0.2
* Added Update link to the quicklist
* Login / Logout no more required to update the quicklist


Version 0.1
* First alpha version

---------------




**Version 0.1**

This is a testing version, that works pretty well, but have some problems:
* quicklist items are updated only at login. If you create a new bookmark, or delete an existing one, you have to log out/log in before having your launcher updated (or manually launch the script)
* when you open a nautilus, it's icon is duplicated on the launcher as highligthed in the image below (no matter if you open it via the quicklist or the dash)
[IMG]https://dl-web.dropbox.com/get/Photos/nautilus-quicklist-3.jpg?w=bc5dcacc[/IMG]


Anyway, for the moment, I'm pretty happy with it.

I put here the code of the script. I hope somebody will find it useful..
(And maybe somebody will also find a way to improve it!)

This is the script:
```
#!/bin/bash

file=~/.local/share/applications/nautilus-home.desktop

cp /usr/share/applications/nautilus-home.desktop $file

cat >> $file <<EOF
X-Ayatana-Desktop-Shortcuts=
EOF



for bookmark in $(cat ~/.gtk-bookmarks); do

    echo -n Adding $bookmark

    path=$(echo $bookmark | sed -e 's|file:///home/'$USER'/||')
    name=$(basename $path)

    ayatana_old=$(cat $file | grep X-Ayatana-Desktop-Shortcuts)
    ayatana_new="$ayatana_old$name;"
    
    sed -e 's|X-Ayatana-Desktop-Shortcuts.*|'$ayatana_new'|g' -i $file

cat >> $file <<EOF

[$name Shortcut Group]
Name=$name
Exec=nautilus $path
TargetEnvironment=Unity
EOF

    echo ....................[OK]



done

exit 0
```


Howto:

1. Save the script anywhere in your home folder and make it executable

2. set an autorun rule via the graphical tool Power Button -> Startup Applications

3. Log out - Log in

Now you'll have the file nautilus-home.desktop located in the folder /home/your_user/.local/share/applications/

4. Drag and drop the file nautilus-home.desktop to your panel

5. Enjoy!


Log out

---

### Post by clemmy on 2011-10-19
**Version 0.2**

Logout/Login is no more required to update the quicklist, since a new shortcut have been added to the home icon, to trigger the update.

[IMG]https://dl-web.dropbox.com/get/Photos/nautilus-quicklist-v2.jpg?w=534c0aee[/IMG]


**Install**

1. open Terminal and paste the following command:
```
sudo gedit /usr/local/bin/unity-home-quicklist
```
2. type password if required, then paste the following code in Gedit:
```
#!/bin/bash

file=~/.local/share/applications/nautilus-home.desktop





#-----------------------------------------------------------
#     Create Basic File
#-----------------------------------------------------------

cp /usr/share/applications/nautilus-home.desktop $file
cat >> $file <<EOF
X-Ayatana-Desktop-Shortcuts=
EOF







#-----------------------------------------------------------
#     Add bookmarks to basic file 
#-----------------------------------------------------------

# for bookmark in $(cat ~/.gtk-bookmarks); do

cat -n ~/.gtk-bookmarks | while read number bookmark alias; do

    echo -n Adding $bookmark

    path=$(echo $bookmark | sed -e 's|file:///home/'$USER'/||')

    if [[ $alias == '' ]]; then
	name=$(basename $path)
    else
	name=$alias
    fi

    ayatana_old=$(cat $file | grep X-Ayatana-Desktop-Shortcuts)
    ayatana_new="$ayatana_old$name;"
    
    sed -e 's|X-Ayatana-Desktop-Shortcuts.*|'$ayatana_new'|g' -i $file

cat >> $file <<EOF

[$name Shortcut Group]
Name=$name
Exec=nautilus $path
TargetEnvironment=Unity
EOF

    echo ....................[OK]

done





#-----------------------------------------------------------
#    Add Update Link to basic file 
#-----------------------------------------------------------

echo -n Adding Update Link

ayatana_old=$(cat $file | grep X-Ayatana-Desktop-Shortcuts)
ayatana_new=$ayatana_old"unity-home-quicklist-spacer;unity-home-quicklist-update"

sed -e 's|X-Ayatana-Desktop-Shortcuts.*|'$ayatana_new'|g' -i $file

cat >> $file <<EOF

[unity-home-quicklist-spacer Shortcut Group]
Name=
Exec=
TargetEnvironment=Unity


[unity-home-quicklist-update Shortcut Group]
Name=Update Bookmarks
Exec=unity-home-quicklist
TargetEnvironment=Unity
EOF

echo ....................[OK]




#-----------------------------------------------------------
#    End script
#-----------------------------------------------------------

exit 0
```

3. save the file and exit

4. back to terminal, run the following commands:
```
unity-home-quicklist

nautilus ~/.local/share/applications/
```

5. A Nautilus window will popup. Drag the file nautilus-home.desktop to your launcher

6. Close Nautilus

7. Close Terminal

---

### Post by clemmy on 2011-10-21
Ok, nobody seems interested in this.. but this script is pretty useful to me, so I'm continuing it's development.

**Here it's version 0.3**
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=205028&stc=1&d=1319188243[/IMG]

**Changelog:**
* automatic install/uninstall procedure
* automatic update of the quicklist every 60 seconds (parameter easily adjustable)
* new icon


**Know bugs:**
* bookmarks containing white spaces will not work for the moment


**Install / Uninstall:**
* Download attached file
* Extract archive anywhere
* Double-click install.sh / uninstall.sh and choose "Run in terminal"


**Adjust change update rate:**
* If it is already installed, uninstall
* Open the file launcher-bookmarks.sh with text editor
* Modify the number in line 7 according to your needs:
```
rate=[COLOR="Red"]60[/COLOR] #  Update rate (in seconds)
```
* Save file and close text editor
* Install

---

### Post by clemmy on 2011-10-21
**Version 0.4**

---

