---
title: "HOW TO - Easiest way to get beryl working 100%"
date: 2007-02-06
forum: Desktop Environments
---

### Post by alphanerd on 2007-02-06
It took me 3 days and lots of restoring xorg.conf  before I finally got  beryl/xgl working on a clean install of edgy.  I also found that wikis and howto said conflicting things and none of them really worked.  Anyway it turns out there is a much simpler way.  So if you need to do it here is how

1) go to [www.getautomatix.com](www.getautomatix.com) and get and install proprietry nvidia driver

2) Go to [www.getautomatix.com](www.getautomatix.com) and get install automatixbleeder.  Run bleeder from system tools and install beryl from the gui.

3) go to [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) and downlowd the envy package.  It autodetects you card and gets the correct and latest nvidia driver (the edgy ones wont work).  It also sets up /etc/X11/xorg.conf specific to your card.  Make sure you read the instructions first on the site first.

3) press ctrl-alt-bkspc to restart x and under option on the logon menu choose XGL.

4) run beryl-manager (put it in start up if you want)

5) everything worked except my windows had no  borders.  Read a few sites and they said latest svn fixes this.  So add the repo below and key then 

deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy beryl-svn
wget [http://3v1n0.tuxfamily.org/DD800CD9.gpg](http://3v1n0.tuxfamily.org/DD800CD9.gpg) -O- | sudo apt-key add -

then sudo apt-get update
then sudo apt-get dist-upgrade.

Works a treat!!!

---

### Post by shareMenaPeace on 2007-02-06
Well you either need the automatix nvidia-settings tools to install the nvidia driver or let envy do this.
Or you can use the unoffical nvidia driver.

---

### Post by lukanium on 2007-02-06
My ATI Radeon is so bad :(, maybe i have to buy a new nvidia one to use 3D and XGL

---

### Post by 71CH on 2007-02-06
Does anybody know the system requirements?  Do you need nvidia to get it to work properly? Thanks.

---

### Post by .robert on 2007-02-07
Speed up Beryl for older (ATI?) video cards with very little RAM.

I am running Feisty Fawn and used Synaptic to install Beryl.  I was really impressed by the features, so couldn't help myself, and installed.  I have an older (and cheap!) ATI card without much RAM, and Beryl was very slow.  Whenever I tried to move a window, the lag was pretty bad.  I almost gave up on it due to performance after enjoying playing around with it for a while.  I just figured I needed to wait until I upgraded to a new NVidia card.  Not So!  The hog appears to be the "Blur Effects", not Beryl in general!


[LIST=1]
[*]Open "Beryl Settings Manager."
[*]Click "Visual Effects"
[*]UN-Check "Blur Effects"
[/LIST]

Man, did this speed up everything Beryl does!  I hope this helps out others.  I'm really pleased to have Beryl running now as my regular Window Manager.  It's not essential, but certainly cool.

Robert

---

