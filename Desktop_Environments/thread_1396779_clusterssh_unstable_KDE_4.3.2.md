---
title: "clusterssh unstable KDE 4.3.2"
date: 2010-02-02
forum: Desktop Environments
---

### Post by eschoeller on 2010-02-02
In one of the last KDE 4 updates, or perhaps when moving from intrepid to karmic, using the application "clusterssh" has become completely unstable. 

Some of the symptoms I have experienced:

1. Window focus problems. Clicking on a single xterm window from a group of xterms controlled by clusterssh does not switch focus to that window. Focus stays on the clusterssh application, so output is still directed to all xterms. Previously, I could interact with a single xterm, or with all of them.

2. Clipboard problems. After using clusterssh for awhile, and perhaps using the clipboard within clusterssh cutting and pasting between other applications completely fails. The only work-around is to completely log out of your kde session, hence killing your clusterssh sessions.

3. xterm window manipulation. At some point during a clusterssh session, all xterm windows become locked in place. You can't move them at all. This also leads to focus problems described above. The work-around for this is to switch virtual desktops, and then switch back to your clusterssh session, and now the windows can be manipulated and re-organized again.

Please if anyone else has noticed these problems with clusterssh, or has some potential work-arounds I would be happy to hear about it!

---

### Post by Tolaris on 2010-05-04
I have the same problem.  I really miss clusterssh.

I'm using keyboardcast now, which lacks some of the better features of clusterssh but otherwise works.

---

### Post by eschoeller on 2010-05-04
I'm wondering if this should be posted as a bug report to gain some more traction on the issue?

---

### Post by Tolaris on 2010-05-04
[https://bugs.launchpad.net/ubuntu/+source/clusterssh/+bug/488138](https://bugs.launchpad.net/ubuntu/+source/clusterssh/+bug/488138)

---

