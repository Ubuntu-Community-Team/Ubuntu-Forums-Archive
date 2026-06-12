---
title: "Transparent PNG"
date: 2007-11-10
forum: Desktop Effects &amp; Customization
---

### Post by Qinjuehang on 2007-11-10
I tried using a transparent PNG for my panel. I was using the Ubuntu Studio theme, so I replaced the "panel.png" with my own (made in Gimp) , and it worked perfectly, except that the transparency was gone. So I'll post 2 screenshots, 1 with the "panel.png" changed, and 2 with me setting the "panel.png" manually on the top bar(Right Click>Properties).
1.[[IMG]http://img131.imageshack.us/img131/3097/screenshotwm5.th.png[/IMG]](http://img131.imageshack.us/my.php?image=screenshotwm5.png)
2.[[IMG]http://img264.imageshack.us/img264/9963/screenshotsg7.th.png[/IMG]](http://img264.imageshack.us/my.php?image=screenshotsg7.png)
It seems replacing panel.png disables transparency, and applying the panel manually does not work on the applets.

---

### Post by Qinjuehang on 2007-11-10
*bump*

---

### Post by Qinjuehang on 2007-11-10
I found out you can change the transparency by alt-scroll. However it also makes applets, icons and such transparent. Is there a way to prevent it?

---

### Post by Naikei on 2007-11-10
[Here's a screenshot]("http://lukewh.com/images/transparent-bars.png") of the options I used for PNG in GIMP (though I tick the save background color option too), don't know if you're using different settings, and I've not tried it on my UbuntuStudio partition, but I don't see why it would be different! Hope this helps!

Naikei

---

### Post by Qinjuehang on 2007-11-11
The PNGs are correctly transparent when you view them in a image editor. Just that GTK/Metacity seems not to support it.

---

### Post by Qinjuehang on 2007-11-11
I tried your settings, they didn't work ><

---

### Post by Qinjuehang on 2007-11-12
*bump again*

---

### Post by Qinjuehang on 2007-11-13
*triple bump*

---

### Post by mcduck on 2007-11-13
How about disabling the background image in the theme completely, and then setting the image as panel background through the panel's own settings? Setting background images through GTK theme has several problems, including not being able to correctly scale the image to different panel sizes or rotate the image for vertical panels, so it could as well be that transparency doesn't work either..

So, remove the panel background from the GTK theme, and then just drag & drop the image to your panel to st it as background. Alternatively you can right-click the panel, select 'Properties' and in the Background-tab set the image you want to use.

If you wish to enable scaling and rotating of the panel background, press Alt-F2 and run 'gconf-editor'. Then browse to apps/panel/toplevels/<name of your panel>/background and enable 'rotate' and 'stretch'  (or you can use 'fit' instead of 'stretch' depending on what you need).

Edit: In case you are using Ubuntu 6.06, just with Ubuntu Studio theme, the Gnome Panel's transparency support is broken in that version of Gnome. It works again in later releases.

---

### Post by Qinjuehang on 2007-11-15
I'm using gutsy.

Thank you very much, that was exactly what I need (disabling the panel background in theme settings)

Why was I so stupid as not to think of removing the panel in the theme.

---

