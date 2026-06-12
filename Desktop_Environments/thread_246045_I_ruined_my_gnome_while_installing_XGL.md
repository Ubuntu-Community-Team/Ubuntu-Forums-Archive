---
title: "I ruined my gnome while installing XGL"
date: 2006-08-28
forum: Desktop Environments
---

### Post by Canute on 2006-08-28
First I'd just like to say that this is entirely my fault and I don't blame neither gnome, xgl nor linux for it.

Anyways, first what i did was that i installed XGL on desktop worked after like 30 seconds and therefor I decided to the same on my laptop. Since I have an Nvidia card for on my desktop and ATI card on my laptop i decided to use a different How-to. 

I found one for ATI, and then after some apt-get's it suddenly started complaining about samba. I couldn't really find out what the problem was so I decided to go over to another How-To ... I started apt-geting again and then it started complaining about samba. I noticed the update tray icon, and according to that I should do "apt-get install -f". Now here's where the trouble starts. It installed everything from the first how-to and the second how-to. The first one was supposed to incorporate XGL right into my original gnome, and the second added another session (like kde). The second one works like a charm, however, when I enter normal gnome every new window i open is placed up in the left corner, and they don't have any titlebar (where the title and the minimize, maximize and close buttons are). If you have tried the "nonXgl" thing for use with games and such, it's exactly the same. Whenever I try to logout of the normal gnome, it all seems normal until you're supposed to see the login screen and then it just becomes black.

Now, the "failsafe" gnome works like it's supposed, if it wasn't for the fact that I am missing the battery/power icon thingy I would have just used that. I noticed some message when it starts that it doesn't use any startup scripts. 

I have tried removing compiz-gnome, compiz and reinstalling ubuntu-desktop. No difference.

Is it possible to remove xgl from my startup scripts? Where would I go about and find that?

Any other suggestions for getting this fixed?

---

### Post by guitarmaniac on 2006-08-30
I have the same problem, I think compiz is screwing up metacity for gnome but I've tried removing XGL and reinstalling metacity and that didnt work either.]
(*,)

---

### Post by ayoli on 2006-08-30
try in a terminal:
```
rm -rf ~/.gnome* && rm -rf ~/.gconf*
```
then restart gnome.
regards.

---

