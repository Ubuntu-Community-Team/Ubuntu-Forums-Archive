---
title: "Gnome logout script"
date: 2005-04-11
forum: Desktop Environments
---

### Post by nocturn on 2005-04-11
How can I have a script triggered when logging out of Gnome?
It has to run as the user that is logging out, so the GDM postsession is not very usefull.

I tried by creating a .logout file, but it is not run.
I know CDE used to have a dtlogout file and some WM's source .logout, so I'm hoping there is something similar for Gnome.

---

### Post by nocturn on 2005-04-21
Bump - still looking for this

---

### Post by audax321 on 2005-04-21
Not sure if this will work but you could make a script as follows and try it:

```
 
#!/bin/sh

#Bring up Gnome Log-out Screen and Choose to Logout
gnome-session-save --kill

#Commands to be run...
<command_1>
<command_2>, etc.

```

If this works though, you'll have to use the script to logout rather than using the System menu...

---

### Post by dare2dreamer on 2005-10-14
You probably need to run your other commands before killing gnome-session.

---

### Post by randyleepublic on 2007-01-16
Same question, but isn't there a script that is run when you click the button.  Seems like editing that would be the simplest thing, no?  If someone can confirm that there is no script, in other words that the session kill command is hard coded into the gui, then I will file a bug.  Cause there should be a script, don't you think?

Oh yeah, (light glowing over noob's head), grep for the command and maybe I'll find the script.  Will report.  Thanks for the clue!

---

### Post by randyleepublic on 2007-01-16
Nah.  It ain't nowhere to be found except in some binarys.   I guess that I'll write my own script and replace the gnome button.

---

### Post by habrys on 2007-04-03
You can add the code into the file:
/etc/gdm/PostSession/Default

(Just found it elsewhere and tried out. Works!)

---

### Post by henriquemaia on 2008-07-03
> **habrys said:**
> You can add the code into the file:
/etc/gdm/PostSession/Default

(Just found it elsewhere and tried out. Works!)

Thanks for posting this tip. :) 

I was precisely looking for this.

---

