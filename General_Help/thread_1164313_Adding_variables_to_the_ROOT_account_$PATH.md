---
title: "Adding variables to the ROOT account $PATH"
date: 2009-05-19
forum: General Help
---

### Post by kofkof_00 on 2009-05-19
Hello All,

I'm trying to add variables to the root $PATH 

I found this while researching the subject.

[http://sahasranaman.com/2008/02/05/path-variable-in-ubuntu/](http://sahasranaman.com/2008/02/05/path-variable-in-ubuntu/)

"Unlike most other linux distros, the PATH environment variable cannot be set in Ubuntu by adding an assignment statement in the ~/.bash_profile script."

His suggestion was to edit the /etc/environment

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games" <---- Insert in here

Is there a different way, a *proper* way to add variable to the ROOT $PATH?

---

### Post by cdenley on 2009-05-19
> **kofkof_00 said:**
> Hello All,

I'm trying to add variables to the root $PATH 

I found this while researching the subject.

[http://sahasranaman.com/2008/02/05/path-variable-in-ubuntu/](http://sahasranaman.com/2008/02/05/path-variable-in-ubuntu/)

"Unlike most other linux distros, the PATH environment variable cannot be set in Ubuntu by adding an assignment statement in the ~/.bash_profile script."

His suggestion was to edit the /etc/environment

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games" <---- Insert in here

Is there a different way, a *proper* way to add variable to the ROOT $PATH?

You could change the PATH variable by editing ~/.bashrc, but the correct way is probably to edit ~/.profile for user-specific settings. /etc/profile should be used for global settings.

---

### Post by kofkof_00 on 2009-05-19
This isn't for a **user** specific parameter. (unless you classify root as a regular user...)

I have a program invoked by root, early into the startup, not by a specific user account, but by root. I need to set a global $PATH variable so that it will know what directory to look into.  

I expected to find a file that contained something very much like this:

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

(/etc/profiles)


And that I could insert something like this:

PATH="/usr/local/sbin:***/some/path/to/an/app:***/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

into it, reboot and voila.

This is something others have achieved, in RH, I'm trying to get it working in 8.10

---

### Post by cdenley on 2009-05-19
Scripts started during boot do not use root's environment variables. The PATH variable is set in "/etc/init.d/rc".

---

### Post by kofkof_00 on 2009-05-19
Let express my deepest gratitude at the help you have provided.

After adding to /etc/init.d/rc I have success.


Thank you ever so much. :D

---

