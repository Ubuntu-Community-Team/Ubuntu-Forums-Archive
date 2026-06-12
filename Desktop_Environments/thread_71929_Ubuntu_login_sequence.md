---
title: "Ubuntu login sequence"
date: 2005-10-04
forum: Desktop Environments
---

### Post by Tuxhedoh on 2005-10-04
Can someone explain the login sequence to me?  I've found a GDM theme to change the look of that screen, but the next screen has the brown Ubuntu logo'ed screen.  How do I change that screen? Where is it located? Is there part of the Wiki that has this answer that I couldn't find?

---

### Post by brentoboy on 2005-10-04
[QUOTE=Tuxhedoh]Can someone explain the login sequence to me?  I've found a GDM theme to change the look of that screen, but the next screen has the brown Ubuntu logo'ed screen.  How do I change that screen? Where is it located? Is there part of the Wiki that has this answer that I couldn't find?[/QUOTE]

My workaround for that-> I go get a sandwich at that point.

All kidding aside, I'd like to try something else there to. Maybe even relace the "welcome to ubuntu" sounds that are played with some starttrek intro music or something.

---

### Post by XDevHald on 2005-10-04
You will need to goto "System > Administration > Login Screen Setup "type the password to get access" then goto "Themed Greeter" and you can click on INSTALL on the bottom right and find the located tar.gz and just click ok. here's a screen shot of what it should look like when you install.

Just be sure to select the dot next to the theme to make it work :)

---

### Post by brentoboy on 2005-10-04
[QUOTE=Steve Myers]You will need to goto "System > Administration > Login Screen Setup "type the password to get access" then goto "Themed Greeter" and you can click on INSTALL on the bottom right and find the located tar.gz and just click ok. here's a screen shot of what it should look like when you install.

Just be sure to select the dot next to the theme to make it work :)[/QUOTE]

Yeah, I am using the garGANTuan theme, it looks great, then as soon as I log in, here comes the humanity startup phase...  where I go get a sandwhich so I dont have to be attacked by brown.

---

### Post by XDevHald on 2005-10-04
:) glad it worked, if you want to change the splash page that you're seeing after the login GDM theme, you can [B]sudo chmod 777 /usr/share/pixmaps/splash

[/B]From there you can take ANY splash image you want and put it in there. Once you're done with that be sure you know the name of the image you want to be the main splash and head to "**Applications** > **System Tools** > **Configuration Editor** and click on **Apps**  > **Gnome-Session** and edit the **splash image **by right-clicking and [B]Edit Key.

[/B]Rename the .png to the name you had saved the splash as in the directory you put it in. Then once you're done click ok once you have done edited the key for the splash image and log out to see the affects made. :)

---

