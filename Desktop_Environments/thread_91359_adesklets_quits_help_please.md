---
title: "adesklets quits help please"
date: 2005-11-17
forum: Desktop Environments
---

### Post by ahh_dee on 2005-11-17
Hey iam trying to make Adesklets work with my fluxbox.  I am able to have the apps start up with the apps config file for fluxbox but they automatically dissapear if i run a program.  when I try command "adesklets" in a terminal nothing pops up.  its like it resets its self can anyone help?

---

### Post by Xian on 2005-11-26
[QUOTE=ahh_dee]Hey iam trying to make Adesklets work with my fluxbox.  I am able to have the apps start up with the apps config file for fluxbox but they automatically dissapear if i run a program.[/quote]  
 
I would try starting it instead by using the ~/.fluxbox/startup file.

```
<snip>
 Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
idesk &
adesklets &
xscreensaver &
<snip>
```

[QUOTE=ahh_dee]when I try command "adesklets" in a terminal nothing pops up.  its like it resets its self can anyone help?[/QUOTE]

Start the desklet by running the applicable desklet_name.py file.
And don't run programs like nautilus...

---

