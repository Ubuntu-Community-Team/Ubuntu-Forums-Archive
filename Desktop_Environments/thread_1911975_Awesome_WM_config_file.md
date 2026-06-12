---
title: "Awesome WM config file"
date: 2012-01-19
forum: Desktop Environments
---

### Post by AndrewZorn on 2012-01-19
Please excuse me if this isn't an appropriate place to ask. I've been trying to figure this out for DAYS now.

Everything says to copy the rc.lua file from /etc/xdg/awesome to ~/.config/awesome... and I thought I was familiar with how this works.

But when I make changes to 'my' rc.lua, nothing happens. Eventually I figured out making changes to the /etc/xdg rc.lua are visible. I can completely delete the user folder rc.lua and nothing happens; deleting (by renaming) the /etc/xdg rc.lua causes Awesome to not start.

I'm on 11.10 with a CR-48, if it matters.

Thank you for reading.

---

### Post by GafftheHorse on 2012-02-02
Andrewzorn

I've just recently set up Awesome myself. I found  this a good starting point.

Ref: [http://compsoc.tardis.ed.ac.uk/wiki/AwesomeWM_guide](http://compsoc.tardis.ed.ac.uk/wiki/AwesomeWM_guide)

Specifically the text under the heading "Configure Awesome!"

Check that you've not missed anything copying the /etc/xdg/awesome to ~/.config/awesome

I followed this next one after:
Ref: [http://awesome.naquadah.org/wiki/My_first_awesome](http://awesome.naquadah.org/wiki/My_first_awesome)

---

### Post by Afisamuleal on 2012-06-20
I have the same problem. There is nothing wrong with my spelling skills, but there is something wrong with the pathing.

For some reason the path is resolving to /etc/xdg/awesome/rc.lua instead of /home/user/.config/awesome/rc.lua ...

---

