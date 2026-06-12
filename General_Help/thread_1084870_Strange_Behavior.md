---
title: "Strange Behavior"
date: 2009-03-02
forum: General Help
---

### Post by idxsem on 2009-03-02
Install - Ubuntu 8.10

This install has been working flawlussly for 5 months for me.  Whatever I throw at it it handles.   Until now and it is probably something stupid I did.  I was installing an applicaiton that required GNOME.  So I logged out and under OPTIONS selected (2)GNOME --> Change Sessions.   And then logged back in as it asked me to make GNOME my default.  So I said sure.

The desktop loaded OK so I figured everything was great.  I then tried to launch Firefox and nothing.......In the bottom panel "Starting Fire Fox Web Browser" appear for 5 secs and then goes away.   I did some preliminary investigaring with the help of firefox and everything pointed to shell and or profile permission issues.

So I created a new user and tried the same exercise with the same results.

Then I notice when I lauch and terminal window I get the following error to appear:

/usr/bin/lesspipe: 28: basename: not found
[: 253: lessfile: unexpected operator


I get some other strange errors while installing other apps...

Any help would be appreiated.

---

### Post by gettinoriginal on 2009-03-02
Um, been a long time since I changed sessions, but I think you want Xclient, not gnome as your default.

---

