---
title: "Strange problem with my network connection"
date: 2006-09-19
forum: Desktop Environments
---

### Post by Regord on 2006-09-19
It all started with Automatix.  My install was working great and I was happily customizing and installing apps.  Then I launched Automatix and thought I'd speed things up.  Well, I've got a lot more apps but now I can't access the internet. 

When I login, I can immediately launch Firefox and get to my homepage but very shortly after that I'm unable to go anywhere.  I'm not able to refresh my homepage and Synaptic won't install the updates that it says I need.  

I tried pinging my router and got a response (even after the browser locks up) but I can't get any response from my DNS servers.  My web connection is working as I'm posting this from my Windows Box.  I've also verified my card settings (IP, DNS and Gateway IP addys).

I don't even know how to start troubleshooting this or even what to google.  Can anyone help or is it just easier to reinstall?

---

### Post by Regord on 2006-09-19
Issue resolved.  Looks like during the installation of all that new software, the default gateway device became unselected.  I simply selected eth0 and my network connection is back up and running.  YAY! :)

---

