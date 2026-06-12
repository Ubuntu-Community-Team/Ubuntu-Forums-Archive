---
title: "Network Monitor needed."
date: 2005-08-27
forum: Desktop Environments
---

### Post by nicholaspaul on 2005-08-27
I have a network with a couple of Ubuntu machines and an OSX laptop. I want to be able to watch other monitors from my laptop, in real time. I know this is possible on Windows networks, what about linux? Is there an app, even one I can run from the Ubuntu machine remotely via ssh, to view what is going on on the Ubuntu machine from the laptop?
I would even settle for a GUI that would log everything going on with the ubuntu machine.

---

### Post by Gerie Langeveld on 2005-08-28
Try gkrellm.
It's a system monitor which can run in client/server mode. This means you can install the server on the Ubuntu machines and run several clients on your laptop to connect to them and see what's going on.
Search for gkrell in Synaptic to see all the plugins it can use.

I am not sure how this works on OS X. Maybe you need to install X11.

---

### Post by nicholaspaul on 2005-08-29
Hey, thats not bad. Thanks for the tip :) I want a little more info tho, like EXACTLY what's going on at the terminal. Are there any apps that provide a live screenshot?

I installed and ran it from X11 and it works great. I do most of my Ubuntu work that way, as perverse as it sounds.

---

