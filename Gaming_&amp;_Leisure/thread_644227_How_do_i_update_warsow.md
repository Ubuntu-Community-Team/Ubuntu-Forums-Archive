---
title: "How do i update warsow?"
date: 2007-12-18
forum: Gaming &amp; Leisure
---

### Post by Tanjer1588 on 2007-12-18
I have looked every ware but the internet is full of junk, I cant find anyware that will simply tell you how to update warsow, I downloaded warsow from the Package manager and it seems to be an older version. warsow 0.32 is out and i dont want to have to reinstall it again from a web site. so is there some simple way to update?

thank you

---

### Post by Beren Camlost on 2007-12-18
Download either the full version or the patch from one of the mirrors found here: [http://www.warsow.net/forum/viewtopic.php?id=15585](http://www.warsow.net/forum/viewtopic.php?id=15585)

If you decide to install the full version 0.32, make sure you uninstall your older version first with Synaptic/Adept/Apt-Get.

---

### Post by Tanjer1588 on 2007-12-18
what do i do with the patch once i unzip it? i have had this zip file before, and i didnt know what to do with it.

---

### Post by jonathansizz on 2008-01-02
Bump.

I'd also like to know the correct procedure for installing the 0.32 update.

Thanks

---

### Post by der_joachim on 2008-01-03
Easy! Download all the packages [here]("http://www.getdeb.net/search.php?keywords=warsow") and install them manually from the terminal:

```

cd /path/to/your/download/directory
sudo dpkg -i warsow*.deb

```

---

### Post by smartalecks on 2008-01-19
Download the latest version of Warsow here: [www.warsow.net](www.warsow.net)

As far as I know there is no available .deb of the latest version of Warsow, but installing it and running it is easy:
(.4 was released today, I encourage everyone to download it and start playing because they have updated the movement system and everyone is starting relatively anew! be aware there a few bugs but they should be fixed soon...)

Warsow does not have an auto-updater, you must download the latest release and install it over the old one. If you want to save your settings backup basewsw/config.cfg and replace it when you are done installing the latest version...

1. Download the linux .zip
2. Make a folder in your home directory named .games (optional), extract contents of the .zip and move the folder with the extracted files to there. Rename the folder the files extracted into 'warsow'
3. Do these in a terminal:
```

$   sudo chmod +x ~/.games/warsow/warsow
$   sudo chmod +x ~/.games/warsow/warsow.i386

```
4. Make a launcher on your desktop:
```

Type: Application in Terminal
Name: Warsow
Command: sh ~/.games/warsow/warsow

```

Save this image, move it to ~/.icons or some other folder
[IMG]http://img253.imageshack.us/img253/4976/warsowih6.png[/IMG]

And set the launcher icon to it. Should work now, just click on the icon!

---

### Post by Perfect Storm on 2008-01-20
Ubuntu 64-bit Installation guide complete: [http://gaming.gwos.org/doku.php/guides:64bit:warsow](http://gaming.gwos.org/doku.php/guides:64bit:warsow)

---

