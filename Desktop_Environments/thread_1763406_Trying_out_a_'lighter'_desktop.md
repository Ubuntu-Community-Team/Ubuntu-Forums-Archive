---
title: "Trying out a 'lighter' desktop"
date: 2011-05-20
forum: Desktop Environments
---

### Post by Condor Cluster on 2011-05-20
I'm currently on Lucid Gnome, and would like to try a different DE.

Not sure what the difference between Xubuntu or Lubuntu is, but I've heard good things about XFCE anyway.

Question is, is there a way to try XFCE on my installation without having to reformat and install the Xubuntu disc? (so all my settings and apps stay intact)

Also, do all the things that work in Gnome (Banshee, Transmission, Chrome, FF, LibreOffice etc) work in Xubuntu?

Thanks.

---

### Post by akand074 on 2011-05-20
You can install XFCE desktop environment right from synaptic package manager. And yes all the software still work in XFCE. There is always still a chance of breakage so I'd backup/be careful. But you should be fine.

---

### Post by SoFl W on 2011-05-20
After adding the XFCE packages from the package manager,  you should have a selection option on the bottom of the log-in screen with your choices.

You can also try it first with the live CD or USB stick.  I installed Xubuntu on my old laptop after trying 11.4 and being disappointed.  It is a great environment.

---

### Post by Condor Cluster on 2011-05-20
Ok, thanks. I take it I can switch DE at the login screen.

Would you recommend XFCE or one of the other ligter DEs (LXDE)?

---

### Post by Frogs Hair on 2011-05-20
The live cd /usb may be the best option without a major commitment .

---

### Post by snowpine on 2011-05-20
You can install as many desktop environments as you like and switch between them from the login manager. Xfce and LXDE are both definitely worth checking out, in my opinion.

To remove an installed desktop environment and go back to "pure" Gnome/Xfce/LXDE/etc you can follow these tutorials:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)
[http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

(lots of other great tutorials on that site, too!)

---

### Post by Condor Cluster on 2011-05-20
Thanks all.

I might wait till I update from Lucid to change DEs.

Seems that Unity could be a real resource hog, so a Lubuntu 11.04 could be on the cards on the not so distant future!

---

### Post by Condor Cluster on 2011-05-21
Can I use all the ppa's and apps in Lubuntu as well? Or do you have to install all the gnome libraries like you have to do with amarok kde libraries?

Also, will ubuntu tweak work with lubuntu?

Thanks

---

### Post by Copper Bezel on 2011-05-21
Unbuntu Tweak is designed around Ubuntu Gnome running with Compiz, so few of the features will work. 

No matter what DE you're running on it, Ubuntu uses the same repositories, so that part's not an issue.

---

### Post by ivanovnegro on 2011-05-21
> **Condor Cluster said:**
> Can I use all the ppa's and apps in Lubuntu as well? Or do you have to install all the gnome libraries like you have to do with amarok kde libraries?

Also, will ubuntu tweak work with lubuntu?

Thanks

Xubuntu and Lubuntu are also using some parts of Gtk just like Gnome so it would not be a problem to use the Gnome apps and they integrate perfectly. For some things you have to tweak it a little bit, like LibreOffice, to have the same look like in Gnome, just install the package libreoffice-gtk from Synaptic. Compiz is a little bit harder because you have to replace the native window manager, but you want it lightweight, so I would not install that on Xfce or LXDE.
The other things are themes that require the Gtk engines.
In general for all the things you want to install that come from Gnome there is no problem for that, maybe some Gnome dependencies, but that does not matter really in my opinion. Of course if you want to go hardcore lightweight then you should not install nothing from Gnome, especially like LibreOffice.

I can only recommend you to try LXDE and Xfce, Im impressed of both, especially I love Xubuntu.

---

### Post by Condor Cluster on 2011-05-21
Will Lubuntu allow me to use keyboard keys to increase/decrease volume & brightness, and also to output to external display via vga port so I can use my netbook in 'clamshell' mode?

---

### Post by ivanovnegro on 2011-05-21
> **Condor Cluster said:**
> Will Lubuntu allow me to use keyboard keys to increase/decrease volume & brightness, and also to output to external display via vga port so I can use my netbook in 'clamshell' mode?

Normally this should work like in Ubuntu. On Xubuntu its working here.

---

### Post by Condor Cluster on 2011-05-21
Cool.

Gonna take the plunge and replace Ubuntu 10.04 with Lubuntu 10.04, then at least its still got long term support (and I know should work with my netbook)

Does Xubuntu/Lubuntu still use pulseaudio?

Can finally shed all that integrated evolution nonsense aswell :)

---

### Post by ivanovnegro on 2011-05-21
> **Condor Cluster said:**
> Cool.

Gonna take the plunge and replace Ubuntu 10.04 with Lubuntu 10.04, then at least its still got long term support (and I know should work with my netbook)

Does Xubuntu/Lubuntu still use pulseaudio?

Can finally shed all that integrated evolution nonsense aswell :)

Im on version 11.04 and it uses Pulse Audio, I think the same applies to 10.04.
The integrated Evolution is replaced on Xubuntu 11.04 with Thunderbird, but you can remove it there and it uses Pidgin what I like.
In Lubuntu I would look in the release notes of 10.04.
And now another thing, as Lubuntu is still not an official Ubuntu derivative, I think it would be better to install 11.04, I think there is no LTS yet for it, if someone knows better, please correct me.
It seems Canonical decided to make Lubuntu with the release 11.10 to an official derivative, then you would have LTS versions in the future. I also recommend you the improved 11.04 release of Lubuntu, it is great and dont fear about too many issues like in Unity, Lubuntu is another beast.

Edit: Try the Live CD anyway to assure to not have issues with the environment, its the best in my opinion or try the metapackage.

---

