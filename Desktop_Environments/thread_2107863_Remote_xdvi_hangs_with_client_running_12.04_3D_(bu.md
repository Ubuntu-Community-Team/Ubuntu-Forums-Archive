---
title: "Remote xdvi hangs with client running 12.04 3D (but not 2D)"
date: 2013-01-22
forum: Desktop Environments
---

### Post by Dr Kayak on 2013-01-22
Working from home, I run 'latex filename' on a remote server, where 'filename.tex' is a file of LaTeX code in which a PostScript file (such as a graph from R) is embedded via the graphics package.  I then do 'xdvi filename', and a window comes up on the client display.

When running Ubuntu 10.04 formerly, and Ubuntu 12.04 2D currently (on the same client, connecting to the same server), the display is immediate.  When running Ubuntu 12.04 3D (Unity), the page containing the PostScript image will often 'hang', i.e., it will be only partially drawn, and stay that way for as much as a minute or two.

Based on my search results, I'd say no one else in the universe is interested in doing this, but you never know.

---

