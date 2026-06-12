---
title: "need help installing Flash for Firefox"
date: 2009-06-12
forum: General Help
---

### Post by dluzius on 2009-06-12
Don't seem to be able to install Flash in Firefox 3.0
New to Ubuntu, installed 9.04 less than 2 weeks ago. Guess I need step by step instructions on this. TIA     Dave

---

### Post by Therion on 2009-06-12
Go here and download the .deb file from the menu:  [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Just run it using GDebi installer when you're prompted to.  

If that fails, save the file to your desktop instead.

Now move the file to your /Home folder.

Open a Terminal and paste in ```
sudo apt-get remove flashplugin-nonfree
```
Then paste in ```
sudo dpkg -i sudo dpkg -i install_flash_player_10_linux.deb
```

That should do it.

---

### Post by Mr. Wellichen on 2009-06-12
Did you already tried  "sudo apt-get install flashplugin-nonfree". Otherwise you can try to enter in a site that uses flash, (maybe not the YouTube), if the site don't recognize that you don't have the plugin for flash Firefox will ask you for the install.;)

---

### Post by dluzius on 2009-06-12
Tks Therion, but I did as you suggested, and it didn't work, instead I got error message fron Terminal.

dpkg: error processing sudo (--install):
 cannot access archive: No such file or directory
dpkg: error processing dpkg (--install):
 cannot access archive: No such file or directory
dpkg: error processing -i (--install):
 cannot access archive: No such file or directory
(Reading database ... 116785 files and directories currently installed.)
Preparing to replace adobe-flashplugin 10.0.22.87-1 (using install_flash_player_10_linux.deb) ...
Unpacking replacement adobe-flashplugin ...
Setting up adobe-flashplugin (10.0.22.87-1) ...

Errors were encountered while processing:
 sudo
 dpkg

---

### Post by JECHO on 2009-06-12
> **dluzius said:**
> Tks Therion, but I did as you suggested, and it didn't work, instead I got error message fron Terminal.

dpkg: error processing sudo (--install):
 cannot access archive: No such file or directory
dpkg: error processing dpkg (--install):
 cannot access archive: No such file or directory
dpkg: error processing -i (--install):
 cannot access archive: No such file or directory
(Reading database ... 116785 files and directories currently installed.)
Preparing to replace adobe-flashplugin 10.0.22.87-1 (using install_flash_player_10_linux.deb) ...
Unpacking replacement adobe-flashplugin ...
Setting up adobe-flashplugin (10.0.22.87-1) ...

Errors were encountered while processing:
 sudo
 dpkg



Follow my tutorial [here]("http://blog.jecho.info/?p=11"). :)

NOTE: you will need to change the "w32codecs" to "w64codecs" if you are using 64-bit ubuntu.

---

### Post by tlois on 2009-06-13
OK.  My problems is that I am trying to get firefox to use the latest flash that i have installed, but only the older 9.something shows up when i look at plugins in ff.  how can i make it use the newer flash?  thanks for any help.

oddly, ff on one computer with jaunty has the latest version, but a fresh install of jaunty on my other computer will only show the older version.

---

### Post by Amilo1718 on 2009-06-13
i just went to the synaptic & installed the flash-nonfree

---

