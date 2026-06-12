---
title: "pypanel and openbox 3.3"
date: 2006-09-04
forum: Desktop Environments
---

### Post by moore.bryan on 2006-09-04
[I]i'm running dapper, kernel 2.6.7.11-686, and openbox 3.3.  since i upgraded openbox from ubuntu's 3.2.x, pypanel displays a border along its bottom.  i have rewritten the pypanel configs (both user and site specifics) to not include borders, but still it shows.  i've asked pypanel and openbox's forums, but no one had any ideas.  i've always gotten good help from this forum, so giving it a shot.  thanks, in advance.
[/I]--------------------------------
[I]got it fixed, thanks to the ob mailing list... if anyone else runs into the problem, just
```
sudo nano ~/.config/openbox/rc.xml
``` and add 
```
<keepBorder>no</keepBorder>
``` to the <theme> section.
--------------------------------
new edit!

ob developers saw the issue and released ob3.3.1.... no issues now.
[/I]

---

