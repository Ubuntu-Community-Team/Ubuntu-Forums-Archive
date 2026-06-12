---
title: "Thunar Remember opened windows"
date: 2015-08-26
forum: Desktop Environments
---

### Post by atipico on 2015-08-26
I am looking for a way to get the list of actual opened windows (directories paths) by Thunar. Next step is to write a bash script in order to make Thunar open this list os paths. Can anyone push me to the right direction? Thanks.

---

### Post by Toz on 2015-08-26
Hello and welcome.

You can use wmctrl to list open windows and filter out the thunar ones. However, by default, thunar only displays the folder name in the title bar, not the full path name. 

So, to have thunar display the full path name in the title bar (so that you can grab this info), you need to enable a [hidden setting]("http://docs.xfce.org/xfce/thunar/hidden-settings"):
```
xfconf-query -c thunar -n -p /misc-full-path-in-title -t bool -s true
```

Then, you can use wmctrl to list all open windows:
```
wmctrl -l
```
...and to show only thunar windows (filter by 'File Manager'):
```
wmctrl -l | grep "File Manager"
```
...and if you want to grab all of the current paths of all of the open thunar windows:
```
wmctrl -l | grep "File Manager" | awk '{ print $4 }'
```

---

### Post by atipico on 2015-08-27
Oh boy, thank you! 

Is there a way to get the window and it's tabs also via "wmctrl -l"? Because it is only getting the tab Thunar have focus on...

By the way I suppose I can pass an array of paths back to "wmctrl" and get them opened in Thunar in the same window as tabs, can't I? 
Because if I use "thunar path1 path2" the command opens the paths in different windows, and I'd like them to be opened in the same window.

Thanks!

---

### Post by Toz on 2015-08-27
> Is there a way to get the window and it's tabs also via "wmctrl -l"?
Unfortunately no. Thunar doesn't expose the different tab paths and wmctrl won't see them. This will only work if you use one tab per thunar instance.

> By the way I suppose I can pass an array of paths back to "wmctrl" and get them opened in Thunar
Here is some code that will save the paths of open Thunar windows (using the "save" parameter) and restore them (using the "load") parameter:
```
#!/bin/bash

case $1 in
	save)
		wmctrl -l | grep "File Manager" | awk '{ print $4 }' > ~/.thunar_open_windows
	;;

	load)
		if [ -f ~/.thunar_open_windows ]; then	
			while IFS='' read -r line || [[ -n "$line" ]]; do
    				thunar $line
			done < ~/.thunar_open_windows
		else
			echo "The save file, ~/.thunar_open_windows, does not exist."
		fi
	;;

	*)  echo "Uasge: $0 [save|load]"
	    echo "             save - save the paths of all open Thunar windows"
	    echo "             load - re-open Thunar to the last list of saved paths"
	    echo ""
	;;

esac

```
Basically, call the application with the save parameter to "save" the list and call the application with the "load" parameter to reload the thunar windows.

>  and get them opened in Thunar in the same window as tabs, can't I?
I don't see a way that Thunar can do this - it can only open each path in its own window. There exists [this enhancement request](https://bugzilla.xfce.org/show_bug.cgi?id=9839) to add this functionality.

---

### Post by atipico on 2015-08-27
Thank you very much for the script and the explanations. My conclusion is that I need another Windows Manager.

---

### Post by Toz on 2015-08-27
> **atipico said:**
> My conclusion is that I need another Windows Manager.
Windows manager or File Manager? Regardless, you'll need to find a file manager that exposes the paths of the open tabs since wmctrl will only read the title (most file managers will put the path in the title and that's what wmctrl grabs).

---

### Post by atipico on 2015-08-27
I ment "File Manager", I'm sorry. 
Right now I am testing this: Krusader, a KDE program.
It also does not exposes the tabs' paths but loads the tabs of the latest session.
[http://www.krusader.org/documentation/konfigurator.html](http://www.krusader.org/documentation/konfigurator.html)

---

