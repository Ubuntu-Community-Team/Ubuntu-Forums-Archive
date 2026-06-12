---
title: "Running commands at startup"
date: 2010-01-02
forum: Desktop Environments
---

### Post by graabein on 2010-01-02
Hi, I have xmonad as my default session on Ubuntu 9.04 GDM. I was wondering how I can run some commands upon login? I don't have a .xinitrc file. Should I make one? Would it crash with loading xmonad as window manager?

I mainly want to run numlock and nautilus (to mount external drives).

---

### Post by iponeverything on 2010-01-02
> **graabein said:**
> Hi, I have xmonad as my default session on Ubuntu 9.04 GDM. I was wondering how I can run some commands upon login? I don't have a .xinitrc file. Should I make one? Would it crash with loading xmonad as window manager?

I mainly want to run numlock and nautilus (to mount external drives).

X looks for the .xinitrc in your home directory, if it does not find it, it uses /etc/X11/xinit/xinitrc

---

### Post by graabein on 2010-01-02
Thanks. I see it invokes global X session script in /etc/X11/Xsession:

```
#!/bin/sh
#
# /etc/X11/Xsession
#
# global Xsession file -- used by display managers and xinit (startx)

# $Id: Xsession 967 2005-12-27 07:20:55Z dnusinow $

set -e

PROGNAME=Xsession

message () {
  # pretty-print messages of arbitrary length; use xmessage if it
  # is available and $DISPLAY is set
  MESSAGE="$PROGNAME: $*"
  echo "$MESSAGE" | fold -s -w ${COLUMNS:-80} >&2
  if [ -n "$DISPLAY" ] && which xmessage > /dev/null 2>&1; then
    echo "$MESSAGE" | fold -s -w ${COLUMNS:-80} | xmessage -center -file -
  fi
}

message_nonl () {
  # pretty-print messages of arbitrary length (no trailing newline); use
  # xmessage if it is available and $DISPLAY is set
  MESSAGE="$PROGNAME: $*"
  echo -n "$MESSAGE" | fold -s -w ${COLUMNS:-80} >&2;
  if [ -n "$DISPLAY" ] && which xmessage > /dev/null 2>&1; then
    echo -n "$MESSAGE" | fold -s -w ${COLUMNS:-80} | xmessage -center -file -
  fi
}

errormsg () {
  # exit script with error
  message "$*"
  exit 1
}

internal_errormsg () {
  # exit script with error; essentially a "THIS SHOULD NEVER HAPPEN" message
  # One big call to message() for the sake of xmessage; if we had two then
  # the user would have dismissed the error we want reported before seeing the
  # request to report it.
  errormsg "$*" \
           "Please report the installed version of the \"x11-common\"" \
           "package and the complete text of this error message to" \
           "<debian-x@lists.debian.org>."
}

# initialize variables for use by all session scripts

OPTIONFILE=/etc/X11/Xsession.options

SYSRESOURCES=/etc/X11/Xresources
USRRESOURCES=$HOME/.Xresources

SYSSESSIONDIR=/etc/X11/Xsession.d
USERXSESSION=$HOME/.xsession
USERXSESSIONRC=$HOME/.xsessionrc
ALTUSERXSESSION=$HOME/.Xsession
ERRFILE=$HOME/.xsession-errors

# attempt to create an error file; abort if we cannot
if (umask 077 && touch "$ERRFILE") 2> /dev/null && [ -w "$ERRFILE" ] &&
  [ ! -L "$ERRFILE" ]; then
  chmod 600 "$ERRFILE"
elif ERRFILE=$(tempfile 2> /dev/null); then
  if ! ln -sf "$ERRFILE" "${TMPDIR:=/tmp}/xsession-$USER"; then
    message "warning: unable to symlink \"$TMPDIR/xsession-$USER\" to" \
             "\"$ERRFILE\"; look for session log/errors in" \
             "\"$TMPDIR/xsession-$USER\"."
  fi
else
  errormsg "unable to create X session log/error file; aborting."
fi

# truncate ERRFILE if it is too big to avoid disk usage DoS
if [ "`stat -c%s \"$ERRFILE\"`" -gt 500000 ]; then
  T=`mktemp -p "$HOME"`
  tail -c 500000 "$ERRFILE" > "$T" && mv -f "$T" "$ERRFILE" || rm -f "$T"
fi

exec >>"$ERRFILE" 2>&1

echo "$PROGNAME: X session started for $LOGNAME at $(date)"

# sanity check; is our session script directory present?
if [ ! -d "$SYSSESSIONDIR" ]; then
  errormsg "no \"$SYSSESSIONDIR\" directory found; aborting."
fi

# Attempt to create a file of non-zero length in /tmp; a full filesystem can
# cause mysterious X session failures.  We do not use touch, :, or test -w
# because they won't actually create a file with contents.  We also let standard
# error from tempfile and echo go to the error file to aid the user in
# determining what went wrong.
WRITE_TEST=$(tempfile)
if ! echo "*" >>"$WRITE_TEST"; then
  message "warning: unable to write to ${WRITE_TEST%/*}; X session may exit" \
          "with an error"
fi
rm -f "$WRITE_TEST"

# use run-parts to source every file in the session directory; we source
# instead of executing so that the variables and functions defined above
# are available to the scripts, and so that they can pass variables to each
# other
SESSIONFILES=$(run-parts --list $SYSSESSIONDIR)
if [ -n "$SESSIONFILES" ]; then
  set +e
  for SESSIONFILE in $SESSIONFILES; do
    . $SESSIONFILE
  done
  set -e
fi

exit 0

# vim:set ai et sts=2 sw=2 tw=80:
```

Should I create USERXSESSION=$HOME/.xsession or USERXSESSIONRC=$HOME/.xsessionrc and insert commands there?

---

### Post by iponeverything on 2010-01-02
I am not sure. I would try the to create the rc one first. You can did around on google for examples.

---

### Post by graabein on 2010-01-06
Using **.xsessionrc** works just fine. Here's what I have now:

```
#!/bin/sh
numlockx on
gnome-settings-deamon &
gnome-volume-manager & 
```


**Update:** Wait a tick, gnome-volume-manager does not exist on Ubuntu 9.04. What should I use? 

Would dbus-launch do the trick?

---

