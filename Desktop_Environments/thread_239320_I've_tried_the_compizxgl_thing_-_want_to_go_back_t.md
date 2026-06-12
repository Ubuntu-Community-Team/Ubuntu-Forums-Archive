---
title: "I've tried the compiz/xgl thing - want to go back to normal..."
date: 2006-08-19
forum: Desktop Environments
---

### Post by elbowgeek on 2006-08-19
The xgl thing definitely ain't happenin' on this ol' laptop's weezy hardware, but I'm left with a graphic interface which is rather mucked up. 

It does work inasmuch as I do have gnome working, but there are screen artifacts and slow screen redrawing issues, and I'd like to reset it to the original settings.

Is there any way of doing so without reinstalling the system entirely?  Or have I toasted the graphical interface completely? 

Thanks for any advice :-)

Cheers

---

### Post by clibre on 2006-08-19
> **elbowgeek said:**
> The xgl thing definitely ain't happenin' on this ol' laptop's weezy hardware, but I'm left with a graphic interface which is rather mucked up. 

It does work inasmuch as I do have gnome working, but there are screen artifacts and slow screen redrawing issues, and I'd like to reset it to the original settings.

Is there any way of doing so without reinstalling the system entirely?  Or have I toasted the graphical interface completely? 

Thanks for any advice :-)

Cheers

You can find some hints about restoring Xorg at the following link:
[http://sonique54.free.fr/xgl/xgl.htm]("http://sonique54.free.fr/xgl/xgl.htm")

---

### Post by elbowgeek on 2006-08-19
Thanks, I'll give that a try :)

Cheers

---

### Post by elbowgeek on 2006-08-19
No luck.  And I imagine anything further requires sacrificed virgin olive oil and chicken blood boiled in the graveyard at midnight on a full moon, so I think I'll just install from scratch, unless there's any other suggestions.

Thanks anyway :-)

Cheers

---

### Post by sumadartson on 2006-08-19
Now, this is why you back up configuration files before you change them :D.

Remember that you modified /etc/gdm/gdm.conf-custom? If I'm correct you added the following lines : 

```
[servers]
0=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true
``` 

IIRC you can switch back to normal Xorg by deleting everything beneath [servers] . Back up first, in case this doesn't work.

To backup use the following command:```

 cp filename filename.`date +%Y%m%d%H%M`.bak
```

This will leave you with a copy of the file of the same name with year, month, date, hour, minute and .bak added to the file name.

Now, restore your original Xorg.conf as well. Again, backup the file before you change it. If you no longer have that file, try 
```
dpkg-reconfigure xserver-xorg
```

No longer start compiz on when you login (remove it from start-up progams in your session settings).


As a final note, XGL can actually be faster than Xorg. Turning off most effects from compiz should leave you with a very fast desktop. What kind of video-card do you have?

---

