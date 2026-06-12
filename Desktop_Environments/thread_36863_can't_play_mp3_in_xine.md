---
title: "can't play mp3 in xine"
date: 2005-05-25
forum: Desktop Environments
---

### Post by epb613 on 2005-05-25
After a fresh install:
added backport and mallirat repo's.
sudo apt-get install w32codecs
sudo apt-get install xine-ui

Then I double click on an mp3 and xine tells me I don't have the codec.

What's interesting is then if I go ahead and install kaffeine, then xine works to. And if I install the gstreamer plugins for totem, then also xine works.

This never used to happen until my last 5 installs or so (ie: my installs over the last week).

If anyone has any idea what's up with this I would appreciate your ideas. Thanks.

---

### Post by Mez on 2005-05-25
mp3s are a Restricted filetype in ubuntu, meaning that support by default is not added... however, xine uses the gstreamer pluing to play Mp3s, so you can install that to get mp3 workign

read

[http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)

for more info on restricted formats

---

### Post by lorap on 2005-05-25
hi friend!
install this player - VLC, and you'll be out of troubles, trust me.
but before you install it via synaptic you've to add it to the repositories's list.
let's do it right now so after i get home the only thing you'd have to do just install the only package.
first of all open System-->Computer Management-->Synaptic Package Manager.
after you get it open go to the Setting-->Repositories.
once you get the repositories window open press Advanced button and mark all checkboxes possible except "download only upgradable packages" then press Ok.
after what you'll need to wait until the update process completes. the repositories' window'll close at the end of the process so you'll be prompted again the synaptic window.
press the Reload button and wait until the reload process completes.
now you're able to install the VLC player.
press the Search button and write in VLC then press Ok.
once you have the package fount out mark it for install and then press Apply button. wait until install process completes after what close the synaptic.
have a nice day.
pavel

p.s.:
or install this codec - gstreamer0.8-ffmpeg

---

### Post by Zodiac on 2005-05-26
[QUOTE=lorap]hi friend!
install this player - VLC, and you'll be out of troubles, trust me.
but before you install it via synaptic you've to add it to the repositories's list.
let's do it right now so after i get home the only thing you'd have to do just install the only package.
first of all open System-->Computer Management-->Synaptic Package Manager.
after you get it open go to the Setting-->Repositories.
once you get the repositories window open press Advanced button and mark all checkboxes possible except "download only upgradable packages" then press Ok.
after what you'll need to wait until the update process completes. the repositories' window'll close at the end of the process so you'll be prompted again the synaptic window.
press the Reload button and wait until the reload process completes.
now you're able to install the VLC player.
press the Search button and write in VLC then press Ok.
once you have the package fount out mark it for install and then press Apply button. wait until install process completes after what close the synaptic.
have a nice day.
pavel

p.s.:
or install this codec - gstreamer0.8-ffmpeg[/QUOTE]


You have posted this as an answer to a few threads that I have seen while researching my problem, but there is a problem....

There is no advanced tab anywhere to be found in the synaptic manager! So, ummm, what pray tell are you talking about? 

This could go a long way to solving my problem...

---

