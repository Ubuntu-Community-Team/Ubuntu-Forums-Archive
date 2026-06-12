---
title: "Runescape Native Client - Linux How To"
date: 2012-04-03
forum: Gaming &amp; Leisure
---

### Post by magnavoid on 2012-04-03
For a long time I've had issues playing Runescape on linux. Mostly sound and or full screen support. This is resolved by using the jagex runescape native client. But wait?! Isnt the Runescape native client windows or mac-os only? Well not anymore! Use the following to download extract and create a executable jar file for runescape, without having to worry about having your account being hacked or stolen.


First you need to install p7zip, you can do this easily with the following: ```
sudo apt-get install p7zip-full
```

Now we should be able to get started quickly. The remaining is easy and can be completed in just a few minutes.
```
mkdir -p ~/runescape/icon
cd ~/runescape/
wget http://www.runescape.com/downloads/runescape.msi
7z x -oextracted runescape.msi
cp ~/runescape/extracted/JagexAppletViewerJarFile.* jagexappletviewer.jar
cp ~/runescape/extracted/JagexAppletViewerPngFile ~/runescape/icon/jagexappletviewer.png

```

Now at this point we should have the jagexappletviewer.jar and the icon in the proper places. We can either clean up the extracted files or we can leave them. To clean it all up run this command in your terminal:
```
rm -r extracted/
```

Now you're probably thinking ok so what do I do with this stuff now? Heres what you're needing:

```
echo 'cd ~/runescape/ && padsp java -cp jagexappletviewer.jar -Dsun.java2d.noddraw=true -Dcom.jagex.config=http://www.runescape.com/k=3/l=0/jav_config.ws -Xmx256M -Xms128M -Dsun.java3d.opengl=true -Dsun.java2d.opengl=True -Xss1m -Xdebug jagexappletviewer /runescape/icon' > ~/runescape/runescape_launcher.sh
```

Then do this:
```
chmod +x runescape_launcher.sh
```

And this will run everything:
```
./runescape_launcher.sh
```


Hope that this is helpful for at least someone out there.

---

### Post by magnavoid on 2012-04-03
Advanced:

People who are interested in increasing the amount of memory that runescape can use should change the following variables in the runescape_launcher.sh file.

Beginning amount of memory java will allocate to runescape:
```
-Xms128M
```

Maxumum amount of memory java will be allowed to use for runescape:
```
-Xmx256M
```

---

### Post by willat8 on 2012-06-09
Thank you, this was very helpful!

---

### Post by samiscool30 on 2012-06-23
Thanks really helped me!

---

### Post by samiscool30 on 2012-06-23
Also which steps do i have to repeat if i want to play again?  Or do i have to repeat the whole thing?

---

### Post by doorknob60 on 2012-06-23
> **samiscool30 said:**
> Also which steps do i have to repeat if i want to play again?  Or do i have to repeat the whole thing?

Just run the script by double clicking or creating a launcher to runescape_launcher.sh

---

### Post by Kjarun on 2012-08-18
twitch@twitch:~/runescape$ 7z x -oextracted runescape.msi

7-Zip [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,2 CPUs)

Processing archive: runescape.msi

Error: Can not open file as archive

So how do I do it?

---

### Post by HikariKnight on 2012-08-20
you could just use one of the methods provided in the official runescape wiki

[http://services.runescape.com/m=rswiki/en/Linux_Native_Clients](http://services.runescape.com/m=rswiki/en/Linux_Native_Clients)

the RSU client i wrote back in october 2011 was designed to make the above process easier and more seamless and there is a ppa for it too.

you can find the instructions on webupd8
[http://www.webupd8.org/2012/07/how-to-install-runescape-linux-game.html](http://www.webupd8.org/2012/07/how-to-install-runescape-linux-game.html)

---

