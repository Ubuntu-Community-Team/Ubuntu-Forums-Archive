---
title: "Distorted Font on Dell Latitude CPi 266XT"
date: 2006-09-15
forum: Desktop Environments
---

### Post by planetg on 2006-09-15
I've just attempted to install Ubuntu onto my old Dell Latitude CPi 266XT which seemed to go rather smoothly, until it finished and I was left with a maximum resolution of 800x600 and a very scarily distorted font. 

After some fiddling I managed to find a way to make the font clear, by clicking on 'Fn' and 'F7' which says Font. However, this made my screen shrink to about half the size and position itself at the top left.

I assume I need some driver to sort this, but have been searching online and found nothing useful.

If anyone has any ideas I'd much appreciate it...

Cheers

Ray

---

### Post by Conspiracy on 2006-10-03
I just solved this problem last night.  I was having the exact same issue with the laptop you mentioned. (technically I'm using Xubuntu but this all still applies).

I've been using Linux for all of 4 days now so keep that in mind.  

It's not a driver issue so much as a settings issue.  You've got to edit the xorg.conf file.  This is what you Screen section should look like:
```

Section "Screen"
        Identifier "Screen0"  #leave this line alone in yours
        Device     "Card0"    #leave this line alone in yours
        Monitor    "Monitor0" #leave this line alone in yours
        DefaultDepth 16       #Change this line in yours
        SubSection "Display"  #This is the only display SubSection I kept
                Viewport  0 0 #I'm pretty sure this line isn't necessary
                Depth     16
                Modes     "1024x768"
        EndSubSection
EndSection
```

It won't load the 1024x768 in 24 bit mode but it can in 16 bit mode.  I also upped the H and V rates in the Monitor section, but I don't remember those settings off the top of my head (maybe I'll edit this later with that info too).

You may want to consider using Xubuntu.  It's a lighter install... but what do I know my sound doesn't work yet.  That's next.

---

