---
title: "Help with the plugins-extra package for Compiz."
date: 2010-08-21
forum: Desktop Environments
---

### Post by xBiocorex on 2010-08-21
Hello there.

My computer came with (I think) Compiz 0.8.4, and after installing the config manager I enjoyed all the fun little effects like 3D Desktop and Water. Buuuuut... I noticed after scrolling through the wiki that there were a good chunk of plugins that were missing, and they sounded pretty neat. I scoured several google results looking for someone who might have an idea as to where these have gone, and eventually I wound up in a funny... library or something of compiz releases.

[http://releases.compiz-fusion.org/0.8.4/](http://releases.compiz-fusion.org/0.8.4/)

I downloaded both packages for the plugins-extra, and looked at the install instructions. ./configure worked for the non-cmake one, but then it told me my intltool was too old... Gah this is confusing. The Compiz wiki should just have download links for individual plugins. ><

---

### Post by Vrroom on 2010-08-21
why don't you install extra compiz plugins from synaptic. search compiz extra....there is a package....install it.

---

### Post by nick_goodfate on 2010-08-21
> **Vrroom said:**
> why don't you install extra compiz plugins from synaptic. search compiz extra....there is a package....install it.

+1 

And for more plug-ins check my signature ...

---

### Post by xBiocorex on 2010-08-21
> **Vrroom said:**
> why don't you install extra compiz plugins from synaptic. search compiz extra....there is a package....install it.
If you would care to explain how I do this? I'm really not happy with all this ./configure, make install stuff in the terminal, it just doesn.t work for me. I can't even install synaptic package manager because I need xmlto.

---

### Post by nick_goodfate on 2010-08-22
> **xBiocorex said:**
> If you would care to explain how I do this? I'm really not happy with all this ./configure, make install stuff in the terminal, it just doesn.t work for me. I can't even install synaptic package manager because I need xmlto.

Synaptic Package Manager is by default installed in Ubuntu. 

[LIST]
[*]Open it (System->Administration->Synaptic Package Manager)

[*]Type in quick search box "ubuntu restricted extras"(without the quotes).

[*]You will see a list of results in the box below quick search. Right click on the package with the name "ubuntu-restricted-extras" and select mark for installation (If it ask you to install additional packages, press yes...? ok...? accept it). 

[*]Click apply and you have installed ubuntu restricted extras! No ./configre make and other scary things...
[/LIST]

---

### Post by stinkeye on 2010-08-22
In  Ubuntu software centre search for and download **compiz-fusion-plugins-extra**


There are also experimental plugins which need to be compiled.
There is a script here that will download and compile these plugins,
while also resolving any dependencies.
[**_[COLOR="DarkRed"]Compiz Addons: A script to install experimental plugins[/COLOR]_**]("http://forum.compiz.org/viewtopic.php?f=114&t=12012")

**Plugins you can install with the script:**
anaglyph
atlantis
cubemodel
dialog
elements
extra-animations
fakeargb
fireflies
freewins
ghost
photowheel
putplus
screensaver
simple-animations
smartput
snow
snowglobe
stackswitch
stars
static
swap
tile
toggle-decoration
wizard
workspacenames

---

### Post by xBiocorex on 2010-08-22
Thanks so much guys. I'm sorry for being so noobish. XD

---

### Post by larryfroot on 2010-08-31
Thanks so much one and all - have just installed these excellent plugins with your advice and help :D now to work out why gstyle is now failing to start!

---

### Post by Bobbyrne01 on 2010-09-03
Sweet was wondering for ages how to get the extra plugins . . synaptic package manager was d way forward :)

---

