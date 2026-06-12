---
title: "Help with setting up two conky scripts"
date: 2011-11-10
forum: Desktop Environments
---

### Post by murderd2death on 2011-11-10
I'm having a hard time finding a guide for setting up two different conky scripts. Right now i got one for system specs on the right side of my desktop, and i wan to get one going for RSS feeds either up top or down bottom. I just have no idea how to run two at the same time. Any help?

---

### Post by werewolves on 2011-11-10
I've never tried it, but maybe if you had two different config files, and ran them with two different commands, it might work.

[http://conky.sourceforge.net/docs.html](http://conky.sourceforge.net/docs.html)

```
-c | --config= FILE
Config file to load instead of $HOME/.conkyrc
```

---

### Post by satanselbow on 2011-11-10
[http://crunchbanglinux.org/wiki/howto/howto_setup_multiple_conky_sessions](http://crunchbanglinux.org/wiki/howto/howto_setup_multiple_conky_sessions)

---

### Post by stinkeye on 2011-11-10
> **murderd2death said:**
> I'm having a hard time finding a guide for setting up two different conky scripts. Right now i got one for system specs on the right side of my desktop, and i wan to get one going for RSS feeds either up top or down bottom. I just have no idea how to run two at the same time. Any help?
If you just run conky it will load the config file @ **~/.conkyrc**
but you may also run conky using a specific config
ie **conky -c /path/to/config**

So if you named your configs **systemconky** and **RSSconky** you could start them with
```
conky -c /path/to/systemconky
conky -c /path/to/RSSconky
```

Let's say you have your conky configs saved in a conky folder in
your home directory.
Your startup script would look like...
**StartConky**
```
#!/bin/bash

sleep 10
conky -c ~/conky/systemconky &
conky -c ~/conky/RSSconky
```
The **sleep 10** command is to allow your window manager time to load 
before conky or you may have display problems.


...and when your working on your conkys it's good to have a script to toggle
conky on and off.
**ToggleConky**
```
#!/bin/bash

# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky 
else
 exec conky -c ~/conky/systemconky &
 exec conky -c ~/conky/RSSconky

fi
```

---

