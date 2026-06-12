---
title: "ubuntu 7.04 cube"
date: 2007-07-20
forum: Desktop Effects &amp; Customization
---

### Post by amoateng on 2007-07-20
i really want a cube badly on my desktop.. can some one please please tell me where/how to get one step by step 

 
thanks very much

---

### Post by BlahMan_of.Doom on 2007-07-20
1) You could use the shiny search button.
2) Okay fine..here you go:
[http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314) For Compiz Fusion
[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851) For nVidia Beryl
[http://ubuntuforums.org/showthread.php?t=402937&highlight=feisty+beryl+ati](http://ubuntuforums.org/showthread.php?t=402937&highlight=feisty+beryl+ati) for ATI Beryl
[http://ubuntuforums.org/showthread.php?t=267232](http://ubuntuforums.org/showthread.php?t=267232) For Intel GMA.

---

### Post by jhernandez1270 on 2007-07-20
Here are the directions I followed:

I assume that you are using Ubuntu Feisty Fawn (7.04) and gnome.
The first step is to disable Compiz (desktop effect) if it is running.

Then you need to un-install Compiz. So in terminal type:

sudo apt-get -y remove compiz-core desktop-effects

Then add the following line to third party repositories in synaptic:

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy


In terminal type:

wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg)

and then:

sudo apt-key add DD800CD9.gpg

Now in synaptic, hit reload button.
The penultimate step is to install Compiz Fusion. In terminal:

sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf

Finally, in terminal type:

compiz --replace

to activate Compiz Fusion.

Click on System>Preferences>CompizConfig Settings Manager

<ctrl> + <alt> + < L click>

---

