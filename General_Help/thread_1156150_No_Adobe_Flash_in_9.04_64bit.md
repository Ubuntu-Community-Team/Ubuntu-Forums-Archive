---
title: "No Adobe Flash in 9.04 64bit"
date: 2009-05-11
forum: General Help
---

### Post by cybrsaylr on 2009-05-11
Just installed 9.04 64bit in my Toshiba AMD laptop.

All went well, install took 15 minutes.
Can't get flash working. It worked fine before when running 8.10 32bit version on this laptop.

None of the options listed on the Adobe site work with the 64bit version.

What do you have to do to get Flash to work?

---

### Post by alexandari on 2009-05-11
Use firefox. There was a beta release of the 64 bit flash on konqueror but it still doesn`t work well (I dont know if it`s not beta anymore).

---

### Post by drs305 on 2009-05-11
[http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

Don't install or uninstall old flash:
```

sudo apt-get uninstall flashplugin-nonfree

```

Download the Flash Alpha .tar.gz file, extract the libflashplayer.so file onto your Desktop, then:
```

mkdir ~/.mozilla/plugins && cp $HOME/Desktop/libflashplayer.so ~/.mozilla/plugins

```

This is a 64-bit alpha release that has been around since February and works really well in Firefox.

---

### Post by Legace on 2009-05-11
Just do
```
sudo apt-get install flashplugin-installer
```

---

### Post by cybrsaylr on 2009-05-11
> **Legace said:**
> Just do
```
sudo apt-get install flashplugin-installer
```

Legace,
Thanks that worked with Firefox after a reboot.
However it seems the video quality is not as good as it was with 8.10 32bit Intrepid. 

Opera browser however still won't play flash video but on some clips the sound does play though. Any idea how to get Opera playing Flash?

Opera is my fav browser because it's faster than Firefox

---

### Post by sloggerkhan on 2009-05-11
There's a beta of 64 bit flash for linux from adobe, search for it.
Otherwise, install from the repos, there's a package for adobe flash that works fine on 64 bit, using a wrapper to the 32 bit plugin.

---

### Post by cybrsaylr on 2009-05-11
> **sloggerkhan said:**
> There's a beta of 64 bit flash for linux from adobe, search for it.
Otherwise, install from the repos, there's a package for adobe flash that works fine on 64 bit, using a wrapper to the 32 bit plugin.

sloggerkhan,
There were 2 packages there.
One was already installed, I put in the other, then rebooted.

Now Opera plays the audio from all the UTube clips tested so far but still no video.
FF plays both audio and video.

---

### Post by cybrsaylr on 2009-05-11
OK, I just tried a couple other sites and the audio and video works with Opera. Not sure why Opera is not working on UTube now. UTube ran fine video with 8.10 32bit Intrepid on this laptop.

---

### Post by baseface on 2009-05-11
all you have to do to get it working in 9.04 is download the 32bit flashpayer and put it in ~/.mozilla/plugins

---

### Post by fooman on 2009-05-11
> **baseface said:**
> all you have to do to get it working in 9.04 is download the 32bit flashpayer and put it in ~/.mozilla/plugins

well,  if your using *64bit ubuntu* and your going to download a flash plugin to place in ~/.mozilla/plugins....then why not get the *64bit plugin*?  

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

download, extract, copy newly extracted libflashplayer.so to ~/.mozilla/plugins

works great on my 64bit jaunty install.  :)

** EDIT:  first,  be sure to open synaptic,  search for "flash" and uninstall any flash/gnash and libswfdec items that are already installed. **

---

### Post by cybrsaylr on 2009-05-11
baseface,
Do you have a link?

---

### Post by Legace on 2009-05-11
> **cybrsaylr said:**
> baseface,
Do you have a link?

Guess he means this: [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)

---

