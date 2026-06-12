---
title: "Install Faenza Icon Theme"
date: 2012-10-10
forum: Desktop Environments
---

### Post by on2mars on 2012-10-10
How do you install new icon themes with XFCE?  In particle, I was thinking about the Faenza icons.

---

### Post by Toz on 2012-10-10
The Faenza icon theme has a PPA - [https://launchpad.net/~tiheum/+archive/equinox]("https://launchpad.net/~tiheum/+archive/equinox").

To install, from a terminal window, run the following commands:
```

sudo add-apt-repository ppa:tiheum/equinox
sudo apt-get update && sudo apt-get install faenza-icon-theme

```

As for general icon installation procedures, extract icon packages to:
**_~/.icons_** -> for individual user use (create folder if it doesn't exist)
**_/usr/share/icons_** -> for system-wide use (required sudo)

Let us know if you need more detailed instructions.

---

### Post by on2mars on 2012-10-11
After I added the PPA and updated it, it said that it could not fetch the tiheum/equinox ppa.  And I tried to install it and it said that faenza-icon-theme was not found.  I don't know what is wrong because I use the terminal to add ppas all the time and this has never happened before.

---

### Post by Toz on 2012-10-11
What version of xubuntu are you using?

What is the output of:
```
sudo apt-get update
```

...and
```
apt-cache policy faenza-icon-theme
```

---

### Post by on2mars on 2012-10-11
I am using 12.10.

---

### Post by DarkAmbient on 2012-10-11
It hasn't been packaged for 12.10 yet I think.

Tried it myself and got this:

> W: Misslyckades med att hämta [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/quantal/main/source/Sources)  404  Not Found

W: Misslyckades med att hämta [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/quantal/main/binary-amd64/Packages](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/quantal/main/binary-amd64/Packages)  404  Not Found

W: Misslyckades med att hämta [http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/tiheum/equinox/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


---

### Post by on2mars on 2012-10-11
That looks pretty similar to what I got.  Not exactly sure because of the different language though.  Will they package it for 12.10 when 12.10 is released?

---

### Post by wojox on 2012-10-11
> **on2mars said:**
> I am using 12.10.

Download [Faenza Icons]("http://www.deviantart.com/download/173323228/faenza_icons_by_tiheum-d2v6x24.zip")

Open a terminal and move to the directory you downloaded to:
```
wojox@wojox-testing:~$[COLOR="Red"] cd Downloads/[/COLOR]
wojox@wojox-testing:~/Downloads$[COLOR="Red"] unzip faenza_icons_by_tiheum-d2v6x24.zip[/COLOR] 
Archive:  faenza_icons_by_tiheum-d2v6x24.zip
  inflating: Faenza.tar.gz           
  inflating: Faenza-Dark.tar.gz      
  inflating: Faenza-Darkest.tar.gz   
  inflating: Faenza-Darker.tar.gz    
  inflating: Faenza-Ambiance.tar.gz  
  inflating: Faenza-Radiance.tar.gz  
  inflating: emesene-faenza-theme.tar.gz  
  inflating: AUTHORS                 
  inflating: ChangeLog               
  inflating: COPYING                 
  inflating: INSTALL                 
  inflating: README                  
  inflating: UNINSTALL               
wojox@wojox-testing:~/Downloads$ ls
AUTHORS                      Faenza-Darker.tar.gz                Faenza.tar.gz
ChangeLog                    Faenza-Darkest.tar.gz               INSTALL
COPYING                      Faenza-Dark.tar.gz                  README
emesene-faenza-theme.tar.gz  faenza_icons_by_tiheum-d2v6x24.zip  UNINSTALL
Faenza-Ambiance.tar.gz       Faenza-Radiance.tar.gz
wojox@wojox-testing:~/Downloads$ [COLOR="Red"]sudo ./INSTALL[/COLOR] 
[sudo] password for wojox: 

```

---

### Post by Toz on 2012-10-11
They can also be found here: [http://tiheum.deviantart.com/art/Faenza-Icons-173323228]("http://tiheum.deviantart.com/art/Faenza-Icons-173323228"). There is a readme file in the zip file with instructions on how to install.

---

### Post by on2mars on 2012-10-11
That worked great wojox.  Thanks guys for the help.

---

