---
title: "Found Desktop in folder - help!"
date: 2009-04-02
forum: General Help
---

### Post by You bunt to? on 2009-04-02
I have a dual boot PC with XP and Ubuntu, managed by Grub. Linux is pretty new to me, and every so often I boot into Ubuntu to learn some more. This current session has been particularly good - except that I ran into a problem in that I couldn't run videos in YouTube (but I could download them using the DownLoadHelper add-on). 

I tried uninstalling/reinstalling FileFox using Synaptic but didn't make any headway. I then uninstalled everything of FireFox using synaptic and downloaded the FireFox .deb file to the Desktop. I had previously noticed that Thunderbird was installed in Desktop/Documents/Thunderbird so I downloaded FireFox to the Desktop, extracted it to Desktop/Documents/FireFox and created a desktop icon with the 'firefox/firefox' runtime script. (Somewhere I had seen a note that stated that the synaptic package manager was inferior to installing FireFox this way). 

So far so good. I revisited YouTube but it complained that Flash was missing. I had previouslt downloaded a .deb flash file to the Desktop, so I doubleclicked on it to install it, but came up with an error! In fact everything on the Desktop was none-functional. I searched around and eventually found a folder called "Desktop" in the Trash. I've moved the folder to the Desktop (and everything within is fuctional) but how do I replace the current Desktop with this folder??

tia (thanks in advance)
Alan ("You bunt to?")

---

### Post by albinootje on 2009-04-02
I suggest to create a new user on your Ubuntu installation, copy your old data over to the new user account, and install Thunderbird and Firefox via Synaptic Package Manager.

And you can have flash for youtube working like this :
```

sudo apt-get install flashplugin-nonfree

```
Or install the package flashplugin-nonfree in Synaptic.

---

### Post by albinootje on 2009-04-02
To create the new user, hit alt+F2 in your Ubuntu desktop (after you logged in), and then type :
```

gksudo users-admin

```

---

### Post by You bunt to? on 2009-04-03
> **albinootje said:**
> To create the new user, hit alt+F2 in your Ubuntu desktop (after you logged in), and then type :
```

gksudo users-admin

```

Thanks.. but I have already solved all the problems, EXCEPT 'playing Youtube videos on their site' which displays..

"Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player."

..just under the title of the video.

I have JavaScript turned on in Firefox.

In a terminal I ran
sudo apt-get update
sudo apt-get upgrade

Synaptic shows that I have installed:
adobe-flashplugin version 10.0.22.87-1
flashplugin-nonfree version 9.0.159.0ubuntu1~hardy1
libflash-0c2 version 0.4.13-9ubuntu1 ****
libflash-swfplayer version 0.4.13-9ubuntu1 ****

**** for some old flash videos I have

The Firefox Error Console contains many warnings for YouTube (and UbuntuForums) - in parsing CSS files on those sites.

Help please

---

