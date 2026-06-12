---
title: "HOW TO: Get Atlantis working on Gutsy's default compiz"
date: 2007-11-03
forum: Desktop Effects &amp; Customization
---

### Post by scottDkoDer on 2007-11-03
Well, for those that are using Gutsy and would like to have the additional eyecandy plug-in 'Atlantis' working with Gutsy's default compiz-fusion, I'm presenting this guide.  This tutorial assumes that:

1) You already have Gutsy installed.
2) You already have Gutsy's default compiz working.
3) You are running as user and not root.

NOTE: compiz-fusion is installed by default in Ubuntu Gutsy and will work as long as you have a video card with appropriate drivers and proper configuration.  This is beyond the scope of this tutorial, but there are a plethora of guides to configure your graphics card on Gutsy.

```
sudo apt-get install compiz-bcop compiz-dev build-essential libxcomposite-dev libpng12-dev libsm-dev libxrandr-dev libxdamage-dev libxinerama-dev libstartup-notification0-dev libgconf2-dev libgl1-mesa-dev libglu1-mesa-dev libmetacity-dev librsvg2-dev libdbus-1-dev libdbus-glib-1-dev libgnome-desktop-dev libgnome-window-settings-dev gitweb curl autoconf automake automake1.9 libtool intltool libxslt1-dev xsltproc
cd /tmp && wget -O 'atlantis.tar.gz' 'http://gitweb.opencompositing.org/?p=fusion/plugins/atlantis;a=snapshot;h=a47d7151444faccd66ea5cb884673cdebe5d7dff'
cd ~/ && mkdir compiz
cd ~/compiz
tar -xvf '/tmp/atlantis.tar.gz' && cd 'atlantis'
make clean
make
make install
```

If there are any problems, please check the prerequisites first, then ensure you have followed all instructions and typed all commands correctly.  Each should return without errors. If all is in order and there are issues, then post any problems or suggested changes here.

Enjoy,

Scott

---

### Post by chefboyjames on 2007-11-09
Thank you very much for the how to. For the mildly computer stupid like myself it is pretty tough to figure out how to install through the "GIT " repositories. The only thing for me though was that I had to add "sudo" to make install before I had permission,don't know if this would be an in general thingy or just for me. Anywho.....loving compiz-fusion and if I can get a couple games to play through wine(scary) then I'll be completely off windows for good( YAY ), Thanks.,


James

---

### Post by stixguy on 2008-01-24
Worked like a charm, thanks.

---

### Post by seanelvidge on 2008-03-25
Hi after typing in the last line i get this:

install   : /home/sean/.compiz/plugins/libatlantis.soinstall: cannot create regular file `/home/sean/.compiz/plugins/libatlantis.so': Permission denied
make: *** [install] Error 1

Does anyone know why this is??

---

### Post by enchantedsky on 2008-03-25
Thanks for this guideline. 

I have installed Atlantis successfully, but what do you do afterwards? I've enabled the Atlantis plugin in the Advanced Desktop Effects Settings, but nothing is happening. Are you supposed to restart your system or something else?

Edit: Ok, I fixed my problem. Apparently you have to go into the settings for the "Desktop Cube" plugin and adjust the level of transparency to 50% to see the Atlantis plugin

---

