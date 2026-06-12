---
title: "Themes, Ubuntu 13.10"
date: 2014-01-07
forum: Desktop Environments
---

### Post by andreadixon825 on 2014-01-07
Hi, I have downloaded some themes and I can not get access to place my theme in the theme folder, How can I get access to this and where is the theme folder because when I did a search It showed up a lot of folders name themes, please help thanks for your time. Oh and I fagot to say what version I'm using its Ubuntu 13.10

---

### Post by deadflowr on 2014-01-07
Themes go into one of two places.

First the easy place, /home/Yourusername/.themes.
This is easy because it's in your own home folder, so extra rights aren't needed.
The dot means that it is a hidden folder.
To access or show hidden folder and files when extracting the download, right-click on the mouse in the window the opens when you click to open the theme folder. Themes generally will be downloaded in a tarball(tar,gz,bz,etc.etc) when you right click on it in the downloads folder a window will open called archive manager, simply right click in the middle window to access a few options one of which will be show hidden files and folders.
Find the themes folder and extract the contents into it.
Starting out, this one would be the preferred place, so you don't have to muck too much in the system folders.

The harder one is in /usr/share/themes.
It's a system folder, so you would need to have root to move it into here.

I would first extract the folder inside the home folder and then copy it into the system folder using sudo(root).

When you do finally get the themes inside the themes folder, changing themes on Ubuntu needs an extra app.
So the best app to use on Ubuntu 13.10 would be unity-tweak-tool.
It's in the software center, so don't be afraid to install it.

---

### Post by andreadixon825 on 2014-01-07
Ok thanks so much, Im going to play around with Ubuntu just to get    	 	 	 	   formulator to it, thanks and happy new year.

---

### Post by buzzingrobot on 2014-01-07
Ditto for icons.  Put them in /usr/share/icons or /home/username/.icons.

---

### Post by andreadixon825 on 2014-01-07
ok thanks

---

