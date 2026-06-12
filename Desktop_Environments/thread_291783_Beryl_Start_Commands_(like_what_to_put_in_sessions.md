---
title: "Beryl Start Commands (like what to put in sessions)"
date: 2006-11-02
forum: Desktop Environments
---

### Post by BOBSONATOR on 2006-11-02
Hey guys, does anyone know the commands to start beryl and the window boarder manager (emerald) and others nessesary?

I know one is 
```

Beryl
```

But what are the others?

thanks!

---

### Post by d3v1ant_0n3 on 2006-11-02
For GNOME, the entry I have in sessions is 

beryl-manager

Which starts up Beryl and emerald for me.

---

### Post by BOBSONATOR on 2006-11-02
Thank you very much.

---

### Post by napsilan on 2006-11-03
Another question regarding Beryl startup.  Whenever I add ¨Beryl¨ or ¨beryl-manager¨ to the startup sessions tab, they automatically get removed as soon as I close the sessions window.  I can start beryl using the terminal, and everything appears to be working perfectly, but I cannot get it to start automatically.  This results usually in no window manager being active when I log in, so I either have to manually fire up metacity or beryl.  Do I have to add another session besides ¨Default¨?

Edit:  Using the beta nvidia drivers, so I don´t think I have xgl installed (xserver-xgl isn´t marked in synaptic, and I used [http://www.ubuntuforums.org/showthread.php?t=263851)](http://www.ubuntuforums.org/showthread.php?t=263851)).  Can I still use [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL) for information on editting config files, or are the XGL and AIGLX methods completely different?

more edit: Using Edgy x64

even more edit: After poking around the above beryl xgl site, I´m going to try to manually add a beryl-manager startup file in ~/.config/autostart, named beryl-manager.desktop and containing 
```

[Desktop Entry]
Name=beryl-manager.desktop
Encoding=UTF-8
Version=0.1.1
Exec=beryl-manager
X-GNOME-Autostart-enabled=true

```

I´ll report soon on whether this works.  I´m modeling it exactly like the beagle startup entry in the same folder.  You need sudo do edit anything in that folder, so I assume that might be why the gnome sessions manager couldn´t write to it.

Final Edit:  VICTORY!  adding the above file to ~/.config/autostart worked.  now just to figure out how to do it for kde....

---

### Post by gldvxx on 2007-03-10
i was having the same problem!  this solution worked for me. don't forget to make the script executable: "sudo chmod -x beryl-manager.desktop".

---

