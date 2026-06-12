---
title: "F-spot external handler"
date: 2008-01-01
forum: Desktop Environments
---

### Post by viniosity on 2008-01-01
I'm running XFCE4 and just loaded F-spot.  When I try to authorize my flickr account I get an error that says

> 
There was an error invoking the external handler...There was an error launching the default action command associated with this location." 


I've run both 
```

sudo update-alternatives --config x-www-browser 

```

and also edited the Desktop setting in the g-conf editor to use firefox instead of epiphany-browser (/desktop/gnome/applications/browser).  Neither seems to have worked. Is there another trick to get f-spot to launch firefox?

nevermind-- found it in the g-conf editor url-handlers.

---

