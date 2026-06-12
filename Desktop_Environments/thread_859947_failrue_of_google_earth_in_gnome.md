---
title: "failrue of google earth in gnome"
date: 2008-07-15
forum: Desktop Environments
---

### Post by natman3400 on 2008-07-15
```
natman3400@natman3400-laptop:~/Desktop$ ./file.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 4.3.7284.3916..............................................................
You don't seem to be running an X server (no DISPLAY set).
Google Earth and its installer both require X11.
Aborting...

```

---

### Post by kunixos on 2008-07-15
are you installing from apt or the downloaded program?

have you tried:
```
sudo apt-get install googleearth
```

also, what happens when you do this in the terminal:
```
echo $DISPLAY
```

if nothing, you may need to reset your display manager (Ctrl+Alt+Bkspc) or reconfigure X11, but i think the first line should do it.

---

### Post by natman3400 on 2008-07-15
```
natman3400@natman3400-laptop:~/Desktop$ sudo apt-get install googleearth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package googleearth
natman3400@natman3400-laptop:~/Desktop$ echo $DISPLAY

natman3400@natman3400-laptop:~/Desktop$ 
```
Downloaded version

---

### Post by merlyn on 2008-07-15
G'day natman,

this may not be the solution you are looking for, as it involves installing google earth 4.2.

If you haven't alreadydone so add the appropriate repositories from [medibuntu]("http://www.medibuntu.org/").

Once done you'll have acess to the debs for versions 4.2 and 4.3 via apt-get / synaptic / adept.

Personally I haven't had much success getting the 4.3 debs to work but 4.2 works fine.

You on the other hand may have better luck with them.

Cheers.

---

### Post by dr.phees on 2008-07-15
@merlyn: What was your problem with googleearth 4.3? If it was that you got an empty window / no earth, this might help you:
[http://blog.phees.de/index.php?/archives/6-earth-4.3-by-google.html](http://blog.phees.de/index.php?/archives/6-earth-4.3-by-google.html)

To get a nicer Qt-interface:
[http://blog.phees.de/index.php?/archives/26-Face-lifting-GoogleEarth.html](http://blog.phees.de/index.php?/archives/26-Face-lifting-GoogleEarth.html)

---

