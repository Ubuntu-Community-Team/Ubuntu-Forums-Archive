---
title: "Ati composite extension problem on feisty"
date: 2007-06-22
forum: Desktop Effects &amp; Customization
---

### Post by Bellochka on 2007-06-22
I installed ati driver using prospectus from this page 
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide) (Method 1)

then I installed beryl , when I attempted to run beryl from terminal, it'd given me composite extension error.than I realised this line in driver guide 

```
In Ubuntu Feisty the Composite extension is enabled by default, however, fglrx does not yet support Composite with DRI. In order to disable Composite you have to edit the xorg.conf file:

Section "Extensions"
        Option  "Composite" "Disable"
EndSection

I igroned it andSection "ServerFlags"
        Option  "AIGLX" "off"
EndSection
```


I igroned it and changed ''Disable'' to ''Enable'' & ''off'' to ''on'' . passed composite extension error . But now it gives me ''non power of two textures missing'' error ;

[IMG]http://img451.imageshack.us/img451/543/untitledtd4.jpg[/IMG]

If fglrx doesn't support ,how could ati users run beryl ? 

Is anyone know what should I do to get it worked ?

---

### Post by jtraub on 2007-06-23
To run Beryl with fglrx you should use XGL.
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

---

