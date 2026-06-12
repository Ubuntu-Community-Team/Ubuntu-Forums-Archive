---
title: "Changing GTK theme for individual applications"
date: 2007-08-05
forum: Desktop Effects &amp; Customization
---

### Post by craigyjack on 2007-08-05
I have searched far and wide trying to figure this out.
I am trying to figure out how to change the GTK theme for individual applications (so that an application will open using a different GTK theme than my normal GTK theme).
I have tried inserting this GTK2_RC_FILES=/path/to/gtkrc/file before running the command for the application. i thought i had this working, and i believe it may have worked a couple times, but now it is not working for me at all.
secondly, this definitely doesnt work with a launcher (like on a panel). i try inserting this into a command in the launcher, but i think it is trying to excute this line as a command, (also in terminal i saw one time that it was looking for it in my home directory for some odd reason).

Does anyone know a way that i can get an application to open using a different GTK theme than the GTK that is being used regularly. Preferably a way I could set it up in a launcher also, so that the program would run from the launcher in a different GTK theme.

I would extremely appreciate if anyone could share any information about this as I have yet to figure this out. 
Thanks,
Craig

---

### Post by craigyjack on 2007-08-07
i have managed to get this working using "env GTK2_RC_FILES=<path> <command>", but it seems to only be working with Human theme, and not other themes (even though they work fine as regular gtk themes in gnome-theme-manager). if i use a theme other than Human it seems to not work and then just go back to my theme that is in gnome-theme-manager. anyone know how i could get this going so that it with use other themes??

---

