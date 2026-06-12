---
title: "Armagetron Moviepacks"
date: 2006-04-20
forum: Gaming &amp; Leisure
---

### Post by sinfreealex on 2006-04-20
Armagetron looks so much better with the moviepacks installed (and in some cases sounds better) but I am unsure as to where to install them.  Where do these suckers go?  The guide on the site tells how to set things up on a Win machine only. :-\"

---

### Post by K.Mandla on 2006-11-14
A late reply, but I found the answer. It took me a while, but short of Neverwinter Nights and Wolfenstein Enemy Territory, this is by far my favorite game for Ubuntu.

I'm using the Feisty version of Armagetron, and the system files are installed to /usr/share/games/armagetron.

You'll need to download the original moviepacks from the SourceForge page.

[http://armagetron.sourceforge.net/old/addons.html](http://armagetron.sourceforge.net/old/addons.html)

Decompress those into a folder called moviepacks (all lower case) in /usr/share/games/armagetron with this command.

```
sudo unzip moviepack.zip -d /usr/share/games/armagetron/
```
Don't forget the trailing slash.

Now download the moviepack you want to use. There are a lot on the Armagetron Advanced wiki page for moviepacks.

[http://wiki.armagetronad.net/index.php/Moviepacks_list](http://wiki.armagetronad.net/index.php/Moviepacks_list)

Decompress your chosen moviepack **into the same folder**, overwriting any files that are already in there.

```
sudo unzip name_of_your_chosen_moviepack_file.zip -d /usr/share/games/armagetron/
```
Again, don't miss the trailing slash. Tell UnZip to overwrite anything it finds there.

Restart Armagetron and you should get the new scenes, sky and light cycle trails. If not, make sure you have Moviepacks turned on in the system settings.

Cheers! :mrgreen:

---

### Post by sinfreealex on 2006-11-14
Funny thing is that I moved to a 20" iMac a month ago so I had to figure out where to put them in OSX.  Thanks for the reply.  Hopefully this will help someone in the future.

:D

---

