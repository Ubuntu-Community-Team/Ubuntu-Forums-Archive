---
title: "Conky thing?"
date: 2007-09-02
forum: Desktop Effects &amp; Customization
---

### Post by perversevoodoo on 2007-09-02
Hi! im new in this.

I want to install the conky thing shown in this link (The info in the right?)

[http://splenetic.info/screenshots/sc...ot_blue2-1.png](http://splenetic.info/screenshots/sc...ot_blue2-1.png)

I already tried but since im new in linux it was hard for me to understand the HOWTO i where given a link to.

can anyone give me a link where there are some details? or will someone explain it?

thanks advance

---

### Post by a-converted-sparky on 2008-01-30
Im in the same boat, i was gonna try this guide:

[http://thio4linux.wordpress.com/2007/11/02/conky-on-my-gutsy/](http://thio4linux.wordpress.com/2007/11/02/conky-on-my-gutsy/)

---

### Post by justsomedude on 2008-01-30
Ok, I provide a short walkthrough:

1. Install Conky: Open a terminal and type:

```
sudo apt-get install conky
```

2. Conky is configured the following way: you create a file called *.conkyrc* in your home directory. Notice the dot at the beginning of the file name, that means it is hidden by default. You can see the file if you select *Show Hidden Files* in Nautilus.

The functions and appearance of Conky can be configured by editing this *.conkyrc* file. We have several threads about this here for example this one:

[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

Pick one configuration you like and paste the contents of the config file you choose into your *.conkyrc* file in your home directory and save it.

To start Conky  hit Alt + F2 and type 

```
conky
```

Hope this helps... :)

---

### Post by rjmdomingo2003 on 2008-01-31
Check out this thread for your basic installation & config: [http://ubuntuforums.org/showthread.php?t=205865&highlight=tint](http://ubuntuforums.org/showthread.php?t=205865&highlight=tint)

---

