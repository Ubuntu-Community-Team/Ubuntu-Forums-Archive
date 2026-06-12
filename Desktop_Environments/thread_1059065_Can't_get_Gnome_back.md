---
title: "Can't get Gnome back"
date: 2009-02-03
forum: Desktop Environments
---

### Post by JRCavileer on 2009-02-03
The other day I was experimenting with the other desktop environments (kubuntu). Everything went well, I installed it, switched from gde to kde, but didnt like what saw. So I went back into Gnome and removed the kubuntu packages.

NOW, when i start up i get the kubuntu login screen, try to login using gnome but i get a page saying its not starting gde, and its starting kde....only i removed those, and it stays on the page.

Is there a way i can restore gde to default from terminal? or any other work-arounds?

---

### Post by taurus on 2009-02-03
How did you remove KDE?

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

You can install Gnome again from a prompt if you wish.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by JRCavileer on 2009-02-03
I used synaptic :/

And i tried installing gnome again, but get the same message saying something along the lines "cant start gde because kde is default"

So I'm bound to the log in screen :(

---

### Post by taurus on 2009-02-03
Try removing the KDM.

```
sudo apt-get remove kdm
```

---

### Post by JRCavileer on 2009-02-03
I fixed it, I ran a command to make gde default, then removed kde the proper way, thank you guys.

---

### Post by nilsA on 2009-07-10
> **JRCavileer said:**
> I fixed it, I ran a command to make gde default, then removed kde the proper way, thank you guys.

It's been a long time since this post, but as I am trying to achieve the same - what is the command for "make gde default"?

I ask this, because I have a netbook that seems to wipe XP when I install Ubuntu on the second partition or "D:" in windows-lingo, so I'd rather not take any chances.

---

