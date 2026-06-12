---
title: "Getting Adoble Flash working in Opera[SOLVED!]"
date: 2009-05-15
forum: General Help
---

### Post by Alpha-Override on 2009-05-15
I use ubuntu 9.04 64 bit and opera 9.64

we all know opera is better than firefox 100%...and i would argue with anyone wanting to dispute that..apart from the fact its not open source...but 10 times more pro than firefox..yep...best browser around...

Please ubuntu include it in the package manager...i mean you gotta be crazy not too...

The only better thing about firefox is more plugins..but who cares right..I mean opera has had its own version of the no script plugin for ages..

Anyway!

I installed flash throught synaptic package manager by installing:
flashplugin-nonfree
flashplugin-installer

Flash will only work in firefox for me...:(

Flash worked fine in firefox but in opera it didn't work at all..or just sound on youtube..it was horrible..

The sad part is you have to make a choice between firefox working and opera for some stupid reason...(Unless you know how to change the plugin folder location for opera, i forgot..hmmm someone would know)

You need to download the latest flash from adobe:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
Get the ubuntu 8.04 version..
Save it
Extract it(if you cant extract it, figure out how to extract by doing a little googling)

In the install_flash_player_10_linux/usr/lib/adobe-flashplugin folder they should be the plugin there...about 9.6MB...

libflashplayer.so

open up a terminal, type the following...

cd /usr/lib/mozilla/plugins
dir
sudo rm flashplugin-alternative.so

cd /usr/lib/opera/plugins

and copy the libflashplayer.so into that directory...
it might be easier to do that with the file browser and open the
/usr/lib/opera/plugins as administrator...

Now open up opera and youtube and everything works!

Yeah i figured this out by myself and im a noob..(only used ubuntu or linux for < 3 weeks...

I think you can have both firefox and opera work but you have to change a config file to point only to the opera plugin directory and put neccesary plugins in there...

Anyway if this dont work for people let me know...Remember to update your flash plugin regularly thought until ubuntu find a proper fix for this...

Anyone who knows how to edit the opera file to only point to opera plugin folder so we can have both firefox and opera use flash let me know...

Also anyone wanting to make this tutorial easier please feel free to change it but give me credit..Anyways peace out..

Ubuntu RULES!

we need a place to download apparmor profiles for more apps...

---

