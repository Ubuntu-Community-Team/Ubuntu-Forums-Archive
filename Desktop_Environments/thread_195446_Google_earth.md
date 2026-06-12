---
title: "Google earth"
date: 2006-06-12
forum: Desktop Environments
---

### Post by ubman on 2006-06-12
Hi all
I just d-loaded GoogleEarthLinux.bin
and i don't know how to install it The Above name is the exact file name.
i knew this would be a good place to ask!:rolleyes:

---

### Post by pyromithrandir on 2006-06-12
Just open up a terminal and go to the directory that it is in and type these two commands:
> chmod +x GoogleEarthLinux.bin
./GoogleEarthLinux.bin

---

### Post by Ahriman on 2006-06-12
try this from the terminal:
```
sh GoogleEarthLinux.bin
```

Edit: lol, beat me by that || much

---

### Post by Artist22405 on 2006-06-12
I also downloaded google earth all I did was go to proprties them permissions and checked excute   then ran in termial 
the  only thing is its doesnt work so well

---

### Post by kblake007 on 2006-06-12
I just did this too, I can tell you that it is rad.  First make the file executable:
**chmod +x GoogleEarthLinux.bin**
Then run as root:
**./GoogleEarthLinux.bin**
Accept default installation options.  At the end of the install the installer will prompt you to run the file.  This is fine. At the moment I am having difficulties running the application with non root permissions.  I will keep you posted.

---

### Post by pyromithrandir on 2006-06-12
[QUOTE=kblake007]I just did this too, I can tell you that it is rad.  First make the file executable:
**chmod +x GoogleEarthLinux.bin**
Then run as root:
**./GoogleEarthLinux.bin**
Accept default installation options.  At the end of the install the installer will prompt you to run the file.  This is fine. At the moment I am having difficulties running the application with non root permissions.  I will keep you posted.[/QUOTE]
If you don't run ./GoogleEarthLinux.bin as root and install it in your home directory, it won't give you any problems. That's what I did.

---

### Post by ubman on 2006-06-12
[QUOTE=pyromithrandir]Just open up a terminal and go to the directory that it is in and type these two commands:[/QUOTE]
chmod +x GoogleEarthLinux.bin
Then run as root:
./GoogleEarthLinux.bin
Accept default installation options. At the end of the install the installer will prompt you to run the file. This is fine. At the moment I am having difficulties running the application with non root permissions. I will keep you posted.

This is how i installed it Works Flawlessly(so far!):D

You Know I forgot to thank you for your help!!  :-)

---

### Post by mishranurag on 2006-06-12
Kudos to Google for launching one more useful application for Linux Platform.

Anurag

---

### Post by vierranet on 2006-06-13
Help, Installed Google Earth Getting Permission Denied when I used the command line and type googleearth, this is what I am getting.

vierranet@vierranet1:~$ googleearth
symlink: Permission denied

vierranet@vierranet1:~$ cd ~/Desktop
vierranet@vierranet1:~/Desktop$ chmod +x GoogleEarthLinux.bin
vierranet@vierranet1:~/Desktop$ ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 

4.0.1563..................................................................
Installing mimetypes...
mkdir: `/home/vierranet/.local/share/mime/packages/': Permission denied
cp: accessing `/home/vierranet/.local/share/mime/packages//googleearth-mimetypes.xml': Permission denied
Running /usr/bin/update-mime-database /home/vierranet/.local/share/mime
/usr/bin/update-mime-database: I don't have write permission on /home/vierranet/.local/share/mime.
Try rerunning me as root.
Installing desktop menu entries...
cp: cannot create regular file `/home/vierranet/.local/share/applications/googleearth.desktop': Permission denied
mkdir: `/home/vierranet/.kde/share/applnk': Permission denied
cp: accessing `/home/vierranet/.kde/share/applnk/googleearth.desktop': Permission denied
cp: accessing `/home/vierranet/.gnome/apps/googleearth.desktop': Permission denied
googleearth

---

### Post by quail-linux on 2006-06-13
Hi all,

I found this howto on the wiki to setup google earth
[https://wiki.ubuntu.com/GoogleEarth?highlight=%28google%29](https://wiki.ubuntu.com/GoogleEarth?highlight=%28google%29)

Enjoy

---

### Post by ubman on 2006-06-13
[QUOTE=vierranet]Help, Installed Google Earth Getting Permission Denied when I used the command line and type googleearth, this is what I am getting.

vierranet@vierranet1:~$ googleearth
symlink: Permission denied

vierranet@vierranet1:~$ cd ~/Desktop
vierranet@vierranet1:~/Desktop$ chmod +x GoogleEarthLinux.bin
vierranet@vierranet1:~/Desktop$ ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 



If you follow post #7 it even puts it in your menu under applications>internet>

If you follow post #7 and read it all To make it more clear
the final comand should be  "sudo ./GoogleEarthLinux.bin"
It even puts in your menu under Applications>Internet>Google Earth:razz:

---

### Post by barakaspeed on 2006-06-13
Create an Icon in the Applications Menu as it didn't do it automatically for me.

gedit ~/.local/share/applications/GoogleEarth.desktop

Save this in the file:

```
[Desktop Entry]
Encoding=UTF-8
Name=Google Earth
GenericName=3D planet viewer
Comment=Explore, search and discover the planet
Exec=/usr/local/google-earth//googleearth %f
Terminal=false
MultipleArgs=false
Type=Application
Icon=/usr/local/google-earth//googleearth-icon.png
Categories=Application;Network
MimeType=application/vnd.google-earth.kml+xml;application/vnd.google-earth.kmz;application/earthviewer;application/keyhole


```

---

### Post by FyreBrand on 2006-06-13
I used the wiki instructions and had the same icon problem.  You can also use the alacarte menu editor to add the icon to the applications menu.  Just make sure you select the binary file and not the desktop configuration file like I did the first time.  The desktop config file has the google earth icon and I selected it by mistake. (well by mistake I mean I'm a long time Windows user and I made a hasty assumption)

---

### Post by phido on 2006-06-13
How can I set it up in firefox so it opens placemarks in the open window and doesnt start a new gEarth instance?

---

### Post by anodizer on 2006-06-13
[QUOTE=vierranet]Help, Installed Google Earth Getting Permission Denied when I used the command line and type googleearth, this is what I am getting.

vierranet@vierranet1:~$ googleearth
symlink: Permission denied
[/QUOTE]

Same here. Maybe it's just a bug, as it is in beta stage. I think creating a menu shortcut with a command like "gksudo googleearth" should be a good workaround for this.

[QUOTE=ubman]
If you follow post #7 it even puts it in your menu under applications>internet>

If you follow post #7 and read it all To make it more clear
the final comand should be  "sudo ./GoogleEarthLinux.bin"
It even puts in your menu under Applications>Internet>Google Earth:razz:[/QUOTE]

Nope, it's not.

---

### Post by REBELinBLUE on 2006-06-13
The reason is because you installed it as root and then ran the application afterwards, so it creates your configuration files as root thus when you try to run it you are unable to do so. I had the same problem.

Simple fix

```
sudo chown -R user:user ~/.googleearth
sudo chown -R user:user ~/.local/share/
```

:)

---

### Post by Jasper Houtman on 2006-06-14
REBELinBLUE thanks for that fix!!!
I have been trying for the past 1,5 hour to get that to work!

Could only get it to work installing as root (wouldn't run otherwise)
So I had temporarily fixed it by creating a menu item which ran "sudo googleearth" in the terminal. 

Now I won't have to type in my PWD everytime I run google earth.

---

