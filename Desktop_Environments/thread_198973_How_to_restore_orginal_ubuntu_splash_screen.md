---
title: "How to restore orginal ubuntu splash screen?"
date: 2006-06-18
forum: Desktop Environments
---

### Post by Owdy on 2006-06-18
[FONT=Arial]How can i restore orginal ubuntu splash screen? I mean that screen what appears when Gnome starts.[/FONT]

---

### Post by Kilz on 2006-06-18
[QUOTE=Owdy][FONT=Arial]How can i restore orginal ubuntu splash screen? I mean that screen what appears when Gnome starts.[/FONT][/QUOTE]
If you are refering to the screen where you type in your username and password. Go to System, then Administration, then Login Window. Click the circle next to the one you want and click close.

---

### Post by Owdy on 2006-06-18
[quote=Kilz]If you are refering to the screen where you type in your username and password. Go to System, then Administration, then Login Window. Click the circle next to the one you want and click close.[/quote] No i mean that image what shows when desktop loads.

---

### Post by aysiu on 2006-06-18
Here it is.

Put it in /usr/share/pixmaps/splash

Make sure it's called ubuntu-splash.png

---

### Post by Perfect Storm on 2006-06-18
or use Splash Screen chooser:

[http://ubuntuforums.org/showthread.php?t=77694](http://ubuntuforums.org/showthread.php?t=77694)

---

### Post by aysiu on 2006-06-18
You may also be able to modify the default location specified in this file: /var/lib/gconf/debian.defaults/%gconf-tree.xml

---

### Post by Owdy on 2006-06-18
[quote=aysiu]Here it is.

Put it in /usr/share/pixmaps/splash

Make sure it's called ubuntu-splash.png[/quote] It is there. But i have used that chooser app and it wants to use those images. :D

---

### Post by aysiu on 2006-06-18
[QUOTE=Owdy]It is there. But i have used that chooser app and it wants to use those images. :D[/QUOTE]
You're saying you can't have the splash screen manager pick /usr/share/pixmaps/splash/ubuntu-splash.png?

Appears to work fine to me.

Can you post the output of this command? ```
cat ~/.gconf/apps/gnome-session/options/%gconf.xml
```

---

### Post by Perfect Storm on 2006-06-18
OT: aysiu, the theme you use, it looks like GT4 but that doesn't have round buttons?

---

### Post by Owdy on 2006-06-18
[quote=aysiu]You're saying you can't have the splash screen manager pick /usr/share/pixmaps/splash/ubuntu-splash.png?

[/quote] I can use it, but i dont want to use it. Lets say Ubuntu updates and that image are updated also. I dont get that new image because i use that manager. I want stop using it and use defaults in this.



edit: I got it. Thanks for help!

---

### Post by aysiu on 2006-06-18
[QUOTE=Owdy]I can use it, but i dont want to use it. Lets say Ubuntu updates and that image are updated also. I dont get that new image because i use that manager. I want stop using it and use defaults in this.

edit: I got it. Thanks for help![/QUOTE] How did you get it? Can you share what your solution was?

[QUOTE=Artificial Intelligence]OT: aysiu, the theme you use, it looks like GT4 but that doesn't have round buttons?[/QUOTE] It's Mac OS X Controls.

---

### Post by Perfect Storm on 2006-06-18
Thanks I'll check it out.

---

### Post by Owdy on 2006-06-18
[quote=aysiu]How did you get it? Can you share what your solution was?

[/quote] Just linked that default image to that application. Just like you sayd :)

---

### Post by dspivey on 2006-06-21
the original question is what drew me to this posting.  i also want to know how to get the original ubuntu splash screens at startup.

when you first boot ubuntu and it shows the boot processes that are occurring, there is an orange/red ubuntu logo that is displayed.  after i added kubuntu to my system, that logo is now the blue kubuntu logo.  how do i get it back to the original ubuntu logo?

---

### Post by dspivey on 2006-06-22
found the answer here:

[http://www.ubuntuforums.org/showpost.php?p=1104903&postcount=6](http://www.ubuntuforums.org/showpost.php?p=1104903&postcount=6)

---

### Post by rykel on 2006-07-06
[QUOTE=aysiu]Here it is.

Put it in /usr/share/pixmaps/splash

Make sure it's called ubuntu-splash.png[/QUOTE]

Hi aysius,

My GNOME Splash Screen Manager keeps crashing and is unuseable, while my /usr/share/pixmaps/splash folder contains 3 different PNG files, with one of them being the original Ubuntu Splash Screen...

Is there a command that I can use to restore the Splash Screen to the original Ubuntu one?

btw, it seems like many people here are not aware that *usplash* and *splash screen* are 2 different matters...

---

### Post by pedro_cesar on 2007-11-24
I have used the splash screen and it shows correctly, but the icons in it won't show, I modified the */var/lib/gconf/debian.defaults/%gconf-tree.xml* and ended  up with this -fragment-: ```

<dir name="gnome-session">
  <dir name="options">
    <entry name="show_splash_screen" mtime="1195737140" type="bool" value="true">
    </entry>
    <entry name="splash_image" mtime="1195737140" type="string">
      <stringvalue>/usr/share/pixmaps/splash/ubuntu-splash.png</stringvalue>
    </entry>
  </dir>
</dir>
```

Are there aditional steps to make the icons show?
I also want to recover the splash screen that shows when Ubuntu is booting up.

---

### Post by Perfect Storm on 2007-11-24
I'm closing this thread as it's old as dust - please check the date of a thread before replying as the info is outdated.

---

