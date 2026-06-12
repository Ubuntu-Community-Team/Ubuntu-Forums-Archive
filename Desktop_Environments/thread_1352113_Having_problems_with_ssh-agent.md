---
title: "Having problems with ssh-agent"
date: 2009-12-11
forum: Desktop Environments
---

### Post by Eniac on 2009-12-11
Hi,

I've been trying to set my pc and server with RSA pair of keys in order to use ssh (actually sshfs) to mount a folder on from my server on my pc.

that part works, but i want to have that folder mounted automatically at every boot. so i researched a little and it comes down to me having to setup passwordless ssh, so that when i use sshfs in fstab, it can be mounted without using a password.

a bunch of posts found on google helped me narrow it :
[http://www.brandonhutchinson.com/Passwordless_ssh_logins.html](http://www.brandonhutchinson.com/Passwordless_ssh_logins.html)
[http://ubuntuforums.org/showthread.php?t=306240](http://ubuntuforums.org/showthread.php?t=306240)

but when i follow what's on the ubuntuforums thread, it doesnt work, perhaps because its not for the same version of ubuntu.

Here's my version of my 90x11-common-ssh_agent file. at the very bottom are the lines i added according to what i found on the other thread, but its not working and its messing my session up when i enable it.

I'm sure im missing some really stupid detail but i just cant find it. does someone have experience with that ?

thanks for any hints you can give me.

ps: 9.10 upgrade having messed up my pc, i reverted to 9.04, clean install if it changes anything.

```

  GNU nano 2.0.9          File: 90x11-common_ssh-agent                          

# $Id: 90x11-common_ssh-agent 305 2005-07-03 18:51:43Z dnusinow $

# This file is sourced by Xsession(5), not executed.

STARTSSH=
SSHAGENT=/usr/bin/ssh-agent
SSHAGENTARGS=

if grep -qs ^use-ssh-agent "$OPTIONFILE"; then
  if [ -x "$SSHAGENT" ] && [ -z "$SSH_AUTH_SOCK" ] \
     && [ -z "$SSH2_AUTH_SOCK" ]; then
    STARTSSH=yes
    if [ -f /usr/bin/ssh-add1 ] && cmp -s $SSHAGENT /usr/bin/ssh-agent2; then
      # use ssh-agent2's ssh-agent1 compatibility mode
      SSHAGENTARGS=-1
    fi
  fi
fi

if [ -n "$STARTSSH" ]; then
  STARTUP="$SSHAGENT $SSHAGENTARGS ${TMPDIR:+env TMPDIR=$TMPDIR} $STARTUP"
fi

# vim:set ai et sts=2 sw=2 tw=80:

#eval "$SSHAGENT"
#ssh-add /home/stephane/.ssh/sshfskey.pub



```

---

