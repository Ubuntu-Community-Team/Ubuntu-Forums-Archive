---
title: "error logging in after changes to etc/profile"
date: 2009-06-16
forum: General Help
---

### Post by NIHrebel on 2009-06-16
I made some changes to my etc/profile so now when I go to login to Ubuntu I get the error message as follows:

Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

* view details (~/.xsession-errors file)

/etc/gdm/Xsession: Beginning session setup...
[:47: 0 : unexpected operator
/etc/profile : 61 : [[: not found
/etc/profile.d/X.sh: 3 : Bad substitution

here is what my etc/profile looks like

```
# Begin /etc/profile
# Written for Beyond Linux From Scratch
# by James Robertson <jameswrobertson@earthlink.net>
# modifications by Dagmar d'Surreal <rivyqntzne@pbzpnfg.arg>

# System wide environment variables and startup programs.

# System wide aliases and functions should go in /etc/bashrc.  Personal
# environment variables and startup programs should go into
# ~/.bash_profile.  Personal aliases and functions should go into
# ~/.bashrc.

# Functions to help us manage paths.  Second argument is the name of the
# path variable to be modified (default: PATH)
pathremove () {
        local IFS=':'
        local NEWPATH
        local DIR
        local PATHVARIABLE=${2:-PATH}
        for DIR in ${!PATHVARIABLE} ; do
                if [ "$DIR" != "$1" ] ; then
                  NEWPATH=${NEWPATH:+$NEWPATH:}$DIR
                fi
        done
        export $PATHVARIABLE="$NEWPATH"
}

pathprepend () {
        pathremove $1 $2
        local PATHVARIABLE=${2:-PATH}
        export $PATHVARIABLE="$1${!PATHVARIABLE:+:${!PATHVARIABLE}}"
}

pathappend () {
        pathremove $1 $2
        local PATHVARIABLE=${2:-PATH}
        export $PATHVARIABLE="${!PATHVARIABLE:+${!PATHVARIABLE}:}$1"
}


# Set the initial path
export PATH=/bin:/usr/bin

if [ $EUID -eq 0 ] ; then
        pathappend /sbin:/usr/sbin
        unset HISTFILE
fi

# Setup some environment variables.
export HISTSIZE=1000
export HISTIGNORE="&:[bf]g:exit"

# Setup a red prompt for root and a green one for users.
NORMAL="\[\e[0m\]"
RED="\[\e[1;31m\]"
GREEN="\[\e[1;32m\]"
if [[ $EUID == 0 ]] ; then
  PS1="$RED\u [ $NORMAL\w$RED ]# $NORMAL"
else
  PS1="$GREEN\u [ $NORMAL\w$GREEN ]\$ $NORMAL"
fi

for script in /etc/profile.d/*.sh ; do
        if [ -r $script ] ; then
                . $script
        fi
done

# Now to clean up
unset pathremove pathprepend pathappend

# End /etc/profile
```Please help. Thanks!

---

### Post by Brandon Williams on 2009-06-16
/etc/profile is used by any posix shell, which means that it should only contain posix syntax. '[[' is not posix, not is '==', so neither should be used in /etc/profile.

If you want to check your changes to make sure they'll work, execute it with /bin/sh, as in: '/bin/sh /etc/profile'

Did you also add /etc/profile.d/X.sh? There appears to be a problem in that script, too.

---

### Post by NIHrebel on 2009-06-16
When I go to change etc/profile it won't allow me to save it. How exactly do I edit and save etc/profile so I can remove the [[ and ==  ? Also, when I go to run sudo -i , I get the error ```
-bash: /etc/profile.d/i18n.sh: line 2: syntax error near unexpected token `<'
-bash: /etc/profile.d/i18n.sh: line 2: `export LANG=<ll>_<CC>.<charmap><@modifiers>'
```

Any more ideas? Thanks again.

---

### Post by Brandon Williams on 2009-06-16
Where did the /etc/profile.d/i18n.sh script come from? I can find with a search on packages.ubuntu.com.

Regardless, you should be able to edit /etc/profile with sudo, e.g. 'sudo nano /etc/profile' You'll also need to look at /etc/profile.d/X.sh and /etc/profile.d/i18n.sh, since neither of them looks like it works in a posix shell either.

---

### Post by NIHrebel on 2009-06-17
I have resolved this issue. I decided I didn't want to take the time editing etc/profile so since I had a fresh install of Ubuntu and I wouldn't be losing much data, I reinstalled Intrepid and upgraded to Jaunty. Thanks for you help though. I appreciate it.

---

