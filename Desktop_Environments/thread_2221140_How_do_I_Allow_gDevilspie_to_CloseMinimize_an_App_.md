---
title: "How do I Allow gDevilspie to Close/Minimize an App only at startup, but allow it open"
date: 2014-04-30
forum: Desktop Environments
---

### Post by kschiff on 2014-04-30
I am trying to use gDevilspie to close an autostart application that is configured to remain running but be closed to the notification tray. Unfortunately, this works, but for obvious reasons, doesn't allow me to actually ever bring the application into focus to use it. Here's the raw code it's running. Is there a way to change this so that it only closes (or minimizes) upon startup?

```

    ( if 
( begin 
( is ( window_name ) "NixNote - Default Account" )
) 
( begin 
( close )
( println "match" )
)
)

```

Minimize works, but it's really a different behavior than I want. Taking Devilspie out of the mix, close keeps the app running minimized to the notification area. Minimize does something different. I'm looking for a way for it to close to the notification area, but still allow it to be opened from there...

---

