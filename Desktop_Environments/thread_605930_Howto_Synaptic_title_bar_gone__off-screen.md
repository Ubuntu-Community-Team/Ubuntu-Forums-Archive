---
title: "Howto: Synaptic title bar gone / off-screen"
date: 2007-11-07
forum: Desktop Environments
---

### Post by DeusEx on 2007-11-07
**problem**:
Synaptic won't minimize, can't be dragged around and the titlebar is off-screen (see screenshot), e.g. the window is permantently displaced.
NOTE This has nothing to do with Compiz or missing window managers, except for the displacement of the window was initially caused by Compiz.

**solution**:
edit /root/.synaptic/synaptic.conf:
change the lines
```

windowX "0";
windowY "0";

```
to:
```

windowX "10";
windowY "10";

```

---

