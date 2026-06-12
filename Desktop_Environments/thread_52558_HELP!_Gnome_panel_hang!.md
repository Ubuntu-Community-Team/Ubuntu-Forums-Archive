---
title: "HELP! Gnome panel hang!"
date: 2005-07-28
forum: Desktop Environments
---

### Post by leslie on 2005-07-28
Hi

I have a small problem, well quite a large one really, my gnome-panel keeps hanging! Also the clock and the speaker icon are missing!

I have used the command ‘killall gnome-panel’ and restarted the panel many time but it still comes back with no clock or usage.  

I have logged off and logged back in but still no joy. Can anyone help?

What would cause the gnome-panel to freeze like that and is there anything I can do to stop it from happening in the future?

Help I want to get beck to using my lovely clean install!

---

### Post by Sam on 2005-07-28
I don't know why is your panel freezing, but to add elements on it, just right-clic on the panel and select 'Add to panel'. In your case you should add 'Clock' and 'Volume control'.

---

### Post by jackocleebrown on 2008-05-28
Hi,
I had a similar problem and think I have managed to work around it. I only have the issue when I use my ubuntu laptop at work. The symptoms are the same as you describe - the panel does not load on login. I connect to the internet at work through a proxy server which required authentication - I don't have this setup by default because it messes up my settings for home. I think that this was the problem for me, something on the panel was trying to get access to the net (perhaps the weather applet or the calendar (via evolution)) and hanging because it could not authenticate with the proxy server - I found that after I setup the proxy using "gnome-network-preferences" everything worked fine. I guess that you can also work around it just by unplugging your ethernet connection (turn off your wireless) before you login. Give it a go.

Jack.

---

