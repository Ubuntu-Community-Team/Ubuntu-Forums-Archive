---
title: "Cannot play Youtube"
date: 2009-01-21
forum: General Help
---

### Post by sbasak on 2009-01-21
Hi

I am running Ubuntu 8.10 from USB (created from live CD).

I cannot play any youtube/google video files :(

I tried to Totem (by enabling youtube plugin) but Totem movie player just hangs when I try to search for youtube videos.

Do I have to install something using sudo etc.?

Thanx

---

### Post by Vince4Amy on 2009-01-21
You just need to install Flash Player

```
sudo apt-get install flashplayer-nonfree
```

Restart your browser after installing this package.

---

### Post by nothingspecial on 2009-01-21
> **Vince4Amy said:**
> You just need to install Flash Player

```
sudo apt-get install flashplayer-nonfree
```

Restart your browser after installing this package.

The package is called flashplugin-nonfree

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Vince4Amy on 2009-01-21
Oh yes, I wasn't on a Ubuntu machine at the time.

---

### Post by Tomatz on 2009-01-21
The flash player in the repos is buggy :(

Download a .deb from here :)

[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

(Dropdown the dropwown box and select ".deb for 8.04+")

---

### Post by rivalslayer on 2009-01-21
The repo file is bad. Get the official version, from Adobe Website...
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by sbasak on 2009-01-21
Ok - once I download the official Adobe version, how do I actually install it?

---

### Post by Tomatz on 2009-01-21
> **sbasak said:**
> Ok - once I download the official Adobe version, how do I actually install it?

Double click it BUT make sure you selected the .deb from the download page (dropdown box). If it says there is a later version available in the repos (and wont let you install), open a terminal and do this:

**Close all browsers!**

```
cd ~/Desktop

sudo apt-get remove --purge flashplugin-nonfree

sudo dpkg -i --force-all install_flash_player_10_linux.deb
```


;)

---

### Post by nothingspecial on 2009-01-21
> **Tomatz said:**
> Double click it BUT make sure you selected the .deb from the download page (dropdown box). If it says there is a later version available in the repos (and wont let you install), open a terminal and do this:

**Close all browsers!**

```
cd ~/Desktop

sudo apt-get remove --purge flashplugin-nonfree

sudo dpkg -i --force-all install_flash_player_10_linux.deb
```


;)

Is this right? Tomatz, you helped me a number of times when I had no clue and so I take your advice seriously.  Flash works fine for me on 2 brand new installs 5 days ago. Should I remove flashplugin-nonfree even though it works?

---

### Post by Tomatz on 2009-01-21
> **nothingspecial said:**
> Is this right? Tomatz, you helped me a number of times when I had no clue and so I take your advice seriously.  Flash works fine for me on 2 brand new installs 5 days ago. Should I remove flashplugin-nonfree even though it works?


If you are not experiencing any issues then leave the repo version installed. If you are experiencing slow flash animation and/or high CPU usage (or even no flash at all) while using flash then i would advise that you install the above version. These problems usually occur when running flash under compiz.

;)

---

### Post by nothingspecial on 2009-01-21
> **Tomatz said:**
> If you are not experiencing any issues then leave the repo version installed. If you are experiencing slow flash animation and/or high CPU usage (or even no flash at all) while using flash then i would advise that you install the above version. These problems usually occur when running flash under compiz.

;)

Ahh well, we don`t bother with compiz here.

Thanks  :D

---

### Post by Tomatz on 2009-01-21
> **nothingspecial said:**
> ahh well, we don`t bother with compiz here.

Thanks  :d

;)

---

### Post by sbasak on 2009-01-21
sudo dpkg -i --force-all install_flash_player_10_linux.deb

worked perfectly

---

