---
title: "emerald themes"
date: 2010-11-24
forum: Desktop Environments
---

### Post by wakkana12 on 2010-11-24
I got emerald and compiz installed and downloaded the themes of emerald correctly i also issued the command to use emerald as a window decorator but the problem is that the emerald theme has a transparent window but when i apply it on my machine it still uses the theme i selected on System > Preferences > Apperance. i wanna use the transparent window on the emerald theme is there something wrong with my configuration?

---

### Post by Frogs Hair on 2010-11-24
Hello and Welcome

You stated you downloaded the themes , did you import them into the Emerald Theme Manager from the downloads folder ? , you didn't mention that. What command did you use to activate Emerald ?

---

### Post by wakkana12 on 2010-11-24
thanks for the reply.. yeah i've imported it to emerald and it displays on the list of themes. i issued this comand to replace my window decoration ```
emerald --replace
```.

---

### Post by Frogs Hair on 2010-11-24
> **wakkana12 said:**
> thanks for the reply.. yeah i've imported it to emerald and it displays on the list of themes. i issued this comand to replace my window decoration ```
emerald --replace
```.

It looks like you have installed everything correctly. What graphics card and driver are you using ? and are your desktop effects enabled ? Also check Compiz and make sure window decoration is enabled.

---

### Post by VastOne on 2010-11-24
> **wakkana12 said:**
> thanks for the reply.. yeah i've imported it to emerald and it displays on the list of themes. i issued this comand to replace my window decoration ```
emerald --replace
```.

Just to be sure, you did go into Emerald Manager and select the one you wanted, correct?  

Sorry to suggest something so simple but it is something I have missed in the past

---

### Post by wakkana12 on 2010-11-24
> **VastOne said:**
> Just to be sure, you did go into Emerald Manager and select the one you wanted, correct?  

Sorry to suggest something so simple but it is something I have missed in the past


yeah i have.. hmmm.. is emerald only for borders and title bar of the window?

---

### Post by Helkaluin on 2010-11-25
Emerald is a window decorator. So yes, it is responsible only for your borders and title bar.

---

### Post by wakkana12 on 2010-11-25
sorry for the double post.. but like this theme [http://gnome-look.org/content/show.php/ShinyIce?content=13328]("http://gnome-look.org/content/show.php/ShinyIce?content=133288")
the screen shot from the second image has a translucent window.. when i applied it to mine it doesn't.. i still got the gnome themes..

---

### Post by VastOne on 2010-11-25
> **wakkana12 said:**
> sorry for the double post.. but like this theme [http://gnome-look.org/content/show.php/ShinyIce?content=13328]("http://gnome-look.org/content/show.php/ShinyIce?content=133288")
the screen shot from the second image has a translucent window.. when i applied it to mine it doesn't.. i still got the gnome themes..

I would ask the author there how he came up with that.  It was posted there in the last month or so, I would think you should get an answer.

---

### Post by Helkaluin on 2010-11-25
> **wakkana12 said:**
> sorry for the double post.. but like this theme [http://gnome-look.org/content/show.php/ShinyIce?content=13328]("http://gnome-look.org/content/show.php/ShinyIce?content=133288")
the screen shot from the second image has a translucent window.. when i applied it to mine it doesn't.. i still got the gnome themes..
That's KDE. You can look here: [http://www.omgubuntu.co.uk/2010/11/get-gorgeous-transparent-blurred-app-windows-in-kubuntu/](http://www.omgubuntu.co.uk/2010/11/get-gorgeous-transparent-blurred-app-windows-in-kubuntu/)

There's also a way to do this in gnome. Go google gtk argb.

---

### Post by mcduck on 2010-11-26
> **wakkana12 said:**
> sorry for the double post.. but like this theme [http://gnome-look.org/content/show.php/ShinyIce?content=13328]("http://gnome-look.org/content/show.php/ShinyIce?content=133288")
the screen shot from the second image has a translucent window.. when i applied it to mine it doesn't.. i still got the gnome themes..

If you still get the default Metacity theme (from Gnome's Appearance dialog) then you are not running  Emerald. Also., like already mentioned, Emerald is just a window decorator and has nothing to do with anything else on your desktop, so it will not change your applications theme or introduce transparency anywhere else than just the window borders.

When you open a terminal and run "*emerald --replace*" do you get any error messages? If yes, you should probably copy them here.

Also remember that running "*emerald --replace*" _will not set Emerald as the default_ setting, it only runs Emerald that time (and closes as soon as you close the terminal). To actually set Emerald as th default decorator, so that it launches automatically with your desktop, you need to go to the CompizConfig Settings Manager and in the *Window Decoration*-plugin's settings change the "*command*" to "*/usr/bin/emerald*".

---

