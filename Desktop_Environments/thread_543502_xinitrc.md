---
title: "xinitrc"
date: 2007-09-05
forum: Desktop Environments
---

### Post by ensis2k on 2007-09-05
Hello,

i do not understand why the lines i have entered into my .xinitrc wont be executed properly.

```

#!/usr/bin/env bash
exec gnome-terminal &
exec xmodmap -e "pointer = 1 2 3 6 7 4 5" &
exec imwheel -k -b "8 9" &
exec gnome-session

```

---

### Post by BobCFC on 2007-12-22
> **ensis2k said:**
> Hello,

i do not understand why the lines i have entered into my .xinitrc wont be executed properly.

```

#!/usr/bin/env bash
exec gnome-terminal &
exec xmodmap -e "pointer = 1 2 3 6 7 4 5" &
exec imwheel -k -b "8 9" &
exec gnome-session

```



I think you only use exec for the last command.  I believe the X desktop closes when the exec command is finished so you only want it for the last one?

---

