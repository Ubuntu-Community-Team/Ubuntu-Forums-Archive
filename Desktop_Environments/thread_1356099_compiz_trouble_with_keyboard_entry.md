---
title: "compiz trouble with keyboard entry"
date: 2009-12-15
forum: Desktop Environments
---

### Post by chk9 on 2009-12-15
I'm running Hardy and am playing around with cairo-dock and compiz. 
In an attempt to kill the dock (to get access to an item on the desktop underneath the dock.) I inadvertently killed the gnome-session (parent of cairo-dock).  :mad:
Now my windows do not get updated anymore on keyboard input; I have to minimize and restore the window in order to view the results of my entries.

What do I need to do to restore normal operations?

I've reinstalled compiz (not a remove and install, might try this next...), I've checked the drive for errors. to no avail. :confused:

When I switch to metacity or openbox, all is functional except for the eye candy of compiz (and the transparency of the cairo-dock).

Anyone has suggestions what I need to do to restore normal operation in compiz?

:cool: Just when I was pleased with the eye candy I got going, this happens... :(

Thanks all for your help,
chk9

---

### Post by chk9 on 2009-12-16
Well the purge and reload of compiz did not solve it either.
I then tried to run it from the command line:

> compiz --replace

And this is what I found:

> ...
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
...

I first tried *System Tools* -> *Configuration Editor* and found the offending key, but it would not let me change it. (Whenever I unset the value and then exit. It's back to "[]" when I reopen the Configuration Editor again.)
Then I loaded from the command line:

> ccsm

And found under *Window Management* -> *Scale*. I disabled and enabled the option (I still could not find the **initiate_edge** key.) and closed ccsm.
Then restarted compiz and whala it's now working! 

Funny thing is, that it still complains about the error! I guess it was not really the main problem, but maybe just have ccsm rewrite the config fixed my problem.

OK, found now that ccsm is under the *Fusion-icon* -> *Session Manager*.
But you don't see the errors, when you start it from there.
I also found the folders **.gconf/apps/compiz/plugins/**, but not the subsequent folder **scale/** ! :-|

Anyway I'm happy now.
If anyone knows how to fix the error message, that would be great. :confused:

Have Fun, chk9

---

