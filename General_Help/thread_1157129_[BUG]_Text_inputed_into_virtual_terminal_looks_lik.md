---
title: "[BUG] Text inputed into virtual terminal looks like: ^[t^[h^[i^[s"
date: 2009-05-12
forum: General Help
---

### Post by learningcurb on 2009-05-12
Hi, I'm having a problem with my virtual terminals.  When I try to login to one of them, all the letters I type are prefixed with ^[. So for instance if I try to login as "user", the terminal prints out "^[u^[s^[e^[r" instead.

Naturally, it won't accept the password I send since it's probably also corrupt.  Switching to ctrl-alt-f7 and back sometimes fixes the problem and sometimes it does not.  Sometimes when I switch back to a virtual terminal, typing letters do nothing, but hitting enter still works. Sometimes hitting enter does nothing except for triggering the system bell and sometimes typing letters does nothing at all.

Does anyone have any ideas on what has caused this or how it can be fixed? I'm running an up to date version of Ubuntu 8.10 with LXDE installed.  It's possible it's a problem with the Xterm program that came with LXDE, however I'm not sure.  I didn't notice this problem before installing LXDE.

---

