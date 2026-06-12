---
title: "CompizConfig doesn't restore HotCorners setting"
date: 2012-06-21
forum: Desktop Environments
---

### Post by busfahrer on 2012-06-21
Hi, I'm on 12.04.

I've used CompizConfig to set it so when I touch the 
                      bottom right corner, compiz exposes all windows in a preview, so I can 
                      pick one of them. This works, but when I logout and login again, it 
                      doesn't work anymore. The setting is still there, but I have to delete 
                      it and re-create it for it to work again.

Anybody got an idea how to 
                      fix this?

---

### Post by busfahrer on 2012-06-22
In case anybody else is having the same problem, here's the workaround I've ended up using:

(Using my home directory as /home/busfahrer, use your own of course)

Create the file /home/busfahrer/.restartcompiz.sh (the leading dot will make sure it's hidden)

in that file, enter these two lines
```

#!/bin/sh
/usr/bin/compiz --replace ccp &

```

Then open a terminal and enter
```

chmod a+x /home/busfahrer/.restartcompiz.sh

```
in order to make the file executable.

Now click the gear in the top right corner of the screen. Select Startup Applications. Add a new entry. Enter any name. As the command, enter
```

/home/busfahrer/.restartcompiz.sh

```

If you now log out and log back in again, the screen will shortly flicker because compiz will be re-started after it's started, but from now on, your hot corner settings should work as you set them using CompizConfig.

Greetings,
busfahrer

---

