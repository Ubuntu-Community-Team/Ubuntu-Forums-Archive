---
title: "Quality of Service (QoS) on the ubuntu update repositories"
date: 2005-09-21
forum: Desktop Environments
---

### Post by Monkey77 on 2005-09-21
Hi,

Does anyone have a script of how to configure ubuntu to set a low priority for fetching the updates from the repositories?

With QoS I should be able to carry on browsing the Internet without noticing a real slowdown.

Regards
Phil Hannent

---

### Post by az on 2005-09-21
[QUOTE=Monkey77]Hi,

Does anyone have a script of how to configure ubuntu to set a low priority for fetching the updates from the repositories?

With QoS I should be able to carry on browsing the Internet without noticing a real slowdown.

Regards
Phil Hannent[/QUOTE]


Well, apt-get uses wget with which you can limit the rate.  I guess there is some sort of setting like this in the apt configuration.  I am not sure if the synaptic in Breezy gives you this option.  If not, then it is a feature request!

Another way would be to use traffic-shaping software, as you mention.  There are a few (like wondershaper) but I have never used them.

---

