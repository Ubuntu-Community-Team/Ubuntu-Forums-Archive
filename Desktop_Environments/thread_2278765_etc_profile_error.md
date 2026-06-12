---
title: "etc profile error"
date: 2015-05-18
forum: Desktop Environments
---

### Post by pwrmx24 on 2015-05-18
can someone help me trouble shoot this profile? I'm new to ubuntu and i tried to insall java and I think i messed up this file.  I'll be back in a second to update this post with the error.

/etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "$PS1" ]; then
  if [ "$BASH" ] && [ "$BASH" != "/bin/sh" ]; then
    # The file bash.bashrc already sets the default PS1.
    # PS1='\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
      . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

# The default umask is now handled by pam_umask.
# See pam_umask(8) and /etc/login.defs.

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi
JAVA_HOME=/usr/local/java/jre1.8.0_45
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
export JAVA_HOME
export PATH

---

### Post by papibe on 2015-05-18
**Thread closed**. Duplicated thread here: [http://ubuntuforums.org/showthread.php?t=2278766](http://ubuntuforums.org/showthread.php?t=2278766)

Please do not post duplicates. Besides diluting the community effort, it is very difficult to provide any consistent help.

Please continue the conversation on the other thread. You can 'bump' (a reply to refresh the thread) every 24hrs if you want.

Regards.

---

