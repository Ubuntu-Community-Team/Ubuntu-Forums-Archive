---
title: "Steam won't run Ubuntu 16.04.1 LTS"
date: 2016-09-20
forum: Gaming &amp; Leisure
---

### Post by fistofmetal226 on 2016-09-20
Hey there. i've been trying to get Steam to launch since yesterday (i'm not sure if this was caused by the recent update (20/9/16 for me - Australia) but it seems to have only just happened afterwards. i don't recall doing anything destructive that might harm steams running capabilities or it's libraries...?)
and i'm getting this error:

Running Steam on ubuntu 16.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(0)
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast

You may think: "there are plenty of other posts about this. go look at them."
well, i've searched through as many as i dared possible. I have a massive headache from this at the moment and i can't seem too fix it the way everyone else seems to fix it.
Before this error i actually had a different error which was saying:

You are missing the following 32-bit libraries, and Steam may not run:
libSDL2-2.0.so.0
libXtst.so.6
libgtk-x11-2.0.so.0
libgdk_pixbuf-2.0.so.0

before you say why didn't you try install or reinstall those libraries? i tried. and i tried multiple other fixes for this and i ended up deleting '/usr/share/steam & /.steam' files and now i get the 'swrast' issue and steam won't even attempt to run.
I'm running on a DELL XPS 17 Laptop and i run the nvidia GT550m graphics card. 
i've tried reinstalling my nvidia drivers and purging them, updating, reinstalling steam, reinstalling mesa drivers, installing different nvidia drivers (through Software & Updates)
I'm just at a loss, i don't know where to go from here.
any help would be greatly appreciated. otherwise i'm going to have to reinstall Ubuntu one day or forget about Steam..

cheers

---

### Post by oldrocker99 on 2016-09-21
Did you install Steam from the repositories?```
sudo apt install steam
```

Installing this way pulls in the dependencies automatically. If you did install this way, your problem is more serious.

---

### Post by Lance321 on 2016-09-21
Your not alone. Its hasn't been running on Ubuntu 16.04 for me with my initial installation attempts either.

I have successfully installed it and it runs beautifully on three separate machines with Ubuntu 16.04. But each machine ran into library errors, and driver issues and needed resolved in different ways. Your error sounds similar to my last one. I will have to look when I get home to see what I did last time.

Btw, did you install originally from Steams site using their deb file? Or did you install from a repository in the command line?

---

### Post by Lance321 on 2016-09-21
Ok not sure if you got it working or not. I didn't have much trouble on two desktops with 16.04 w/ Nvidia cards after a few config changes, but on a laptop with AMD drivers I did.

I initially tried installing via the deb file from the website and that failed due to failed dependencies using Ubuntu's graphical deb installation.

I then tried the repository, but got an error similar to yours.

Eventually this got it working for me. And I honestly have no idea why renaming these files did it but oh well.

> 
cd $HOME/.steam/steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu
mv libstdc++.so.6 libstdc++.so.6.bak
cd $HOME/.steam/steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu
mv libstdc++.so.6 libstdc++.so.6.bak


---

### Post by fistofmetal226 on 2016-09-21
I searched through my history and dug into my downloads folder to find that, no i originally did not install from the steam site.
after i posted this yesterday i found the pinned post and read that it causes a multitude of unfixable problems for 16.04, which i'll keep in mind.
but i have only ever installed via ```
sudo apt-get install steam
```

---

### Post by fistofmetal226 on 2016-09-22
> **pete-wilkins321 said:**
> Ok not sure if you got it working or not. I didn't have much trouble on two desktops with 16.04 w/ Nvidia cards after a few config changes, but on a laptop with AMD drivers I did.

I initially tried installing via the deb file from the website and that failed due to failed dependencies using Ubuntu's graphical deb installation.

I then tried the repository, but got an error similar to yours.

Eventually this got it working for me. And I honestly have no idea why renaming these files did it but oh well.

I tried the first code, it worked, but no result. and i have an nVidia card so i don't even have that amd directory.
cheers for the help, though.

---

