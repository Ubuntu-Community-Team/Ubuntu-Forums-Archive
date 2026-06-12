---
title: "very large text/graphic on login window"
date: 2008-01-28
forum: Desktop Effects &amp; Customization
---

### Post by taydu on 2008-01-28
I don't know what happen but after install and boot to Kubuntu the login screen is really mess up, The text and images is really big i can't hardly see the login name when i type it in the text box. 

After login everything look fine the the login screen really bug me, please help me fix this problem

thanks

---

### Post by pecatto on 2008-04-16
Can you switch between different screen resolutions?

---

### Post by Zorael on 2008-04-16
Wait. Did the theme change from the nicey blue theme into something very huge and ugly? If so, I've had it happen and I sort of know what to do.

edit: Do note that this thing I'm speaking of does not have to do with your screen resolution, just the theme and the dpi setting.

If that's what you're experiencing, you want to edit your **/etc/kde3/kdm/kdmrc** file, with superuser permissions.
```
$ gksu gedit /etc/kde3/kdm/kdmrc
```

Scroll down to the section beginning with [X-*-Greeter] and find the following line.
```
Theme=@@@@@tobereplacedblahblah@@@@@@
```
Replace it with the following.
```
Theme=/usr/share/apps/kdm/themes/kubuntu
```


Then search the file for "ServerArgs", and add "-dpi 96" to the end of that line, making it look something like this.
```
ServerArgsLocal=-nolisten tcp -dpi 96
```

Save, restart X. (Ctrl+Alt+Backspace)

That'll get you your theme and dpi setting back.

---

