---
title: "Composito Effecto"
date: 2008-04-09
forum: Desktop Effects &amp; Customization
---

### Post by Exsecrabilus on 2008-04-09
So I recently installed **xorg-driver-fglrx** to enable the **ATI accelerated graphics driver**.

[IMG]http://i212.photobucket.com/albums/cc134/Exsecrabilus/Picture25.png[/IMG]

Now when I go to **Appearances** >> **Visual Effects**:

[IMG]http://i212.photobucket.com/albums/cc134/Exsecrabilus/Screenshot1.png[/IMG]

And try to enable **Normal** or **Extra Effects**, it says there is no composite extension:

[IMG]http://i212.photobucket.com/albums/cc134/Exsecrabilus/Screenshot2.png[/IMG]

What do I have to install to enable this?

P.S.:
I don't have Internet on my Ubuntu laptop so I'm writing this from someone else's computer.
I just go to [Http://packages.ubuntu.com/](Http://packages.ubuntu.com/) and download .deb packges from there, put the files onto my USB and install them at home.

Also, I'm running **Ubuntu 7.10** on an **HP laptop** that I bought like 9 months ago.

THANKS FOR ALL THE HELP!!!!!

---

### Post by russo.mic on 2008-04-09
sudo apt-get install xserver-xgl

sudo apt-get install compizconfig-settings-manager

have fun!

---

