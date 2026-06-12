---
title: "firefox 1.0.6"
date: 2005-07-19
forum: Desktop Environments
---

### Post by vempire on 2005-07-19
como puedo bajar firefox 1.0.6 en paquete .deb para kubuntu?? alguna idea?

---

### Post by bored2k on 2005-07-19
[QUOTE=vempire]como puedo bajar firefox 1.0.6 en paquete .deb para kubuntu?? alguna idea?[/QUOTE]
 Esto es un foro exclusivamente en Inglés.

He wants to knwo how to download Firefox .6 for Kubuntu (in .deb package..) ? Any Ideas ?

---

### Post by wellery on 2005-07-19
More information on this can be viewed here:

[http://www.ubuntuforums.org/showthread.php?t=50398](http://www.ubuntuforums.org/showthread.php?t=50398)

---

### Post by Seth on 2005-07-19
[QUOTE=wellery]i don't know that you can get in in deb format but you can download it from:

[http://download.mozilla.org/?product=firefox-1.0.6&os=linux&lang=en-US](httphttp://download.mozilla.org/?product=firefox-1.0.6&os=linux&lang=en-US) 


Open a terminal (right click on the desktop and select 'open terminal') and type the following:

```
$ cd Desktop 
$ tar xzvf firefox-1.0.5.installer.tar.gz [You'll see the files unzipping] 
$ cd firefox-installer 
$ mkdir ~/apps/firefox1.05 
$ ./firefox-installer
```


And then you'll see a graphical Firefox install program. You'll want to change the default install directory though, to the one you created. In this example, apps/firefox1.05 in your home directory.

The installer will put all the files there. To run the program, you'll want to right click on the panel and select 'Add custom launcher', then browse for the command and locate 'firefox' in the new folder you created. There should be an icon for the program in there, too.

And you're done! To uninstall the program, just delete that folder.[/QUOTE]
 It'll be backported for Hoary in a week or so.

---

### Post by nrayever on 2005-07-20
i hope that really happend seth. but i'n still wondering why there aren't backports for amd64??

---

### Post by peter07 on 2005-07-20
[QUOTE=wellery]i don't know that you can get in in deb format but you can download it from:

[http://download.mozilla.org/?product=firefox-1.0.6&os=linux&lang=en-US](httphttp://download.mozilla.org/?product=firefox-1.0.6&os=linux&lang=en-US) 


Open a terminal (right click on the desktop and select 'open terminal') and type the following:

```
$ cd Desktop 
$ tar xzvf firefox-1.0.5.installer.tar.gz [You'll see the files unzipping] 
$ cd firefox-installer 
$ mkdir ~/apps/firefox1.05 
$ ./firefox-installer
```


And then you'll see a graphical Firefox install program. You'll want to change the default install directory though, to the one you created. In this example, apps/firefox1.05 in your home directory.

The installer will put all the files there. To run the program, you'll want to right click on the panel and select 'Add custom launcher', then browse for the command and locate 'firefox' in the new folder you created. There should be an icon for the program in there, too.

And you're done! To uninstall the program, just delete that folder.[/QUOTE]
 I'm not using backports.

Is firefox in standard Ubuntu repositories ( form ubuntu.com ) safe ??

---

### Post by wellery on 2005-07-20
The one in the standard is version 1.04 which is pretty safe since there is no record of the current flaws in 1.05 being exploited. It should be soon when the latest patch gets uploaded.

---

### Post by daigorobr on 2005-07-20
I really really really recommend installing Deer Park alpha 1.1 as an user in Kubuntu. It's sharp as a diamond and really doesn't crash - no matter what.

Ps. - just don't forget to symlink the plugins of your old browser (be it Firefox, Konqueror, Opera or Mozilla) to your Deer Park plugins directory.

---

