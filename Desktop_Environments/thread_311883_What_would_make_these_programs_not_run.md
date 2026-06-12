---
title: "What would make these programs not run?"
date: 2006-12-03
forum: Desktop Environments
---

### Post by djsroknrol on 2006-12-03
I have a problem I hope someone can help me figure out. I had Beryl and XGL running on my compy when it crashed. I removed Beryl, but suddenly, Celestia, Stellerium, Search & Rescue and Uplink stopped working.

There's got to be a file that Beryl has upgraded that's corrupted and needs to be downgraded, but I can't figure out what one/ones that need to be replaced....

Anyone have any ideas on what I could do?

---

### Post by Rui Pais on 2006-12-03
hi,
how they fail? you have any error message when launch them from a terminal?

maybe tring to do a sudo aptitude purge celestia stellarium etc followed by a sudo aptitude install celestia stellarium ...

---

### Post by djsroknrol on 2006-12-03
Well, it varies...Uplink doesn't start at all, while Celestia, Flight Gear and Search & Rescue open windows but don't start the programs and then locks the computer up.

I can hear the monitor clicking on and off and the busy (spinning icon) shows and disappears and then reappears.

I've tried reinstalling them all and reinstalling them but get the same effect....

When Beryl-project had their crash, I lost the Dapper guide, so I'm at a loss as to what might be doing it. There has to be a common denominator with all of the programs that's causing this.

---

### Post by Rui Pais on 2006-12-03
uhmm... that should be something related with OpenGL/GLX libraries, since astronomy/sky visualizers use a lot of graphics resources.

Going back to a normal clean X-server/OpenGl state after a beryl or a compiz install as been reported several times and hard to get... 

You could try to remove/comment any XGL/Beryl repos on your sources.list, do an apt-get update and use synaptic to localize the changed packages by beryl on 'Installed (local or obsolete)'.
And then force a reinstallation of those packages with the Ubuntu versions. 

That should put things working normally again. Don't know if something goes wrong if you don't stay with a borked X server or something, so do it carefully.

---

