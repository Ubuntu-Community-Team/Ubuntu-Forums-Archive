---
title: "How to detect when a user has closed a graphical session?"
date: 2013-05-10
forum: Desktop Environments
---

### Post by zedixal on 2013-05-10
Hi,

I use Xubuntu. I've setup a small script that starts when I log in and continuously checks things:

```

#!/bin/bash

# Main loop
while [ 1 ]
do
  # ... do stuff
  sleep 5
done

exit 0

```

Unfortunately, when I log off and log in as another user, the script is still running... Every time I have to kill it manually.
I'd like to instruct this script to stop when the user that started it logs off. I tried to use the command *who*, but it seems to detect only the users that have opened a terminal.

Thank you in advance

---

### Post by zedixal on 2013-05-10
I probably found a solution (for xfce environments only)

In short, I modified the script to save the current user in a variable before starting the while loop; then it checks the current owner of the **xfdesktop** process in every loop. If the two do not match anymore, the script breaks the loop and exits:

```

#!/bin/bash

ORIGINAL_USER="$( id -u -n )"

# Main loop
while [ 1 ]
do
  # ... do stuff

  # Check current user; if it changed, exit
  CURRENT_USER="$( ps aux | grep [x]fdesktop | awk '{print $1}' )"
  if [ ! "$CURRENT_USER" == "$ORIGINAL_USER" ]; then
    break
  fi

  sleep 5
done

exit 0


```

I guess that a more general (i.e. valid for all graphical environments) solution exists, but in my box it works ;)

---

