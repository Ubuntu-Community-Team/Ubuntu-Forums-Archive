---
title: "No image preview and disappearing workspaces"
date: 2013-05-27
forum: Desktop Environments
---

### Post by cincinnatus13 on 2013-05-27
Running Gnome 3.6 in Ubuntu Gnome 13.04.
Added a few extensions and Dropbox but otherwise nothing really.

Anyway, one, even after changing preferences for Nautilus and logging out and back in, I can't get image previews. I have it set to 100MB and still can't get even small JPEGs to generate thumbnails. Do I need to manually clear out the cache to get it to work? I've tried reload and it just gives me the small normal icons.

Also, only other thing is I have the Faenza icons I believe. Will that override image previews?

Lastly, my workspaces are set to dynamic but I no longer have the ability to just drag windows over to the right. Even when using two or more, they still don't appear and I have to click on the icon to get to them. Not sure if this is a quirk somehow or what but it's annoying.

---

### Post by Frogs Hair on 2013-05-27
The Faenza  icon set has no effect on the thumbnail view in nautilus on my system .

---

### Post by cincinnatus13 on 2013-05-27
Thanks. I didn't think it should (and certainly saw no other tool in Gnome tweak tool to change it) but it's good to know for sure.

I'm just wondering what could've went wrong. I just installed 13.04 fresh and just have the latest stable updates.

---

### Post by Frogs Hair on 2013-05-28
It appears that dragging applications to different work spaces is possible in the right panel displayed in the overview, but not from desktop to that panel with my current settings .
 
Restart Shell: Alt + F2```
 r  
``` 

Restart Nautilus ```
nautilus -q
```

In the picture you see Chrome and I move it to a new space by dragging it downward.

---

### Post by cincinnatus13 on 2013-05-28
Yeah, I've restarted the shell and still can't get the right side workspace switcher up. It only shows up when I right click on the title bar and move a program a workspace down. Then if I close each program on that workspace, my workspaces disappear and then I have to click the program icon to get back to my open programs (ie, Nautilus closes on W2, it all goes blank. I have to click on the FF icon to get back to W1 (FF residing on W1.))

I'm starting to wonder if the minimize to desktop extension is borking my stuff somehow.

No clue on Nautilus previews though. Ran the code above and no change.

---

### Post by cincinnatus13 on 2013-05-28
Well, update for those who want to know how to fix this...

Nautilus (most images work now, maybe I need to rm the generated ones and I'll get them all) needs a command entered to change the ownership to the user for thumbnails.
[http://askubuntu.com/questions/211843/why-i-cant-see-the-thumbnails-in-nautilus](http://askubuntu.com/questions/211843/why-i-cant-see-the-thumbnails-in-nautilus)

Seems to have worked for most images (though ones that don't work don't appear any different in size or file type.)

Edit- fixed the whole Nautilus thing by deleting all items in the fail folder where thumbnails are stored. As of 3.6 (maybe earlier) this is located in ~/.cache/thumbnails

Hope that helps someone in the future.

---

