---
title: "Place terminals in an effective way"
date: 2006-10-26
forum: Desktop Environments
---

### Post by andiii on 2006-10-26
For my basic work I usually need at least three terminals, which I arranged manually most times.

To make this easier I created a script that places the Terminals on the Desktop exactly how I want it.

First, here is how it looks like:
[[IMG]http://img183.imageshack.us/img183/6621/termur3.th.png[/IMG]](http://img183.imageshack.us/img183/6621/termur3.png)

Here is the script:
```
#!/bin/sh
gnome-terminal --window-with-profile=/work/bin --hide-menubar --working-directory=/work/bin  --geometry 97x24+6+0 &
gnome-terminal --window-with-profile=/work/macro --working-directory=/work/macro --geometry 80x24-8+0 &
gnome-terminal --window-with-profile=work --hide-menubar --working-directory=/media/sda4/ --geometry 80x21+6-40 &
sleep 2
gedit
exit 0

```

Terminals get launched without menubar and the --geometry option puts them in the right place.
The sleep 2 makes sure that gedit is loaded last (because gedit doesn't take --geometry options), so it fills up the lower right corner.

If you would like this for your desktop, place the applications (Terminals, and if you want also gedit) how you want them and find out what --geometry values to use by typing "xwininfo" in a Terminal and then clicking on the windows.
Also adjust the --window-with-profile and the --working-directory options to your Profiles and Directories.
For example you could launch one terminal directly to your Music dir and the other one to your Videos. Or whatever one likes.

Save the script somewhere and make it executable. I did

gedit ~/bin/etc/termstart (you have to create the dirs /bin/etc in your home if they don't exist..)
and then
chmod a+x ~/bin/etc/termstart

Finally, I created a launcher and put in ~/bin/etc/termstart as Command.

Now to start work, I just click on that launcher and have three terminals and my text editor started and nicely arranged.

---

