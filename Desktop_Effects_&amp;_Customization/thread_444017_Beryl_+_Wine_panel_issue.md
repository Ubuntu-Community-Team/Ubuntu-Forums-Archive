---
title: "Beryl + Wine panel issue"
date: 2007-05-14
forum: Desktop Effects &amp; Customization
---

### Post by adhesivesynergy on 2007-05-14
I've been using Linux for a few months now so I've gotten rather comfortable with Beryl and editing xorg.conf and all the stuff that used to give me trouble....but one issue still vexes me and I haven't been able to find a solution!
     When I try to run a fullscreen app in wine (fallout or half life 2 etc) the gnome panel stays on top of the window. I can easily fix the problem by just switching back to Metacity while I play, but thats a little annoying and I would prefer a cleaner solution. Any ideas?

---

### Post by Cresho on 2007-05-15
I'm curious to see if this will work for you.  These settings allowes me to play certain games which require 3d acceleration but sometimes I have mouse control problems on certain games.

1. Going into the Beryl settings manager->General options->Advanced, I ticked the "unredirect fullscreen windows" and "enable workarounds for certain wine legacy games"

2. In addition, I also used the beryl manager->advanced rendering options->rendering options->and checked force aigxl. Now this combo made my setup run very nice. one last thing, i noticed I had problems with some-things so I clicked on disable gl under beryl manager->advanced rendering options for better performance.

Hope this works.  I also revert to metacity sometimes but I just reinstalled.  I'm trying alot of things until i get it right.  I even managed to find the anisotrophic and antialiasing commands for bootup with beryl for smooth edges. :guitar:

---

### Post by adhesivesynergy on 2007-05-15
Groovy, I'll give it a try and see if it works, I'll clarify that the games run perfectly well, just with an annoying panel on top of them. Also kudos on working in the :guitar: smiley :lolflag:

---

### Post by adhesivesynergy on 2007-05-15
> **Cresho said:**
> I'm curious to see if this will work for you.  These settings allowes me to play certain games which require 3d acceleration but sometimes I have mouse control problems on certain games.

1. Going into the Beryl settings manager->General options->Advanced, I ticked the "unredirect fullscreen windows" and "enable workarounds for certain wine legacy games"

2. In addition, I also used the beryl manager->advanced rendering options->rendering options->and checked force aigxl. Now this combo made my setup run very nice. one last thing, i noticed I had problems with some-things so I clicked on disable gl under beryl manager->advanced rendering options for better performance.

Hope this works.  I also revert to metacity sometimes but I just reinstalled.  I'm trying alot of things until i get it right.  I even managed to find the anisotrophic and antialiasing commands for bootup with beryl for smooth edges. :guitar:

sadly it didn't work, I still get the panel over my fullscreen windows. This only seems to happen in wine

---

### Post by macabro22 on 2007-06-03
I get the panel on top of my fullscreen counterstrike as well

---

### Post by notwen on 2007-06-03
Could you simply auto-hide the panel during the game play?

---

