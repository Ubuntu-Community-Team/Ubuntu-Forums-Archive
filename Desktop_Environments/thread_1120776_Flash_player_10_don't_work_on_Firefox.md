---
title: "Flash player 10 don't work on Firefox"
date: 2009-04-09
forum: Desktop Environments
---

### Post by D@RKKIN6 on 2009-04-09
Hi

I've installed flash 10 using 'Synaptic ...', because when I try to install it from Adobe's website it gives a bug so I can't install it. 
When I go to youtube with Firefox the Video opens, but freezes, then I open SeaMonkey browser and it opens the video, 
but some sites like Facebook, ... don't shows all the contents of the site because it's "an old version of Mozilla Firefox, please upgrade it to the last version". 
I try the Arora browser but it doesn't support Flash at all. I've installed ie4Linux, windows Internet Explorer for Linux, 
but it's to slow and it's also a Beta version, so I deleted it.
Do I need to try Opera? 
But some people are saying that it doesn't support Flash correctly.
Can someone give me an advice with this problem?

Thank you

---

### Post by reahjw6 on 2009-04-09
Did you install falshplugin-nonfree from synaptic.

---

### Post by nathanpc on 2009-04-09
You have tried to install flash player from sources.

Nathan Paulino Campos

---

### Post by StuartN on 2009-04-09
I had this problem and went in a loop of the Flash website [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/) telling me I had no Flash and directing me to a download, which I was then told was already installed. Installing flashplugin-nonfree in Synaptic worked.

---

### Post by graysky on 2009-04-09
For Intrepid-amd64 (you might not be using this are you?) installation is simple:

1) download flash10 [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)
2) $  sudo cp libflashplayer.so /usr/lib/mozilla/plugins/

---

### Post by D@RKKIN6 on 2009-04-09
Yes I installed flashplugin-nonfree in Synaptic.
Because when I try to install from Adobe website,
I choose .deb for Ubuntu 8.04+, when the installer starts I get this error
[COLOR="Red"]Error: Wrong architecture 'i386'[/COLOR]
So I can't press to "Install Package" button.

> For Intrepid-amd64 (you might not be using this are you?) installation is simple:

1) download flash10 [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)
2) $ sudo cp libflashplayer.so /usr/lib/mozilla/plugins/ 

I don't know how to discover if I'm using Intrepid-amd64 or not?
And I installed the Tar file, untarred it then used the 2) step, but it's the same, Firefox freezes the flash contents.

---

### Post by benerivo on 2009-04-09
> **D@RKKIN6 said:**
> I don't know how to discover if I'm using Intrepid-amd64 or not?

Use this command```
uname -a
```To get 64 bit flash working i think you need to copy that downloaded [libflashplayer.so]("http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz") file to 
/usr/lib/firefox-addons/plugins

---

### Post by dokdoom on 2009-04-09
You can also copy the libflashplayer.so to .mozilla/plugins

note: you have to create the /plugins folder

---

### Post by graysky on 2009-04-10
> **dokdoom said:**
> You can also copy the libflashplayer.so to .mozilla/plugins

note: you have to create the /plugins folder

Is there an echo in here :)

> **graysky said:**
> For Intrepid-amd64 (you might not be using this are you?) installation is simple:

1) download flash10 [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)
2) $  sudo cp libflashplayer.so /usr/lib/mozilla/plugins/

---

### Post by adamlau on 2009-04-10
Download and extract libflashplayer.so from:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

```
sudo mkdir /usr/lib/mozilla/plugins/; cp libflashplayer.so /usr/lib/mozilla/plugins/
```

---

### Post by shonecse on 2011-06-29
I'm having same problem, used synaptics to install flash plugin and also tryed adobe web site and installed with no problems, but any flash content on youtube is slow even when the progress bar at the bottom has finished loading??????????????

---

