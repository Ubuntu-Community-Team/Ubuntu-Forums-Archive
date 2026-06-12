---
title: "kpersonalizer appears by every login repeatly"
date: 2006-09-22
forum: Desktop Environments
---

### Post by JvdS45 on 2006-09-22
Hi by every new login kpersonalizer which i don't want to use, but it came by a seperate installation when i need soem other files,. Now when i start the pc alwats kpersonalizer comes up and ask a new desktop configuration. I am want these thing off.

where is a a config localised and which command can i use to put this tool of permantly :|

thanks

:-)

---

### Post by someguyouknow on 2006-09-22
edit /usr/bin/startkde
change this kpersonalizerrc General FirstLogin true
to this kpersonalizerrc General FirstLogin false

---

