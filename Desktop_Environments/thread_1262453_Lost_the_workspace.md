---
title: "Lost the workspace"
date: 2009-09-09
forum: Desktop Environments
---

### Post by jeannacav on 2009-09-09
Now I have done it!

I was having cursor problems with the workspace switching on me. I had just read the manual and decided to see if I could have only one workspace for a while to save on my learning curve.

I clicked 'remove from panel' and now nothing on any panels works at all.
I can see what they are from the hover function, but I cannot click on anything to open it at all!

Is there a way to restore the workspace...(and hopefully only have one, but I'd be happy with the original 2 for now.)

thanks,

jeanna

---

### Post by jeannacav on 2009-09-09
OK I got it back

So, here is the problem,
I am not able to control the workspace. I have no idea what cursor motion sets it off, but suddenly I get a message from off screen!! I wish this were in the help where it is prominent! This is crazy behavior.

jeanna

---

### Post by earthpigg on 2009-09-09
hi,

one option you will always have with any Ubuntu application is to delete its corresponding "dotfile" in your /home/your-username-here/ to restore it to all of its default settings, like the day you installed it.

open the file browser, and find your home folder.

click view -> show hidden files.

all the hidden files and folders that start with a dot (.) are dotfiles.

/home/your-user-name/.gconf/apps/panel is where gnome-panel keeps all its settings for you.

delete it, and it will fall back to default settings.


if you are fed up with pointing and clicking around to try to fix the panel, go ahead and delete that 'panel' folder. 

double check to ensure you aren't deleting the wrong thing!

log out, and back in for changes to take effect.

---

### Post by jeannacav on 2009-09-10
Thank you earthpigg,

At the time I asked for help I was not able to open a new finder window. Nothing but hover was working.
The crazy behavior of the other workspace came alive and zoomed in front of me (2 times before I could catch it) and it asked me to cancel my order. I did and everything is OK NOW.

I hope I can learn how to move around before I need to dig into the terminal. 

I appreciate your help.

jeanna

---

