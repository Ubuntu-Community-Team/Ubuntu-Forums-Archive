---
title: "Firefox Freezes opening Youtube Videos"
date: 2009-04-22
forum: General Help
---

### Post by frtrev on 2009-04-22
Hi Guys,
 
I am new on Ubuntu, I installed a dual boot system with Ubuntu 8.10 and XP, I really like Ubuntu but I am having a problem trying to open a youtube video with firefox.
 
I saw some posts with recommendations but I could not find any concrete answer, so my question is:
 
Is there a way to solve this problem for firefox?
 
If the plug in requires an re-install procedure, can you describe it?
 
I also tried using Opera browser, but it fails more than firefox, it also freezes but not only with youtube but also with some more, but Opera freezes the content not like firefox which turns black and white.
 
So I am almost sure that the plugin being used is the one with the problem.
 
I hope you can help me.   :confused:
 
Thanks.

---

### Post by Sam Lars on 2009-04-24
So Firefox always freezes when you go to YouTube?  Does other Flash content work?
The package you would want to reinstall is flashplugin-nonfree.
Also, are you using 32-bit or 64-bit?

---

### Post by paradigm2 on 2009-04-24
> **Sam Lars said:**
> So Firefox always freezes when you go to YouTube?  Does other Flash content work?
The package you would want to reinstall is flashplugin-nonfree.
Also, are you using 32-bit or 64-bit?

Hello.

In addition to this, do this from the terminal (Applications -> Accessories -> Terminal) and post the output:

```

lspci

```

This will tell us what hardware you have so we can check for hardware specific issues.

---

### Post by frtrev on 2009-04-24
Thanks for your answers guys, I fixed it manually yesterday and I hope this procedure helps others:
 
Problem:
All flash content worked OK but when opening a youtube video, firefox browser would freeze and CPU usage at 100%.
Hardware:
Motherboard GA-M61SME-S2
AMD Athlon XP 64 2.0 GHz
[COLOR=#fd6724]NVIDIA® GeForce 6100 / nForce 405 GPU[/COLOR]
 
1) I searched for the "libflashplayer.so" file, and found several.
2) I deleted all of them with the following command: sudo rm libflashplayer.so
3) I installed the "Macromedia Flash Player 10" form the site, using the .deb file.
4) It did not work, firefox kept requesting for installing the plugin.
5) I searched for the "libflashplayer.so" file again, I found it on a folder named: "flashplugin-nonfree".
6) I copied it to the folder usr/lib/mozila-firefox/plugins
7) And it worked ! 
 
Thanks a lot.

---

### Post by SuperSonic4 on 2009-04-24
I believe you can use a symlink in step 6 too.

In step 3 if you get the tarball you can copy and paste the plugin to ~/.mozilla/plugins which is especially handy for downloading 64bit flash from adobe

---

### Post by frtrev on 2009-04-24
what is a symlink?

---

### Post by codeseer on 2009-04-24
I wish I would have seen your post earlier. I have the solution in a text file that I just copy/paste out depending on if it's a 32-bit or 64-bit user. I've pasted it to probably 10 threads now; the flash in the repositories just doesn't work on everything.

Here it is and it answers your symlink question in the install part:

```

Download it from here: http://labs.adobe.com/downloads/flashplayer10.html

Extract it using: tar zxvf libflashplayer-*.tar.gz

Clean up past installation of Flash:

sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

Install the new Flash:

sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins

```

---

### Post by codeseer on 2009-04-24
As commonly as the issue arises, it should probably be stickied.

---

