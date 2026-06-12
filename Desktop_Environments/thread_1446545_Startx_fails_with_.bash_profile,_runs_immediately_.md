---
title: "Startx fails with .bash_profile, runs immediately after"
date: 2010-04-04
forum: Desktop Environments
---

### Post by MeBrains on 2010-04-04
I installed minimal karmic koala with openbox lxde on an old notebook.

when i boot up, I automatically get logged in through /etc/init/tty1.conf

```
# tty1 - getty
#
# This service maintains a getty on tty1 from the point the system is
# started until it is shut down again.

start on stopped rc RUNLEVEL=[2345]
stop on runlevel [!2345]

respawn

exec /bin/login -f USER < /dev/tty1 > /dev/tty1 2>&1

```

it starts .bash_profile:
```

#startx

echo "is this parsed?"

case "`tty`" in
/dev/tty1) echo "case start" && wait && startx;;
esac

```

and runs up to startx.

there I get the error that it can not open display 0 and that I should remove .X0-lock from /tmp

strange thing is: there is no .X0-lock. when I ty startx immediately after getting the prompt and immediately after receiving the lock error, it does work.

when i exit the command prompt and log in again. .bash_profile is correctly parsed and x starts automatically...

what can be wrong? why does it fail the first time around?

---

### Post by Brandon Williams on 2010-04-06
I expect that this is due to startup script ordering problems. The upstart mount-tmp job is deleting the lock file, which is probably why you don't see it when you look. You want to be sure that the lock file is gone before you attempt to start X, but there is nothing in your tty1.conf file to guarantee that your tty1 job runs after the mounted-tmp job is complete.

I don't know enough about upstart to be able to suggest a fix for your tty1.conf file, but you could add something like this in your .bash_profile just before running startx:
```
while [ -e /tmp/.X0-lock ]; do
    sleep 1
done
```
or even just:
```
rm -f /tmp/.X0-lock
```

---

### Post by MeBrains on 2010-05-21
brandon, rm seems to have worked... thx.

---

