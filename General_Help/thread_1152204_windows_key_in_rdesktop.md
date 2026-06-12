---
title: "windows key in rdesktop"
date: 2009-05-07
forum: General Help
---

### Post by sq377 on 2009-05-07
I've been using an altered ltsp client to create kind of a fat thin client (more like thinstation).  It works well except that the windows key is toggled, not pushed down to be active.

The only thing I'm running in the xsession is this:
```
#!/bin/sh
metacity &
## Debugging
#xterm &

cd /opt/shrimp
exec /opt/shrimp/shrimp

```

"shrimp" does not alter the keymap at all, would metacity do this? or is there something else I should add in here to get the proper response from that key?  It may be other keys as well, but this is the first one the clients have noticed.

Thanks!

---

