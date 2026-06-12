---
title: "Trackpad failure - Ubuntu 12 - Reload nescessary Compaq"
date: 2012-09-03
forum: Desktop Environments
---

### Post by mickymills on 2012-09-03
Hi Ubuntu Community,

My config is a Compaq Presario CQ62, using Ubuntu 12. The trackpad will cease working unexpectedly after a few hours of operation.

Usually there is a bit of load on, and a few Java Applications open (libreoffice, and Firefox feature whenever the fault eventuates).

I have the habit of leaving a Terminal window open, which I have used to reload my trackpad drivers with total success using the following:

To unload psmouse, do:
Code:
```
modprobe -r psmouse
```

Then reload it, using one of the following commands:
Code:
```
modprobe psmouse proto=bare
modprobe psmouse proto=exps

```
This is from the page [http://www.remastersys.com/forums/index.php?topic=2483.0](http://www.remastersys.com/forums/index.php?topic=2483.0)

can anyone offer a workaround on this very frustrating error?
:popcorn:

---

