---
title: "Quicktime plugin support"
date: 2005-12-19
forum: Desktop Environments
---

### Post by tagg3rx on 2005-12-19
Hi all,

I need to find a web browser that will support quick time plugins.

I have tried Firefox 1.5 which does not have a plug in and konqueror which as soon as the quick time plug in is called it begins to load an external app that never loads.

I want to try opera but cant figure out how to install it.

Help plz

---

### Post by dcstar on 2005-12-19
[QUOTE=tagg3rx]Hi all,

I need to find a web browser that will support quick time plugins.

I have tried Firefox 1.5 which does not have a plug in and konqueror which as soon as the quick time plug in is called it begins to load an external app that never loads.

I want to try opera but cant figure out how to install it.

Help plz[/QUOTE]
Install mozplugger, that will should make all Firefox Quicktime stuff work.

---

### Post by waldorf on 2005-12-19
Thanks!

I've been beating my head over this one for a while and you solved it!

Cheers

---

### Post by tagg3rx on 2005-12-19
Hi, thanks

How do i do that?
I dont see it in synamtic and upon locating the mosdev website I became a bit lost.  

Thanks

---

### Post by Kurt Dodrill on 2005-12-19
why does synaptic say mozilla-acroread to be removed when attempting to install mozplugger?

---

### Post by dcstar on 2005-12-19
[QUOTE=tagg3rx]Hi, thanks

How do i do that?
I dont see it in synamtic and upon locating the mosdev website I became a bit lost.  

Thanks[/QUOTE]
It is in the "Universe" repository - you need that enabled in your list.

---

### Post by dcstar on 2005-12-19
[QUOTE=Kurt Dodrill]why does synaptic say mozilla-acroread to be removed when attempting to install mozplugger?[/QUOTE]
Probably because of a conflict, I'd say mozplugger replaces its functionality.

---

### Post by rfruth on 2005-12-19
I just started with Breezy and mozplugger did wonders for me, thanks all !  Now I can focus on getting streaming audio (just audio) to work ...

---

### Post by tagg3rx on 2005-12-19
Ok mozplugger is installed - went to a quick time site it still says i need a quicktime plugin.  I click to download it and firefox is unable to find a plugin for it.

Help plz

---

### Post by rfruth on 2005-12-19
Hey tagg like you mozplugger didn't solve everything for me but I can now play (& or save) .MOV files like the movie trailers at rotten tomatoes [http://www.rottentomatoes.com/]("http://www.rottentomatoes.com/") which I couldn't before - now for my streaming audio problem any ideas out there ?

---

### Post by chele on 2005-12-19
You probably will need to install the proprietary (and likely illegal in your country) win32codecs in order to play quicktime.
[]("http://en.wikipedia.org/wiki/Proprietary")

---

### Post by chele on 2005-12-19
[quote=tagg3rx]Ok mozplugger is installed - went to a quick time site it still says i need a quicktime plugin. I click to download it and firefox is unable to find a plugin for it.

Help plz[/quote]Apple does not distribute quicktime plugins for Linux or other Free systems, they only make versions for propietary systems.

People work around this (on x86 machines) with a package called w32codecs, which is less then legal in most parts of the world. There are projects around trying to build legal codecs for these propietary formats, though I am not sure when they will be ready, or how much they will cost.

---

### Post by dcstar on 2005-12-19
[QUOTE=rfruth]Hey tagg like you mozplugger didn't solve everything for me but I can now play (& or save) .MOV files like the movie trailers at rotten tomatoes [http://www.rottentomatoes.com/]("http://www.rottentomatoes.com/") which I couldn't before - now for my streaming audio problem any ideas out there ?[/QUOTE]
This is probably a good start for getting this stuff working:

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

---

### Post by tagg3rx on 2005-12-20
Arrg Maitey

ok i think now i need a repositary with the w32codec in it.
Where would one look to find repositorys not included in the default sources.list.

Thanks,

---

