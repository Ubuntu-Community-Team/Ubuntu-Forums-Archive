---
title: "modifing GNOME &quot;boot process&quot;?"
date: 2005-12-21
forum: General Help
---

### Post by joft on 2005-12-21
Hi,

Can anybody tell me something about the "boot process" of GNOME (process of loading GNOME Desktop after logging in)?
I would like to start a daemon just *before* esd gets started, because on my System esd has to depend on that daemon (another sound daemon).

Is this possible and if yes, which (start-up) script do I have to change?

---

### Post by audax321 on 2005-12-21
Not sure about how to do that, but does this work?

```

#!/bin/sh

killall esd

if [ "$?" = "0" ]; then
  <put command to start daemon here>
fi

esd

```

This shell script will kill esd, start the daemon if the kill succeeded, then start esd again. To use it, copy the contents to a file (e.g. sound_daemon.sh) and then set the permissions to 755. Run the script in terminal by doing "sh <name of script>"

---

### Post by joft on 2005-12-21
audax321, thank you for your answer.

I already do it the way you wrote. But I like to *integrate* the start of my second sound daemon into the Gnome Desktop "boot process" (= loading of the Window Manager, Panels ....).

---

### Post by joft on 2005-12-24
Hi,

yesterday I found a way to start the above mentioned sound daemon: ~/.gnomerc.

This file is executed/sourced (directly) after logging in.

But now there is the next problem:
How do I tell GNOME to stop my second sound daemon after a logout?

---

### Post by kosmic on 2005-12-24
Your solution resides in the /etc/init.d/ :) just do a man init or have a look where ->[http://linux.about.com/od/commands/l/blcmdl8_init.htm](http://linux.about.com/od/commands/l/blcmdl8_init.htm)

---

### Post by joft on 2005-12-24
Hi kosmic,

hmmm, and which runlevel is used *after* logging out (NOT shutdown or poweroff)?
Isn't there a possibility (like the ~/.gnomerc file) for logout? (script which is executed/sourced after logout)

---

