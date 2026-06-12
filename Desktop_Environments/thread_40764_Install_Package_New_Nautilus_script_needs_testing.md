---
title: "Install Package: New Nautilus script needs testing"
date: 2005-06-10
forum: Desktop Environments
---

### Post by shakin on 2005-06-10
* I'll post this in the Tips & Tricks section as soon as I know it works. *

Seeing a few suggestions about how something like Autopackage would help fix problems trying to install non-repository software, I figured I'd try to do a little something about making RPMs easier to install. I wrote this Nautilus script based on my [previous deb-only script](http://ubuntuforums.org/showthread.php?t=33584) to use as a single point of entry for installing RPMs and Debs. It could easily be adapted to work with any other format Alien supports.

However, this script is entirely untested, by which I mean this is all off-the-cuff code and I don't even know for sure that the shebang line works :). I don't run Gnome anymore and I'm in the middle of a huge batch process, so I can't login to Gnome for a few more hours. Hopefully I can get some feedback from a few brave testers. If that's you, read on.

```
$ gedit ~/.gnome2/nautilus-scripts/Install\ Package
```

Now add the following code and save the file.
```

#!/bin/bash
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	ext=${uri##*.}	# get file extension so we know if it's an rpm or deb
	
# run the correct installer/converter for the file type
	if [ "$ext" = "rpm" -o "$ext" = "RPM" ]
	then
    	gnome-terminal -x sudo alien -i ${uri:7}
    elif [ "$ext" = "deb" -o "$ext" = "DEB" ]
    then
    	gnome-terminal -x sudo dpkg -i ${uri:7}
	fi
done

```

Make the script executable:
```

$ chmod +x  ~/.gnome2/nautilus-scripts/Install\ Package

```

The script will now be accessible from Nautilus' right-click menu under 'Scripts'. If this works, you can delete the 'Install Deb' script if you had that one.

P.S. This should work if you highlight more than one package, even of different types. So you can have a folder with a bunch of rpms and debs in it, highlight them all, then right-click install them all in one menu click.

---

### Post by mhearn on 2005-06-11
> **shakin]* I'll post this in the Tips & Tricks section as soon as I know it works. *

Seeing a few suggestions about how something like Autopackage would help fix problems trying to install non-repository software, I figured I'd try to do a little something about making RPMs easier to install. I wrote this Nautilus script based on my [previous deb-only script](http://ubuntuforums.org/showthread.php?t=33584) to use as a single point of entry for installing RPMs and Debs. It could easily be adapted to work with any other format Alien supports.

However, this script is entirely untested, by which I mean this is all off-the-cuff code and I don't even know for sure that the shebang line works :). I don't run Gnome anymore and I'm in the middle of a huge batch process, so I can't login to Gnome for a few more hours. Hopefully I can get some feedback from a few brave testers. If that's you, read on.

```
$ gedit ~/.gnome2/nautilus-scripts/Install\ Package
```

Now add the following code and save the file.
```

#!/bin/bash
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS said:**
> 
	then
    	gnome-terminal -x sudo alien -i ${uri:7}
    elif [ "$ext" = "deb" -o "$ext" = "DEB" ]
    then
    	gnome-terminal -x sudo dpkg -i ${uri:7}
	fi
done

```

Make the script executable:
```

$ chmod +x  ~/.gnome2/nautilus-scripts/Install\ Package

```

The script will now be accessible from Nautilus' right-click menu under 'Scripts'. If this works, you can delete the 'Install Deb' script if you had that one.

P.S. This should work if you highlight more than one package, even of different types. So you can have a folder with a bunch of rpms and debs in it, highlight them all, then right-click install them all in one menu click.
 Is it really wise to recommend people use Alien? RPMs are simply not designed to install on anything other than the exact system they were built for, whereas autopackages are.

---

