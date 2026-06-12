---
title: "Synaptic ugly in beryl, terminal not transparent"
date: 2007-04-04
forum: Desktop Environments
---

### Post by grogger13 on 2007-04-04
[IMG]http://i177.photobucket.com/albums/w214/grogger13/Screenshot-synaptic.png[/IMG]

See how synaptic looks like windows 95(not sure about the Linux time line equivalent)

Also i opened the beryl terminal preview window up in the background to compare it to how my terminal looks now.  How do  i make my terminal transparent like the website says is possible.

---

### Post by pjones0404 on 2007-04-04
my synaptic loks exactly the same.

i regards to the transparent terminal, it looks like you have 2 terminls open and one is transparent and one is not. I am not sure how that happened. 

hopefully someone else can explain why the terminal is that way but synaptic looks normal to me.

---

### Post by silverglade00 on 2007-04-04
Try installing gtk2-engines to help with the Synaptic thing.

Terminal - Edit menu - Current Profile - Effects tab - change to Transparent Background and play with the slider to get transparent Terminal.
You might want to do this again choosing edit profiles to make sure they are all set to transparent, if you have more than one.

:)

---

### Post by jocko on 2007-04-04
The reason for the ugly theme is that applications that you run with root privileges will use the settings it can find in the /root directory and not in your home directory.
A simple way to make sure you always have the same theme for your root account as you have set for your normal user can be found in [this post]("http://ubuntuforums.org/showpost.php?p=2385323&postcount=2").

---

