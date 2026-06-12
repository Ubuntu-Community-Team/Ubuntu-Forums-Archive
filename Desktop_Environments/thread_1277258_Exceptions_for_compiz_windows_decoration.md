---
title: "Exceptions for compiz windows decoration"
date: 2009-09-28
forum: Desktop Environments
---

### Post by RikoW on 2009-09-28
Dear all,

is there a possibility to except certain windows from the windows decoration in compiz?

Background of the questions is the following. I often connect to an XP machine using seamless RDP. However, the seamless windows have to frames:

1) the frame that comes from XP in the XP theme
2) the proper decoration from the ubuntu windows manager

I'd like to get rid of the frames of 2). When I turn of windows decoration in compiz altogether, no window has a frame anymore (as expected :). But I have no idea how to set it, that all native ubuntu windows are decorated, but all windows coming through RDP are not!!

Any ideas?

Thanks and cheers,

            Riko

---

### Post by RikoW on 2009-09-28
Never mind! One just keep on playing before posting :)

I just added 

```
(any)  & !(class=SeamlessRDP)
```

in den "Decoration windows" field in the plugin config. 
Clicking on "+" and using the "grab" button lets you determine the windows class which is used.

Cheers,

          Riko

---

