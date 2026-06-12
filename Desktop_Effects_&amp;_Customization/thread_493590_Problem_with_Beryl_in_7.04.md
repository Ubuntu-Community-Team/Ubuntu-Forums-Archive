---
title: "Problem with Beryl in 7.04"
date: 2007-07-05
forum: Desktop Effects &amp; Customization
---

### Post by bigboy2490 on 2007-07-05
I installed Beryl on Ubuntu 7.04, and it works, except for what appears to be a glitch with the 3D Desktop cube.

I had programs open in two different workspaces, yet when I go to the 3D cube, only the workspace that I'm currently in shows up.  The windows I have open in that workspace show up maximized, and when I look at another workspace on the cube, I can see the windows from my current workspace in there, minimized, despite the fact that there should be other programs in there.
I looked through Beryl's settings extensively, wondering if I had checked some sort of cloning box or something similar, but to no avail.

Any help is greatly appreciated.

---

### Post by Waappu on 2007-07-06
Hi

You can reset all Beryl settings by typing in terminal```
rm -r ~/.beryl
rm ~/.beryl-managerrc
```

---

