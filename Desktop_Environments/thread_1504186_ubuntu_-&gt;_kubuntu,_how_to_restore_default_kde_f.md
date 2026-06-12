---
title: "ubuntu -&gt; kubuntu, how to restore default kde file associations?"
date: 2010-06-07
forum: Desktop Environments
---

### Post by jonas_t on 2010-06-07
hi there,

i initially installed ubuntu, working with gnome for a while. i now migrated to kde as i like it better. however, the kde session still has lots of the "old" file associations set as they are in gnome...

some examples?
text files open in gedit, instead of kate
pdfs open in "document viewer" instead of okular
double clicking zip folder opens the "archiver" (gnome?), extracting an archive from the archiver and then pressing the "open folder" dialog after extracting has finished, opens nautilus (although dophin is the default program for inodes).
... etc.

i'm aware of the possibility to edit file associations, however thats a tedious thingy to do, if you want to get it complete... furthermore, the file association edit dialog has the "defaults" button disabled, hence my questions:

is there any way to "restore" the kde default file associations, just as i would have installed **k**ubuntu initially? i don't want to reinstall just because of this...

thanks,
jonas

---

### Post by SlidingHorn on 2010-06-07
You can remove the gnome aspects by 

```
sudo apt-get remove ubuntu-desktop
```

and then make sure that all of the necessary kde packages are installed:

```
sudo apt-get install kubuntu-desktop
```

---

### Post by jonas_t on 2010-06-08
hey,

thanks for the quick reply. however,  ubuntu/gnome is not completely removed since removing the meta-package ubuntu-desktop  does not cause any of the ubuntu packages to be scheduled for autoremove...

i found some other threads referring to a "kde only" system (and the respective apt-get command), but that also removes firefox etc. it's weird that now, after removing the meta-package, all those gnome packages are still installed...

---

### Post by SlidingHorn on 2010-06-08
Maybe this might help: [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

**Edit:**  That removes firefox as well...you can always reinstall any of the packages you want to keep (or just not include them in the command)

---

### Post by jonas_t on 2010-06-08
hey,

yeah this is what i was referring to with 

> "kde only" system

in my previous post. however, i'm not sure whether this is a good idea since i dont know for sure which applications i would have to keep in order to not change my running kde system. i just wan to get rid of the gnome thingies.. :)

---

### Post by jonas_t on 2010-06-09
few, with lots of fiddling i managed to get that "pure kde" to a "kde with my apps" ....

uninstalled that bunch of gnome applications somehow messed up the system or revealed a messed up system. i'm not sure which is true..

apt-get would just refuse to remove the packages as it detected some broken libraries... aptitude also detected the same broken packages but offered to resolve these broken things... after that my ati control center was broken... (dpkg-divert said something of libGL.so pointing to the wrong file...?!) -> google helped... complicated commands finally let me reinstall the control center and the fglrx driver... phew

thanks anyway. :) -> marking as solved.

---

