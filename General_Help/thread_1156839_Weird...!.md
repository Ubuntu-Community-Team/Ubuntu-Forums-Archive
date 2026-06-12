---
title: "Weird...?!"
date: 2009-05-12
forum: General Help
---

### Post by jwkungfu on 2009-05-12
Hi all,

I have upgraded to Jaunty via a disc.
After that was complete I jumped online and checked for for any updates,
After doing a lengthy update/partial upgrade, when I boot up now, my desktop has a whole pile of folders on it? Documents, Firefox, Examples, Music, Pictures, Public etc etc...

Is this new to Jaunty or is something wrong?

JW.

---

### Post by MysticalRiotCandy on 2009-05-12
In Gconf-editor, there's a setting to make the home directory act like the Desktop folder.  You might want to disable that one.  
/apps/nautilus/preferences/desktop_is_home_dir

---

### Post by kpkeerthi on 2009-05-12
[This]("http://ubuntuforums.org/showthread.php?t=47434") could be the issue.

---

### Post by jwkungfu on 2009-05-12
Many thanks for the reply.
Maybe if I can access the Configuration editor, I might be able to change it with that?
One of the posts mentions Applications/System Tools/Configuration Editor....
It's not in my Applications/System Tools/... ?

Tried in a terminal $ configuration editor

Bash

Damn it

---

### Post by jwkungfu on 2009-05-12
hang on!
think i've worked that one out...?

$ gconf-editor


now to try and work out what it does?!?!?!?

---

