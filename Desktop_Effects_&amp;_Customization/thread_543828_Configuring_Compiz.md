---
title: "Configuring Compiz"
date: 2007-09-05
forum: Desktop Effects &amp; Customization
---

### Post by Grant1219 on 2007-09-05
I installed Ubuntu Fiesty 7.04 x64, but I'm having trouble configuring Compiz. Compiz is working great, the problem is the config app seems very limited.

Here is a screen of the only config tool I seem to have.
[IMG]http://i33.photobucket.com/albums/d86/Smitty1219/config.png[/IMG]

I went to the compiz-settings page on the Compiz site but it seems that is discontinued. What am I supposed to do?

---

### Post by Inxsible on 2007-09-05
I don't think thats the Compiz Config Settings Manager. Have you downloaded ccsm ?

What guide did you use  to install Compiz ?

Also note that Compiz Fusion and Compiz are different. The former is the merger of Compiz and Beryl, whereas the latter(aka Desktop Effects) is what comes installed with Ubuntu and gives only basic plugins

---

### Post by Grant1219 on 2007-09-05
Oh, well I only have the "desktop effects" that came installed with Ubuntu. Although it seems I have Compiz packages installed. What else do I need?

---

### Post by Inxsible on 2007-09-05
> **Grant1219 said:**
> Oh, well I only have the "desktop effects" that came installed with Ubuntu. Although it seems I have Compiz packages installed. What else do I need?
In short,  a lot. :lolflag:

But you should follow one of the guides for installing Compiz Fusion. There are currently three ways to install 

1) Trevino's repos - Bleeding edge , has the latest plugins

2) Amaranth' repos - backported from Gutsy, does not have all the plugins

3) Compile from source 

See which one fits your needs :)

---

### Post by Grant1219 on 2007-09-05
Well it's all installed (thanks for the help, I thought Compiz was already installed), but now there are no window borders! I know many people have had this problem, how do I fix it?

EDIT: Nevermind, I found another tutorial with trouble shooting help, I just had to enable argb-visuals. Thanks for the help.

---

### Post by jhernandez1270 on 2007-09-05
This should get you started with Compiz-Fusion:


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

---

