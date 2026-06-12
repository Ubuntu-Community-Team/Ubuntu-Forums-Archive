---
title: "Ambiance &amp; Radiance menu radio button"
date: 2010-11-08
forum: Desktop Environments
---

### Post by brookie on 2010-11-08
Hello,

Does anybody know why the Ambiance and Radiance "menu radio button" looks broken when I select System>Prefrences>Appearance?

The themes work fine, but the radio button displays broken only in this appearance prefs selection window. 

Look at attached png. 

No big deal, just bugs me when I can't fix things. I already uninstalled and re-installed these themes. No go. Other machines show okay.

Any ideas? 
brook

ps just ran gksudo gnome-appearance-properties and it looks okay. so where is the conf file for gnome appearance properties for the user so i can delete it?

---

### Post by brookie on 2010-11-09
Any of you guys and gals  know why this looks borked on two of my machines? 

See attached png. Does it affect anything? Probably not. 

Does it look borked? Yes. Can I fix it?

---

### Post by brookie on 2010-11-09
Okay, I got to the bottom of this. :P

I'm running Lucid updated from Karmic. When I was in Karmic I had added the webupd8 ppa to use light themes in Karmic. 

Well, after upgrading to Lucid and removing the ppa I was still using:
gtk2-engines-murrine               0.90.3+git20100323-webupd8-3~karmic2

I could have uninstalled this but too many other packages were going to be uninstalled with it. So, I just added the [Murrine Daily ppa]("https://launchpad.net/%7Emurrine-daily/+archive/ppa?field.series_filter=lucid") to my system instead.

More info at [UbuntuGeek]("http://www.ubuntugeek.com/install-ubuntu-light-themes-in-ubuntu-10-1010-04.html"),which is a pretty cool site too. The new updated Radiance theme looks really sweet! Sharp lines with a little more gray than brown.

Hope this helps someone who had previously used webupd8 to install light-themes in Karmic. 

Cheers, 
brook

---

