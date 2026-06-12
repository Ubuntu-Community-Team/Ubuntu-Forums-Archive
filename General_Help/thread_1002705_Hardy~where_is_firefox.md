---
title: "Hardy~where is firefox???"
date: 2008-12-05
forum: General Help
---

### Post by KEE on 2008-12-05
```
whereis firefox
```
=```

firefox: /usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/share/firefox
```
but im try to install flashplayer 10 so i get this...

```

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/bin/firefox /etc/firefox /usr/lib/firefox

WARNING: /usr/bin/firefox /etc/firefox /usr/lib/firefox is not a directory.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): 
```

---

### Post by thegreenblob on 2008-12-05
Have you tried just using the deb? [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Or just: sudo apt-get install flashplugin-nonfree

---

### Post by taurus on 2008-12-05
Why not put it in /usr/lib/mozilla since firefox will look in there anyway?

---

### Post by KEE on 2008-12-05
> **thegreenblob said:**
> Have you tried just using the deb? [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Or just: sudo apt-get install flashplugin-nonfree

yeah i got that installed and extracted...I dont know want to do here. heres how i started ..

got the thing from here

[http://www.adobe.com/shockwave/downl...shockwaveFlash](http://www.adobe.com/shockwave/downl...shockwaveFlash)

```

cd ~/Desktop/install_flash_player_10_linux/
``````
sudo chmod +x flashplayer-installer
``````
sudo ./flashplayer-installer
```
```
Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/bin/firefox /etc/firefox /usr/lib/firefox

WARNING: /usr/bin/firefox /etc/firefox /usr/lib/firefox is not a directory.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): 

```

---

### Post by KEE on 2008-12-05
> **taurus said:**
> Why not put it in /usr/lib/mozilla since firefox will look in there anyway?
```

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/mozilla

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): 
```yeah that was the first thing i tried to do...the only problem it wont let you paste it there

---

### Post by SeanHodges on 2008-12-05
whereis is providing all the directories that contain Firefox files (binary, source, manual page files, etc), not just the directory containing the plugins.

You want to type this into the installer:

> /usr/lib/xulrunner

That will install it to the right place. Remember to restart Firefox if it is running.

---

### Post by KEE on 2008-12-05
> **SeanHodges said:**
> whereis is providing all the directories that contain Firefox files (binary, source, manual page files, etc), not just the directory containing the plugins.

You want to type this into the installer:



That will install it to the right place. Remember to restart Firefox if it is running.

```
Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/xulrunner 

WARNING: /usr/lib/xulrunner is not a directory.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): 

```yeah that was a good idea though...im redownload again and gona try to see if i can extract it to /usr/lib/mozilla
since copy/paste is refused

---

### Post by KEE on 2008-12-05
so i tried and what taurus suggested and it dose not work either =(


```
tar: install_flash_player_10_linux: Cannot mkdir: Permission denied
tar: install_flash_player_10_linux/flashplayer-installer: Cannot open: No such file or directory
tar: install_flash_player_10_linux/libflashplayer.so: Cannot open: No such file or directory
tar: Error exit delayed from previous errors

```

---

### Post by KEE on 2008-12-05
why does Linux have to be so simple and yet so difficult at the sometime.

---

### Post by benny bronx on 2008-12-05
Did you try the suggestion posted by thegreenblob?  Download the deb for ubuntu, right click on it, and choose open with gdebi package installer.  That's it.  Just make sure that you have all the old flash files deleted before doing this.

---

### Post by taurus on 2008-12-05
Where are you trying to unpack the flash player?

---

### Post by KEE on 2008-12-05
> **taurus said:**
> Where are you trying to unpack the flash player?

yup

---

### Post by spcwingo on 2008-12-05
How about usr/lib/firefox-3.0.4...or whatever version you're running.

---

### Post by Yellow Pasque on 2008-12-05
> How about usr/lib/firefox-3.0.4..
The directory for FF3 plugins is /usr/lib/firefox-addons/plugins. You don't need to run the installer script; just copy libflashplayer.so there.
```
cd <wherever you unzipped libflashplayer.so>
chown root:root libflashplayer.so
sudo chmod 755 libflashplayer.so
sudo mv libflashplayer.so /usr/lib/firefox-addons/plugins
```

---

### Post by KEE on 2008-12-05
> **Temüjin said:**
> The directory for FF3 plugins is /usr/lib/firefox-addons/plugins. You don't need to run the installer script; just copy libflashplayer.so there.
```
cd <wherever you unzipped libflashplayer.so>
chown root:root libflashplayer.so
sudo chmod 755 libflashplayer.so
sudo mv libflashplayer.so /usr/lib/firefox-addons/plugins
```
```
root@root-desktop:~$ cd ~/home/root/Desktop/liblibflashplayer.so
bash: cd: /home/root/home/root/Desktop/liblibflashplayer.so: No such file or directory
root@root-desktop:~$ 
root@root-desktop:~$ chown root:root libflashplayer.so
chown: cannot access `libflashplayer.so': No such file or directory
root@root-desktop:~$ sudo chmod 755 libflashplayer.so
chmod: cannot access `libflashplayer.so': No such file or directory
root@root-desktop:~$ sudo mv libflashplayer.so /usr/lib/firefox-addons/plugins
mv: cannot stat `libflashplayer.so': No such file or directory

```

I m wondering if i did it right, and still i cant move libflashplayer.so there, Im denied everytime

---

### Post by KEE on 2008-12-05
oh i just figured out that theres a ubuntu .deb installer for you in the list =P never notice it before XD thanks all for the speedy replies and happy holly days. i gave ya all thank you's =)

---