### Post by tagg3rx on 2005-12-20
Ok I have installed the W32Codecs using the walkthru @
[http://www.ubuntuforums.org/showthread.php?t=79449&highlight=w32codec](http://www.ubuntuforums.org/showthread.php?t=79449&highlight=w32codec)

As well as all plugins listed @
[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

sudo apt-get install gstreamer0.8-plugins
sudo apt-get install gstreamer0.8-lame
sudo apt-get install gstreamer0.8-ffmpeg
sudo apt-get install w32codecs
sudo apt-get install libdivx4linux
sudo apt-get install lame
sudo apt-get install sox
sudo apt-get install ffmpeg
sudo apt-get install mjpegtools
sudo apt-get install vorbis-tools
gst-register-0.8

And yet i am still unable to get the quicktime plugin to work

I wish all i needed to do was play a .mov file but i dont, I'd get into specifics but they are long and drawn out, I need the plugin to work or i have to switch back to windows and I really dont want to .....

Please help

---

### Post by sent_by_LUG on 2005-12-20
I think what you need is libquicktime1 (not sure which repository that is in) I installed it and I can see the movie trailers at apple, so that is a good sign.

---

### Post by tagg3rx on 2005-12-20
Hello
I have libquicktime1 installed 

In Konqurer i go to apples site and get nothing
In Firefox I go to apples site and it prompts for a plugin

---

### Post by dcstar on 2005-12-20
[QUOTE=tagg3rx]Hello
I have libquicktime1 installed 

In Konqurer i go to apples site and get nothing
In Firefox I go to apples site and it prompts for a plugin[/QUOTE]
In Firefox, type: about: plugins (remove the space) in the address bar and have a look for any Quicktime entries.

Post them here for us to look at.

---

### Post by tagg3rx on 2005-12-21
Hi 
It's a clean install of Firefox 1.5 so i dont have much to post.  This box dosent need to do much but sit and display 1 web page all day long and play a siren when a system goes down.  The siren happens to be a quick time plugin (thank you ipswitch)

Since I cant find a quicktime plugin about:plugins is blank

Here is the requested info (ie no plugins installed):

Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No

---

### Post by dcstar on 2005-12-21
[QUOTE=tagg3rx]Hi 
It's a clean install of Firefox 1.5 so i dont have much to post.  This box dosent need to do much but sit and display 1 web page all day long and play a siren when a system goes down.  The siren happens to be a quick time plugin (thank you ipswitch)

Since I cant find a quicktime plugin about:plugins is blank

Here is the requested info (ie no plugins installed):

Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No[/QUOTE]
Try reinstalling mozplugger - otherwise your FF installation is not "standard" so none of the plugins are installing correctly.

---

### Post by tagg3rx on 2005-12-22
*shrug*
Well I gave up this morning and switched that system back to the darkside.

I still have my pc on ubuntu but my attempt to bring a box to corporate use has died.  

I blame ipswitch, apple, and the darker shades of purple that tend to mock me on thursdays.

Thanks for the help

---

### Post by dcstar on 2005-12-22
[QUOTE=tagg3rx]*shrug*
Well I gave up this morning and switched that system back to the darkside.

I still have my pc on ubuntu but my attempt to bring a box to corporate use has died.  

I blame ipswitch, apple, and the darker shades of purple that tend to mock me on thursdays.

Thanks for the help[/QUOTE]
It will probably be better to wait until FF 1.5 is in the official Ubuntu repositories, complications can occur with stuff being installed before reaching this status.

---

### Post by mmcmonster on 2005-12-25
[QUOTE=tagg3rx]*shrug*
Well I gave up this morning and switched that system back to the darkside.

I still have my pc on ubuntu but my attempt to bring a box to corporate use has died.  

I blame ipswitch, apple, and the darker shades of purple that tend to mock me on thursdays.

Thanks for the help[/QUOTE]

Make sure firefox is using mplayer to view video instead of totem.  I was having this problem since I installed Ubuntu a couple months ago.  I then stumbled upon  this thread: [http://www.ubuntuforums.org/showthread.php?t=76946](http://www.ubuntuforums.org/showthread.php?t=76946)

I also added /usr/local/lib/win32 to /etc/ld.so.conf and re-ran ldconfig as mentioned in the following thread, just to make sure I didn't hit any bumps. :-)
[http://www.ubuntuforums.org/showthread.php?t=106455](http://www.ubuntuforums.org/showthread.php?t=106455)

Now the Apple Quicktime trailers work fine!.  I'll finally be able to get my brother to switch!


As an aside, maybe someone should make a quicktime how-to that includes getting libquicktime1, w32codecs, [additional mplayer codecs](http://ubuntuforums.org/showthread.php?t=115741), and [setting up mplayer in firefox](http://www.ubuntuforums.org/showthread.php?t=76946)?

P.S. I'm editing this post so that people looking to get quicktime working will find all the info in one place.  Not a how-to, but at least it's something. :-)

---

