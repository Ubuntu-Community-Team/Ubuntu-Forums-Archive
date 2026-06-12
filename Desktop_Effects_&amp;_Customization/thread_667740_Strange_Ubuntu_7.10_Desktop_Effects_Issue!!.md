---
title: "Strange Ubuntu 7.10 Desktop Effects Issue!!"
date: 2008-01-14
forum: Desktop Effects &amp; Customization
---

### Post by Javawag on 2008-01-14
Hi all,

First post here! I've recented started dualbooting Ubuntu 7.10 with Windows on my machine to see if I like it and I've come across a strange problem! Occasionally, when using desktop effects, the close/minimise/maximise buttons on the window frames disappear, although they still show the tooltips and pointing hand cursor when you hover where they should be, and they do still work also. Interestingly, it was working fine until I got curious and run "GL Desktop"... any ideas on what I could try to fix this? If you need any more information (which you probably will) just ask!

Thanks,
- Javawag

---

### Post by 5735guy on 2008-01-15
If you are using emerald,this means is not running. To get emerald to work you need to :

press alt + f2

then type   

emerald --replace

that should fix the problem.

To make sure emerald runs at startup you need to go to :

preferences>sessions

the type

emerald --replace

in both boxes.

---

### Post by Javawag on 2008-01-15
OK, just tried that now. The borders of the windows disappear and reappear again, but the problem still exists... I think emerald was already running but something is going horribly wrong with it... if I open Emerald Theme Manager, the Themes list is empty (is this normal?) and if I click "Fetch GPL'd themes" or "Fetch non GPL'd theme" from the repositories tab, the please wait dialogue box appears and disappears, but nothing is downloaded. Interestingly, under the edit themes tab, the theme I'm using at the moment (truglass) works (but with the obvious min/max/close button issues), but others work less well - for example, if I choose oxygen, the title bar background disappears (ie the icon, text, and min/max/close buttons appear to float above the window contents...) and pixmap shows a sort of corrupt looking thing. 

Any ideas/suggestions?
I can get screenshots if that'll help by the way...

- Javawag

---

### Post by mikeym on 2008-01-15
What video card are you using? And what diver do you have in your /etc/X11/xorg.conf file?

---

### Post by Javawag on 2008-01-15
As shown by /etc/X11/xorg.conf:

Graphics Card: "nVidia Corporation G72 [GeForce 7300 SE]"
Driver: "nvidia"

It's not the best graphics card going hehe!

- Javawag

---

### Post by mikeym on 2008-01-15
I was asking because the nvidia native drivers have been driving me up the wall. I have posted 2 threads on the affiliated forum nvnews about it but haven't has so much as a reply. 

[Post 1]("http://www.nvnews.net/vbulletin/showthread.php?t=105919")
[Post 2]("http://www.nvnews.net/vbulletin/showthread.php?t=106244")

Yours sounds like it could be related to what [these people]("http://www.nvnews.net/vbulletin/showthread.php?t=104822") are reporting.

---

### Post by Javawag on 2008-01-15
Yes! It's very similar to what they're reporting... how would I go about reverting to the earlier nvidia driver version? And what would I lose from not having the latest version (I guess not a lot?)

Thanks!
- Javawag

---

### Post by mikeym on 2008-01-16
I have to warn that I tried reverting to the version they recommend and X wouldn't start again afterwards. But that could be because of my 8600 GTS.

Download the driver you want from NVIDIA ([http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)) make sure to go into us rather than uk because the don't update the uk ones! 

Switch to the command prompt with [ctrl] + [alt] + F2 and log in. Change to the directory you saved the NVIDIA-linux-Whatever file.

Type:

```

sudo /etc/init.d/gdm stop
chmod +x NVIDIA-linux*
sudo ./NVIDIA-linux*

```

follow the porompts to install

```

sudo /etc/init.d/gdm start

```

If you get stuck with a driver that doesn't work go back to the command prompt and type:

```

sudo /etc/init.d/gdm stop
sudo ./NVIDIA-linux* --update
sudo /etc/init.d/gdm start

```

To download and install the latest driver.

---

