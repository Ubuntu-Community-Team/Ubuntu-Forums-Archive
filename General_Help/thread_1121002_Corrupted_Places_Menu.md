---
title: "Corrupted Places Menu"
date: 2009-04-09
forum: General Help
---

### Post by odduck on 2009-04-09
Somewhere along the way (not sure when) my Places menu in my top toolbar got corrupted.  Where I'd expect to see links to my Documents, Music, Videos, etc. folders, I instead see two folders that look like they're labeled with gibberish.  When I try to open either one of them I get an error message that says "An error occurred while loading or saving configuration information for gnome-panel. Some of your configuration settings may not work properly".  When I click to see more details I get "Bad key or directory name: "/desktop/gnome/url-handlers/": Key/directory may not end with a slash '/'".

Any ideas on how to fix this or even to just go back to the default settings?

---

### Post by odduck on 2009-04-09
Well I figured it out myself. For some reason I was thinking I'd have to enter in something in the command line to return my gnome-panel to the defaults (something which I gleaned how to do from other threads while searching for a solution) but that didn't work.

Turns out the solution I used was much simpler than I thought it would be.  I just noticed that the gibberish folders were listed in the side bar of any nautilus window I had open (as well as legitimate folders and locations on my file system) so I just right-clicked and deleted them.  Then I dragged the folders over from the main window that I wanted to be there instead (Documents, Music, etc).

Man, I'm a noob.  I just hope this can help other people.

](*,)

---

### Post by schloss on 2009-04-11
I'm actually getting the exact same error, except it's from a panel launcher. In this case, I created a launcher for my home folder (by creating one on the desktop -- that one works fine -- and dragging it to the panel). Every time I try to use it, though, it gives me the "Bad key or directory name" error.

Does anyone know of a bug in drag-and-drop with the GNOME panels?

---

