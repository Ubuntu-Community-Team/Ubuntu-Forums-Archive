---
title: "Chromium &quot;show in folder&quot; and downloads in Lubuntu"
date: 2010-06-01
forum: Desktop Environments
---

### Post by beastrace91 on 2010-06-01
Howdy All,

So I recently installed Lubuntu on my netbook and I have it all working except for one hitch - when I download something in Chromium (such as a .deb or a .odt file) when I click on the finished download in the bar at the bottom of Chromium it does not open the file in gdebi/abiword as it should. Also when I right click on a file and select "show in folder" it does not work...

Any suggestions? Not sure if this is an issue with Chromium or LXDE/PCMan but I figured it couldn't hurt to post here asking about it.

Regards,
~Jeff

---

### Post by kerry_s on 2010-06-01
i think it's xdg-open.

try this:
**sudo ln -s /usr/bin/gnome-open /usr/local/bin/xdg-open**

---

### Post by beastrace91 on 2010-06-01
> **kerry_s said:**
> **sudo ln -s /usr/bin/gnome-open /usr/local/bin/xdg-open**

Both those files exist already :-/ Any other ideas?

~Jeff

---

### Post by kerry_s on 2010-06-01
> **beastrace91 said:**
> Both those files exist already :-/ Any other ideas?

~Jeff

you don't understand, that command links xdg-open to gnome-open, cause gnome-open handles things better. you can always delete the "/usr/local/bin/xdg-open" link to reverse it back to normal.

the problem with lxde, is it uses both gnome & xfce4 parts, so there are 3 different systems to open things "xdg-open, gnome-open, exo-open" out of the 3 the gnome-open gets it right most of the time & if it don't it can be changed in gconf-editor.

xdg-open = open standard
gnome-open = gnome
exo-open = xfce4

chromium uses xdg-open to determine what to use to open things.

---

### Post by Kaso_Da_Zmok on 2010-06-21
chrome uses xdg-open

it is dumb script, edit it to your needs. i use e16 and rox to show in folder.

```
[root@rzcoolerm64 ~]# which xdg-open
/usr/bin/xdg-open
[root@rzcoolerm64 ~]# nano /usr/bin/xdg-open
```

scroll to the very end of the file and hardcode what you need. i replaced the open_generic with rox.

```

    generic)
    rox "$url"
    ;;

#    generic)
#    open_generic "$url"
#    ;;
```

---

### Post by beastrace91 on 2010-06-21
Very cool! Thanks for the tip :)

~Jeff

---

### Post by realbezo on 2010-09-24
i recently installed lubuntu on my laptop and had the same problem.
But i just modified the file a bit differently due to lubuntu's default file manager is pcmanfm. 
    
   generic)
    pcmanfm "$url"
    ;;

worked for me. Thanks a lot for the solution

---

### Post by ohiomoto on 2010-11-02
> **realbezo said:**
> i recently installed lubuntu on my laptop and had the same problem.
But i just modified the file a bit differently due to lubuntu's default file manager is pcmanfm. 
    
   generic)
    pcmanfm "$url"
    ;;

worked for me. Thanks a lot for the solution

Thanks!  I also have Lubuntu and this worked perfectly.

I used leafpad to edit xdg-open:

```
sudo leafpad /usr/bin/xdg-open
```

My changes looked like this when done and it works great with Chromium.
```

    generic)
    pcmanfm "$url"
    ;;

#    generic)
#    open_generic "$url"
#    ;;
```

---

### Post by apochry on 2011-08-23
> **kerry_s said:**
> i think it's xdg-open.

try this:
**sudo ln -s /usr/bin/gnome-open /usr/local/bin/xdg-open**

Worked for me on Lubuntu 11.04.
Thanks!

---

