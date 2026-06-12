---
title: "why my cairo-dock is 2D not 3D ???"
date: 2008-03-19
forum: Desktop Effects &amp; Customization
---

### Post by linuxnewbie999 on 2008-03-19
I install cairo-dock but it is defalut to 2D and there is no 3D option only set to default.... How do I make it 3D ???

---

### Post by FuturePilot on 2008-03-19
I'm not quite sure I understand. What exactly do you mean by 3D? Perhaps a screenshot would help.

---

### Post by linuxnewbie999 on 2008-03-19
under cairo-dock configure->personnalisation->views  there is only default option which means i cannot choose other than the default 2D. 


here is my screenshot, the dock's background image is not in like in the Mac OS(Not 2D??).....
[IMG]http://i144.photobucket.com/albums/r176/4d10s/Screenshot-1.png[/IMG]

---

### Post by FuturePilot on 2008-03-19
I've never used cairo-dock but I've heard there's a plugin you need to enable for the 3D effect.

---

### Post by linuxnewbie999 on 2008-03-19
Hmmm ic, anyone know what is the plugin??

---

### Post by Flynn555 on 2008-03-28
here is the plug-in you need...
[http://packman.links2linux.de/download/cairo-dock-plugins/144119/cairo-dock-rendering-20080318-3.pm.0.i586.rpm]("http://packman.links2linux.de/download/cairo-dock-plugins/144119/cairo-dock-rendering-20080318-3.pm.0.i586.rpm")

to install...

navigate to the folder in terminal and type...=
autoreconf -isvf && ./configure --prefix=/usr/local && make

restart your cairo dock,go to the configuartion menu,  then select rendering from the applets. then check rendering.  restart cairo again. then go to the views tab (from the configuration menu) and select your view.

i think it has 3d plane, carosel, rainbow and a few others.

---

### Post by linuxnewbie999 on 2008-03-29
That's rpm file which is not supported in Ubuntu.  I cann't install it.

---

### Post by Flynn555 on 2008-03-29
sorry..this one should work. (archived it myself)  ;)

[http://www.megaupload.com/?d=HWHM6DDU]("http://www.megaupload.com/?d=HWHM6DDU")

contains the plugin folder for the rendering plugin...just extract to your desktop and follow the instructions above :)

---

### Post by linuxnewbie999 on 2008-03-29
Not working :(  . I have done the steps but when i click Applets->Preferences there's nothing.....   Or it must run with 3D card???? I don't have 3D card in my laptop.

---

### Post by Flynn555 on 2008-03-29
hummm...well im only running a 128 meg card in my desktop right now. so i dont know why its not working for you...  it sounds like you are having the same problem as i was?  im taking it you cant add any applets (like trash, clock, ect?) did you install it using the deb packages from berlinOS? 

what i had to end up doing was installing manually.

ok this archive has the cairo-dock, all the plugins, and themes.
[http://www.uploading.com/files/YLPGTPLA/cairo-dock.zip.html]("http://www.uploading.com/files/YLPGTPLA/cairo-dock.zip.html")
run these commands...
   
   autoreconf -isvf && ./configure --prefix=/usr/local && make

   sudo make install

 in the inclosed folders
cairo-dock>trunk>cairo-dock
cairo-dock>trunk>themes


note:you'll have to install all the plugins individually i think. 
so...
cairo-dock>trunk>plugins>plugin you want

hope this works for you man.  i know it took me forever to get it to work right.
also you'll have a shortcut to the dock in Apps>SystemTools>Cairo Dock nice huh?

---

