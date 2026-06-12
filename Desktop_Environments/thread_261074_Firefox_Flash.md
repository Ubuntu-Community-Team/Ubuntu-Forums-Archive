---
title: "Firefox Flash"
date: 2006-09-19
forum: Desktop Environments
---

### Post by Randal Leavitt on 2006-09-19
I just turned on the new computer which had Ubuntu installed in the store.
I wanted to add the "Flash" plugin to the browser.
I followed the instruction at

[https://help.ubuntu.com/ubuntu/desktopguide/C/internet.html](https://help.ubuntu.com/ubuntu/desktopguide/C/internet.html)

The last step does not work.

sudo update-flashplugin

It complains about something being changed upstream.

What should I do next?

---

### Post by aysiu on 2006-09-19
I've never used the *sudo update-flashplugin* command. I just installed *flashplugin-nonfree* and then restarted Firefox.

---

### Post by gtkourounis on 2006-09-19
or you could just use automatix (or if you have a x64 you must get switchfox AND install flash through automatix)

---

### Post by elementadiobam on 2006-09-19
I installed flash with Automatix and everything goes good. I also installe the Java Runtime Environment with Automatix.

---

### Post by hw-tph on 2006-09-20
I have also had problems with flashplugin-nonfree and update-flashplugin recently. I ended up downloading the installer from Macromedia/Adobe and installing it manually just for myself (into ~/.mozilla/plugins/ ).


Håkan

---

### Post by Randal Leavitt on 2006-09-20
Hey, thanks for all the response.

Based on the first comment I went back and tried to download 

flashplugin-nonfree

again.  Previously I had not noticed that the version installed was not the latest.  I am not familiar with these downloading tools so I hope they can survive lots of mistakes as I smash along.  Anyway, it downloaded and ran, but not smoothly.  It asked me to confirm that I agreed with the license twice, which seemed excessive.  And it suffered an error before completing:

E: flashplugin-nonfree: subprocess post-installation script returned error exit status 1

So I hope someone can report this error to the appropriate level.

However, my browser can now run the Flash plugin.  This is important for me because I am building up a slide show at:

[http://tinyurl.com/hgvmg](http://tinyurl.com/hgvmg)

---

### Post by Randal Leavitt on 2006-09-21
Help!

I installed two items from the Ubuntu respositories.  The installations seemed to work OK.  However, in both cases screens popped up asking me if I want to agree with the Flash licence, and telling me that an installation failed.  It seems that something is left over from the failed Flash installation that just won't go away.

---

### Post by beerfan on 2006-09-21
I also fell victim to this foul update bug.

The update failed the first time and every subsequent time. The bigger problem is that I cannot install ANYTHING now. Trying to install any package makes this flash-plugin also install and it fails and causes everything to fail.

I tried installing automatix (never did before) since some people seem to have been able to work around the problem with it but it will not install either.

Please, someone post a fix or workaround for this silly issue.

---

### Post by rudiz on 2006-09-21
Try this

sudo sed -e 's/multiuser/defaults/' -i /var/lib/dpkg/info/flashplugin-nonfree.postinst


sudo dpkg --configure -a

---

### Post by bluefuse on 2006-09-21
uninstall those silly wannabe flash players and get is straight from ubuntu.... [http://ubuntu.mirrors.tds.net/ubuntu/pool/multiverse/f/flash-player/flashplayer-mozilla_7.0.25-0.0ubuntu1_i386.deb](http://ubuntu.mirrors.tds.net/ubuntu/pool/multiverse/f/flash-player/flashplayer-mozilla_7.0.25-0.0ubuntu1_i386.deb)

---

### Post by skymt on 2006-09-21
> **bluefuse said:**
> uninstall those silly wannabe flash players and get is straight from ubuntu.... [http://ubuntu.mirrors.tds.net/ubuntu/pool/multiverse/f/flash-player/flashplayer-mozilla_7.0.25-0.0ubuntu1_i386.deb](http://ubuntu.mirrors.tds.net/ubuntu/pool/multiverse/f/flash-player/flashplayer-mozilla_7.0.25-0.0ubuntu1_i386.deb)

The bug causing all this trouble is in the Ubuntu package...

---

### Post by Randal Leavitt on 2006-09-21
I tried the fix suggested by "rudiz", namely

sudo sed -e 's/multiuser/defaults/' -i /var/lib/dpkg/info/flashplugin-nonfree.postinst
sudo dpkg --configure -a

This seems to have solved the problem.  I still have the Flash plugin and I was able to install "gnumeric" later on with no errors.  Very good!

---

### Post by umphlette on 2006-09-21
I had some issues with it as well and decided to remove it altogether...My real concern is that that somehow messed with some other codecs or some such as I've noted that now anytime I try to burn a audio disk from mp3's I get an error that theres no plugin to handle files of type audio/mpeg.  I previously had no issues burning audio disks from mp3.  I tried reinstalling all relavant audio packages to no avail.  Anyone having same issue after this failure?

---

