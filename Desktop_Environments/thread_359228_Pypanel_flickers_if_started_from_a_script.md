---
title: "Pypanel flickers if started from a script"
date: 2007-02-11
forum: Desktop Environments
---

### Post by GnuKemist on 2007-02-11
Running openbox on my Feisty HERD 3 via a script (shown below) that gets executed upon login in.  I noticed that pypanel keeps flickering and won't even display opened applications in the panel.  However, killing it and starting it from the console fixes it.  I was wondering if anyone has any ideas or suggestions?

```
#!/bin/bash
gnome-settings-daemon &
gnome-volume-manager &
gnome-power-manager &
Esetroot -s ~/images/wallpaper.png &
pypanel &
update-notifier &
exec openbox
```

Cheers,

Og

---

### Post by baekster on 2007-03-10
I am getting the same probelm.  I'm using Edgy with openbox, gnome-power-manager, pypanel.  Any help would be appreciated.  Oh, and the CPU workload goes to 99% once it starts flickering.

---

### Post by DagMan on 2007-04-08
pypanel needs to start after the exec openbox.  This isn't possible to do by putting it in the script because nothing after `exec openbox` will be run.  I don't run openbox but I had this same exact problem in fluxbox.

The easiest way around it was to have the script call another script before the `exec openbox` command and have the script sleep for an amount of time so that openbox is started and running and then it launches pypanel, so for example:

#!/bin/bash
gnome-settings-daemon &
gnome-volume-manager &
gnome-power-manager &
Esetroot -s ~/images/wallpaper.png &
update-notifier &
pypanel-handler &
exec openbox

And then make a script called pypanel-handler which is just something like this:

#!/bin/bash
sleep 5
pypanel &

The idea is not to start pypanel until openbox is up and running.
This worked for me except that my script happened to be in python along with some other junk but I really doubt that would make any differance and I think what is important is that pypanel's graphics start after openbox's graphics.

This method might make terminals launced from pypanel unable to use an ssh-agent that launced the window manager since they won't be children of it and that's the only thing I've found that needing working around.  It doesn't look like an issue in your case though.

---

### Post by moore.bryan on 2007-04-12
*this didn't work for me at all, but i may have a different issue.  i find the only time pypanel flickers is when i start-up sylpheed--no other programs, just sylpheed.  weird.*

---

### Post by dbbolton on 2007-04-28
i installed pypanel, but keep getting "command not found"

---

