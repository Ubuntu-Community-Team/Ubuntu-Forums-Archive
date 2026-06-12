---
title: "NX server and Firefox - &quot;already runnung&quot;?"
date: 2010-04-11
forum: Desktop Environments
---

### Post by itzfritz on 2010-04-11
When I use NX to log into my ubuntu box upstairs, and start Firefox, I get a "firefox is already running" error if I am already running firefox in that box via local session (under the same username).  
Shouldnt NX be starting a new session?  How come every other app works fine?

Has anybody come across this problem, and if so how did you handle it?



Thanks!

EDIT: I don't want to start using a different firefox profile, if I didnt need my bookmarks etc I would just log in as some other user.  thx ;)
EDIT2: I believe this is related; [http://ubuntuforums.org/showthread.php?t=1337435](http://ubuntuforums.org/showthread.php?t=1337435) (Firefox can't run new window in second X Screen...? - no resolution)

---

### Post by lovinglinux on 2010-04-11
Since you are running Firefox on the remote machine using the remote user profiles, then is not possible to start another Firefox process using a profile already in use.

You should consider creating a Firefox profile for remote connections and synchronize your bookmarks using [Xmarks](https://addons.mozilla.org/en-US/firefox/search/?q=Xmarks) or [Mozilla Weave](https://addons.mozilla.org/en-US/firefox/addon/10868). You can start Firefox with -no-remote option then.

---

