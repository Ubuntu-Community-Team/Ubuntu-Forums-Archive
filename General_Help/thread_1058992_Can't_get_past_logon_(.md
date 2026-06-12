---
title: "Can't get past logon :("
date: 2009-02-03
forum: General Help
---

### Post by JRCavileer on 2009-02-03
The other day I was experimenting with the other desktop environments (kubuntu). Everything went well, I installed it, switched from gde to kde, but didnt like what saw. So I went back into Gnome and removed the kubuntu packages.

NOW, when i start up i get the kubuntu login screen, try to login using gnome but i get a page saying its not starting gde, and its starting kde....only i removed those, and it stays on the page.

Is there a way i can restore gde to default from terminal? or any other work-arounds?

---

### Post by phantom3113 on 2009-02-03
Have you tried changing the sessions at/on the login screen? (bottom-left>>options>>select session>>GNOME) There should be a similar method for KDE. I've never used it, but I imagine clicking the "session type" button should yield similar results. If that doesn't work, try this:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

That link has a terminal command that gets rid of anything KDE that was installed by adding the KDE desktop environment to Gnome as well as installing (or reinstalling) the Gnome Desktop. Note however, that you may need to follow a link if you don't run 8.10 (the link is for Intrepid only, but offers links for previous releases). As long as you have access to a terminal and the internet, that should fix you right up.

---

