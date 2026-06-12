---
title: "questions for the xfce heads out there."
date: 2007-07-04
forum: Desktop Environments
---

### Post by the bored majority on 2007-07-04
i run litestep on my xp desktop (using litestep since win'98) and love the customization and using the full screen. winkey brings up the menu when i'm browsing so no need for the taskbar. all running tasks are grouped together in a nice list in the litestep menu.

i was wondering if i could do this in xfce? i noticed you can add commands to the panel that show running tasks/icons. i would like to add a list like this to to the popup-menu or is it possible to add a panel to the menu so all this shows up?

oh and one last thing, if any of the above can be done, is it possible to just remove the last panel completely? everytime i try to get rid of it i get an error message saying [you cant remove the last panel, would you like to quit].

i know fluxbox is more akin to litestep (litestep being build off the concept of blackbox and all) but i just like using xfce on my laptop more.

---

### Post by kerry_s on 2007-07-04
what?
can you make your questions more understandable?

are you talking about the middle mouse click on the desktop?
and what last panel?
can you post a screenshot with xfce4-shooter so we can have a look?

also xfce4 has a lot of keyboard settings preinstalled, look in the settings>keyboard>shortcuts it might have key shortcut's for what you want.

---

### Post by the bored majority on 2007-07-04
yeah, i guess a screenshot would help :) sorry. the image is taken from the wikipedia entry on xfce

i managed to get rid of the panel (by crashing it actually). so that really isn't a problem now.

in litestep all the running tasks show up in the menu. this is what i would like to do in xfce if possible.

---

### Post by kerry_s on 2007-07-04
okay that's what i was thinking. did you check if there a keyboard short cut for the middle click menu, if there is you can put that command into the main menu. i'm not using xfce4 so i can't look. you just need to find the command that shows that menu, then just use the menu editor to add it where you want. i'm not sure if it can be done as my xfce4 is on my main computer, which is down right now(i'm rebuilding it), so i'm on a old laptop running fluxbox.

---

### Post by PARO on 2007-07-04
The middle mouse click on the desktop should do that. Go to settings>desktop preferences> and under the behavior tab make sure "show window list on middle click" is enabled.

This is the command to use to get to the task list in xfce> xfdesktop -windowlist

But I'm not sure how to integrate that into the main menu if that's all you wanted to know.

---

### Post by bapoumba on 2007-07-04
(hello Kerry :))
This (middle click on desktop)?

Edit: Sorry, did not get the notification for post just above mine...

---

### Post by the bored majority on 2007-07-04
thanks for the help. i guess it cant be added as sidemenu but thats cool. i didn't know you could add the window list command to the menu. :)

again, thanks for the help.

---

### Post by kerry_s on 2007-07-04
> **the bored majority said:**
> thanks for the help. i guess it cant be added as sidemenu but thats cool. i didn't know you could add the window list command to the menu. :)

again, thanks for the help.

What? just add the command to you menu, it will call up the task list.

look at "bapoumba"(thanks bapoumba) pic it shows the "edit menu" click on that, then click wher you want to put it in the menu and click the + sighn(or use the menu at the top select new launcher), then put the command that "PARO" provided.
looks something like this:

Name: Show tasks 
Command: xfdesktop -windowlist

You can even put that in a launcher on the panel if you want, it's not as small as yours, but then thats not dealing with 4 desktops.

**Can someone do it and post a pick for him?**

---

### Post by the bored majority on 2007-07-04
that's what i did. i meant it's cool that it can't be added as submenu. like if i where to hightlight the entry it would show all the running tasks in a submenu like litestep does on my windows box; like the mockup pic i posted above.

 i added the command itself to the menu as an entry and now it shows the running tasks when i click it which is fine. works just as well as the other way.

sorry i wasn't that clear in my posts; i've been a bit out of it today.

again, thanks for everyone's help.

---

### Post by kerry_s on 2007-07-05
okay i think i got you, you mean like a mouse over instead of having to have to click it.
i'm sure there's away, but i would have to run some test's, which of course i can't do since my main system is down for rebuild. maybe in the future i'll revisit this. ;) take care.

---

