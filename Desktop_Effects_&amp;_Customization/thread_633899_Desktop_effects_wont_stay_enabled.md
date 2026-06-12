---
title: "Desktop effects wont stay enabled"
date: 2007-12-07
forum: Desktop Effects &amp; Customization
---

### Post by JohnnyTarr on 2007-12-07
Hi

I'm running ubuntu 7.10 on an HP Pavillion 952x. I've just recently installed a new video card  which is I think a nVidia GeForce 6200 put out by PNY Technologies and while I can stumble around and enable the desktop effects they don't stay enabled after I restart the computer. 

I want my desktop cube. Help help. 

:(

Thanks for any help.

---

### Post by Ub1476 on 2007-12-07
If you installed the graphic card after Ubuntu was installed, try to reconfigure X.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by erginemr on 2007-12-07
Hello,

* First things first, you need to enable the restricted driver for your NVidia card.
Main Menu -> System -> Administation -> Restricted Driver Manager

or do it manually with:
"sudo aptitude install nvidia-glx-new" from a console.

* After the installation, trying "sudo dpkg-reconfigure -phigh xserver-xorg" above is a valuable advice.

* Also make sure hat "direct rendering" has been enabled with:
"glxinfo | grep rendering" from the console.

* Finally, if you have already installed NVidia and still Compiz does not persist between boots, then you can work around this problem by adding a link to "compiz --replace" to restart Compiz automatically at each reboot. 

You can do this with:
Main Menu -> System -> Preferences -> Sessions

and adding "compiz --replace" as a new item to the existing list.

Take Care.

---

### Post by JohnnyTarr on 2007-12-12
Hi, 

I tried the stuff you mentioned but it didnt seem to work. I had one idea from some of what you said trying to get compiz to be one of the start up programs when my session loads. 

So to test what command it was I opened a terminal window and typed compiz and dang it seemed to toggle compiz effects. Then my machine crashed, When I tried this again when I was back up I got the following results.

james@kenshin:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0221 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: Segmentation fault (core dumped)
Not present. 
aborting and using fallback: /usr/bin/metacity 

does that make any sense?

Aaah still need help. 

:confused:

---

### Post by mozetti on 2007-12-12
As **erginemr** mentioned, the command for compiz is: ```
compiz --replace
```

---

### Post by JohnnyTarr on 2007-12-12
I will try to get the command to startup when my session begins with the command you provided. 

But what is all this about xgl not being present?

freaky

---

