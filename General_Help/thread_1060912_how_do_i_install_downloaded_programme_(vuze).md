---
title: "how do i install downloaded programme (vuze)?"
date: 2009-02-05
forum: General Help
---

### Post by Mzwo on 2009-02-05
hi,

apologies if the following question soudns somewhat daft. 

i've downloaded vuze, formerly known as azureus, from the homepage, since it doens't appear in the repos (or i'm ti thick to find it. anyways, got the zip-file, extracted it and i can run vuze by running the shell script - which, alas, is not the same as installing it. i'd quite like to though - but how?

hope you know what i mean ...

thanks,

Mzwo

ps: alternatively: does anybody know how to find vuze using synaptics?

8.04 studio 64

---

### Post by Dies on 2009-02-05
Much like the Mozilla programs, there's no real "installation".

I typically move the folder to /opt/ and link the script to /usr/bin/ then add an entry to my menu.

BTW if you open Synaptic and search for Azureus or Vuze it comes right up, of course it's not up to date, but it is there.

---

### Post by bff7755a on 2009-02-05
> **Mzwo said:**
> hi,

apologies if the following question soudns somewhat daft. 

i've downloaded vuze, formerly known as azureus, from the homepage, since it doens't appear in the repos (or i'm ti thick to find it. anyways, got the zip-file, extracted it and i can run vuze by running the shell script - which, alas, is not the same as installing it. i'd quite like to though - but how?

hope you know what i mean ...

thanks,

Mzwo

ps: alternatively: does anybody know how to find vuze using synaptics?

8.04 studio 64

It's interesting, but I found it in packages:

```
[desktop][mutex]~> apt-cache -n search vuze
vuze - Multimedia BitTorrent client
```

Are you mean this program?

---

### Post by Mzwo on 2009-02-05
> **Dies said:**
> Much like the Mozilla programs, there's no real "installation".

I typically move the folder to /opt/ and link the script to /usr/bin/ then add an entry to my menu.



that sounds pretty much like what i want to do - could you run that past me step by step? sorry, still struggling with linux ... 


i can't find vuze in any repos, btw...

cheers,

Mzwo

---

### Post by scouser73 on 2009-02-05
Download the (.deb) file from here: [http://www.getdeb.net/search.php?keywords=vuze]("http://www.getdeb.net/search.php?keywords=vuze")

Alternatively go to the Synaptic Package Manager, in the search box, type Vuze and it will appear in the search results.

To install it via the Synaptic Package Manager you'll need to select it, and then click apply which will then install the program. From there it's just a matter of setting up the folders where you want the torrents to be downloaded and so forth.

---

### Post by redilyn on 2009-02-05
Have you enabled each repo? Main - Universe - Multiverse?

---

### Post by Mzwo on 2009-02-05
thanks, that did it.

i do have all repos enabled, yet synaptic wouldn't find vuze. strange?

anyhow - case closed. many thanks.

Mzwo

---

### Post by Dies on 2009-02-05
> **Mzwo said:**
> that sounds pretty much like what i want to do - could you run that past me step by step? sorry, still struggling with linux ... 


Sure. Assuming the Vuze folder is sitting on your desktop open a terminal and do
```

sudo mv vuze /opt/
gksudo gedit /usr/bin/vuze
```

you can substitute any text editor for gedit, add the following to the file you just created

```
#!/bin/bash
cd /opt/vuze/
./vuze
```

save the file and make it executable

```
sudo chmod +x /usr/bin/vuze
```

then make your menu entry
```

gksudo gedit /usr/share/applications/vuze.desktop
```

add this to the file you just created

```
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=/opt/vuze/vuze.png
Name[en_US]=Vuze
Exec=/usr/bin/vuze
Name=Vuze
Icon=/opt/vuze/vuze.png
Categories=Application;Network;
```

Save the file and you should be done. Vuze should show up in your menu, it may take a few seconds, if it doesn't, log out and back in then check again.

---

### Post by Mzwo on 2009-02-05
thanks!

i'll file that for future reference.

Mzwo

---

