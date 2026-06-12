---
title: "[SOLVED] Problems setting global umask (for gnome users) in Hardy Heron"
date: 2008-11-11
forum: Desktop Environments
---

### Post by larseko on 2008-11-11
Hi,

I've been trying to set umask 0002 for users on our network, so that they may share files on a NFS network. At first I specified this in /etc/profile, by adding:

if [ $UID > 0 ] && [ $UID == "`id -g`" ]; then 
        umask 002
else 
        umask 022
fi


This to ensure only real non-root users should get this umask. I was 99% sure I tested this on several machines, but apparently that was not so, because every file they make now, even in a terminal, still gets umask 022. So /etc/profile was wrong, and google told me /etc/X11/Xsession.d/55gnome_session-gnomerc was the place to look. However, that doesn't seem to be read when users log in via GDM/GNOME either.

So, where should I put these statements or other statements to change umask? I can't see what I'm doing wrong here. I thought every file in Xsession.d was read?

Btw:

someuser@myhost:/etc/X11/Xsession.d$ cat 55gnome-session_gnomerc 
# If we are running the GNOME session, source ~/.gnomerc

BASESTARTUP=`basename "$STARTUP" | cut -d\  -f1`
if [ "$BASESTARTUP" = gnome-session -o \
	\( "$BASESTARTUP" = x-session-manager -a \
	"`readlink /etc/alternatives/x-session-manager`" = \
		/usr/bin/gnome-session \) ]; then
  GNOMERC=$HOME/.gnomerc
  if [ -r "$GNOMERC" ]; then
    . "$GNOMERC"
  fi
fi

if [ $UID > 0 ] && [ $UID == "`id -g`" ]; then 
        umask 002
else 
        umask 022
fi

---

### Post by larseko on 2008-11-11
Hm, come to think of it, could the problem be that $UID or id -g won't yield the right output on the stage where /etc/profile or the session file is loaded?

---

