---
title: "synaptic package manager Help"
date: 2006-07-27
forum: Desktop Environments
---

### Post by thunderfox933 on 2006-07-27
all my resportoires fail when they try to download. Is there a roblem

---

### Post by llamakc on 2006-07-27
Are you connected to the net? What error is given? Are you using a proxy?

Do you think there is a problem because Synaptic fails to connect to the repositories? If you think so, then yes there is a problem.

---

### Post by Ziox on 2006-07-27
do: sudo aptitude update

and paste the output/errors here...

---

### Post by thunderfox933 on 2006-07-27
i am on the net. I am not on a proxy. I get this

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg:) Connection failed [IP: 146.137.96.15 80]
[http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg:) Connection failed
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz:) Connection failed
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz:) Connection failed
[http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz:) Connection failed
[http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz:) Connection failed
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz:) Connection failed
[http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz:) Connection failed
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]
[http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:](http://us.archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz:) Connection failed [IP: 146.137.96.15 80]

---

### Post by Ziox on 2006-07-27
try this: gksu gedit /etc/apt/sources.list

and remove all the "us." things that's infront of the urls...

then do sudo aptitude update...and see what you get...

---

### Post by djheadley on 2006-07-27
First try Reload on the menu bar.

---

### Post by thunderfox933 on 2006-07-27
it dosnt work i get this

thunderfox@thunderfox-desktop:~$ gksu gedit /etc/apt/sources.list
(gedit:8236): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
thunderfox@thunderfox-desktop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 82.211.81.151 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 82.211.81.151 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Connection failed [IP: 82.211.81.151 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
  Connection failed [IP: 82.211.81.151 80]

---

### Post by Ziox on 2006-07-27
> **thunderfox933 said:**
> it dosnt work i get this

thunderfox@thunderfox-desktop:~$ gksu gedit /etc/apt/sources.list
(gedit:8236): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
thunderfox@thunderfox-desktop:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 82.211.81.151 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 82.211.81.151 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Connection failed [IP: 82.211.81.151 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
  Connection failed [IP: 82.211.81.151 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
  Connection failed [IP: 82.211.81.151 80]


paste your Xorg.conf file please...

---

### Post by thunderfox933 on 2006-07-27
here is the xorg

#!/bin/sh
# Debian xserver-xorg package configuration script
# Copyright 2000-2004 Branden Robinson.
# Copyright 2004-2005 Canonical Ltd.
# Authors: Branden Robinson, Fabio Massimo Di Nitto, Daniel Stone.
# Licensed under the GNU General Public License, version 2.  See the file
# /usr/share/common-licenses/GPL or <http://www.gnu.org/copyleft/gpl.txt>.

set -e

# source debconf library
. /usr/share/debconf/confmodule

THIS_PACKAGE=xserver-xorg
THIS_SCRIPT=config

SOURCE_VERSION=7.0.0-0ubuntu45

# Use special abnormal exit codes so that problems with this library are more
# easily tracked down.
SHELL_LIB_INTERNAL_ERROR=86
SHELL_LIB_THROWN_ERROR=74
SHELL_LIB_USAGE_ERROR=99

THIS_PACKAGE=${THIS_PACKAGE:-"(unknown package)"}
THIS_SCRIPT=${THIS_SCRIPT:-"(unknown script)"}

ARCHITECTURE="$(dpkg --print-installation-architecture)"

LAPTOP=""
if [ -n "$(which laptop-detect)" ]; then
    if laptop-detect >/dev/null; then
	LAPTOP=true
    fi
fi

if [ "$1" = "reconfigure" ] || [ -n "$DEBCONF_RECONFIGURE" ]; then
  RECONFIGURE="true"
else
  RECONFIGURE=
fi

if ([ "$1" = "install" ] || [ "$1" = "configure" ]) && [ -z "$2" ]; then
  FIRSTINST="yes"
fi

if [ -z "$RECONFIGURE" ] && [ -z "$FIRSTINST" ]; then
  UPGRADE="yes"
fi

trap "message;\
      message \"Received signal.  Aborting $THIS_PACKAGE package $THIS_SCRIPT script.\";\
      message;\
      exit 1" HUP INT QUIT TERM

reject_nondigits () {
  # syntax: reject_nondigits [ operand ... ]
  #
  # scan operands (typically shell variables whose values cannot be trusted) for
  # characters other than decimal digits and barf if any are found
  while [ -n "$1" ]; do
    # does the operand contain anything but digits?
    if ! expr "$1" : "[[:digit:]]\+$" > /dev/null 2>&1; then
      # can't use die(), because it wraps message() which wraps this function
      echo "$THIS_PACKAGE $THIS_SCRIPT error: reject_nondigits() encountered" \
           "possibly malicious garbage \"$1\"" >&2
      exit $SHELL_LIB_THROWN_ERROR
    fi
    shift
  done
}

# Query the terminal to establish a default number of columns to use for
# displaying messages to the user.  This is used only as a fallback in the
# event the COLUMNS variable is not set.  ($COLUMNS can react to SIGWINCH while
# the script is running, and this cannot, only being calculated once.)
DEFCOLUMNS=$(stty size 2> /dev/null | awk '{print $2}') || true
if ! expr "$DEFCOLUMNS" : "[[:digit:]]\+$" > /dev/null 2>&1; then
  DEFCOLUMNS=80
fi

message () {
  # pretty-print messages of arbitrary length
  reject_nondigits "$COLUMNS"
  echo "$*" | fmt -t -w ${COLUMNS:-$DEFCOLUMNS} >&2
}

observe () {
  # syntax: observe message ...
  #
  # issue observational message suitable for logging someday when support for
  # it exists in dpkg
  if [ -n "$DEBUG_XORG_PACKAGE" ]; then
    message "$THIS_PACKAGE $THIS_SCRIPT note: $*"
  fi
}

warn () {
  # syntax: warn message ...
  #
  # issue warning message suitable for logging someday when support for
  # it exists in dpkg; also send to standard error
  message "$THIS_PACKAGE $THIS_SCRIPT warning: $*"
}

die () {
  # syntax: die message ...
  #
  # exit script with error message
  message "$THIS_PACKAGE $THIS_SCRIPT error: $*"
  exit $SHELL_LIB_THROWN_ERROR
}

internal_error () {
  # exit script with error; essentially a "THIS SHOULD NEVER HAPPEN" message
  message "$THIS_PACKAGE $THIS_SCRIPT internal error: $*"
  exit $SHELL_LIB_INTERNAL_ERROR
}

usage_error () {
  message "$THIS_PACKAGE $THIS_SCRIPT usage error: $*"
  exit $SHELL_LIB_USAGE_ERROR
}

run () {
  # syntax: run command [ argument ... ]
  #
  # Run specified command with optional arguments and report its exit status.
  # Useful for commands whose exit status may be nonzero, but still acceptable,
  # or commands whose failure is not fatal to us.
  #
  # NOTE: Do *not* use this function with db_get or db_metaget commands; in
  # those cases the return value of the debconf command *must* be checked
  # before the string returned by debconf is used for anything.

  # validate arguments
  if [ $# -lt 1 ]; then
    usage_error "run() called with wrong number of arguments; expected at" \
                "least 1, got $#"
    exit $SHELL_LIB_USAGE_ERROR
  fi

  "$@" || _retval=$?

  if [ ${_retval:-0} -ne 0 ]; then
    observe "command \"$*\" exited with status $_retval"
  fi
}

if [ -e /etc/default/xorg ]; then
  . /etc/default/xorg
fi

# leave configuration alone in this case
if [ "x$XORG_CONFIG" = "xcustom" ]; then
  warn "not updating configuration as per \$XORG_CONFIG"
  exit 0
fi

CONFIG_DIR=/etc/X11
CONFIG_AUX_DIR=/var/lib/x11
SERVER_SYMLINK="$CONFIG_DIR/X"
XF86CONFIG="$CONFIG_DIR/XF86Config-4"
XORGCONFIG="$CONFIG_DIR/xorg.conf"
XF86CONFIG_CHECKSUM="$CONFIG_AUX_DIR/${XF86CONFIG##*/}.md5sum"
XORGCONFIG_CHECKSUM="$CONFIG_AUX_DIR/${XORGCONFIG##*/}.md5sum"
XF86CONFIG_ROSTER="$CONFIG_AUX_DIR/${XF86CONFIG##*/}.roster"
XORGCONFIG_ROSTER="$CONFIG_AUX_DIR/${XORGCONFIG##*/}.roster"
THIS_SERVER=/usr/bin/Xorg

NCARDS=0
NSERVERS=0
NDRIVERS=0
MULTIHEAD=

# get machine architecture
ARCH=$(dpkg --print-installation-architecture)

debug_echo () {
  # Syntax: debug_echo message ...
  if [ -n "$DEBUG_XORG_DEBCONF" ] || [ "$DEBCONF_DEBUG" = "user" ] \
    || [ "$DEBCONF_DEBUG" = '.*' ]; then
    DEBUG_XORG_PACKAGE=yes observe "$*"
  fi
}

debug_report_status () {
  # Syntax: debug_report_status command exit_status
  debug_echo "$1 exited with status $2"
}

discover_video () {
  if which discover >/dev/null 2>&1; then
    # must be Discover 1.x
    DISCOVERED_VIDEO=$(discover --disable-all --enable=pci \
                                --format="%V %M\t%S\t%D\n" video 2>/dev/null)
    # for sparc we attempt discovery on sbus but only after pci.
    if [ "$ARCH" = "sparc" ] && [ -z "$DISCOVERED_VIDEO" ]; then
      DISCOVERED_VIDEO=$(discover --disable-all --enable=sbus \
                                --format="%V %M\t%S\t%D\n" video 2>/dev/null)
    fi
    echo "$DISCOVERED_VIDEO"
  else
    warn "discover not found; video autodetection not available"
  fi
}

validate_string_db_input () {
  # Syntax: validate_string_db_input priority template
  #
  # validate string input; can't have doublequotes
  # If $MAY_BE_NULL is a non-null value (e.g., "yes"), the string may be null.
  if [ $# -ne 2 ]; then
    echo "internal error: validate_string_db_input() called with wrong number of arguments: $*" >&2
    exit 1
  fi
  PRIORITY=$1
  TEMPLATE=$2
  db_get "$TEMPLATE"
  SAFE="$RET"
  set +e
  while :; do
    db_input "$PRIORITY" "$TEMPLATE"
    # is the question going to be asked?
    if [ $? -eq 30 ]; then
      break # no; bail out of validation loop
    fi
    db_go
    db_get "$TEMPLATE"
    if [ -n "$RET" ]; then
      if ! expr "$RET" : '.*".*' > /dev/null 2>&1; then
        break # valid input
      else
        ERROR=xserver-xorg/config/doublequote_in_string_error
      fi
    else
      if [ -n "$MAY_BE_NULL" ]; then
        break # valid (null) input
      else
        ERROR=xserver-xorg/config/null_string_error
      fi
    fi
    # we only get to this point if the input was invalid; restore the known
    # good value in case we are interrupted before the user provides a valid
    # one
    db_set "$TEMPLATE" "$SAFE"
    db_fset "$TEMPLATE" seen false
    # now show the user the error message
    db_fset "$ERROR" seen false
    db_input critical "$ERROR"
    db_go
  done
  set -e
}

validate_numeric_db_input () {
  # Syntax: validate_numeric_db_input priority template
  #
  # validate numeric input; must have only digits, can be null
  if [ $# -ne 2 ]; then
    echo "internal error: validate_numeric_db_input() called with wrong number of arguments: $*" >&2
    exit 1
  fi
  PRIORITY=$1
  TEMPLATE=$2
  db_get "$TEMPLATE"
  SAFE="$RET"
  set +e
  while :; do
    db_input "$PRIORITY" "$TEMPLATE"
    # is the question going to be asked?
    if [ $? -eq 30 ]; then
      break # no; bail out of validation loop
    fi
    db_go
    db_get "$TEMPLATE"
    if [ -z "$RET" ] || expr "$RET" : "[0-9]\+$" > /dev/null 2>&1; then
      break # valid input
    fi
    # we only get to this point if the input was invalid; restore the known
    # good value in case we are interrupted before the user provides a valid
    # one
    db_set "$TEMPLATE" "$SAFE"
    db_fset "$TEMPLATE" seen false
    # now show the user the error message
    db_fset xserver-xorg/config/nonnumeric_string_error seen false
    db_input critical xserver-xorg/config/nonnumeric_string_error
    db_go
  done
  set -e
}

validate_bus_id_db_input () {
  # Syntax: validate_bus_id_db_input priority template
  #
  # validate BusID input
  if [ $# -ne 2 ]; then
    echo "internal error: validate_bus_id_db_input() called with wrong number of arguments: $*" >&2
    exit 1
  fi
  PRIORITY=$1
  TEMPLATE=$2
  db_get "$TEMPLATE"
  SAFE="$RET"
  set +e
  while :; do
    db_input "$PRIORITY" "$TEMPLATE"
    # is the question going to be asked?
    if [ $? -eq 30 ]; then
      break # no; bail out of validation loop
    fi
    db_go
    db_get "$TEMPLATE"
    case "$RET" in
      "")
        # An empty string is valid.
        break
        ;;
      ISA:*)
        # Looks like an ISA bus ID specification string.  At least up to a
        # point; upstream (xf86ParseIsaBusString() in
        # xc/programs/Xserver/hw/xfree86/common/xf86isaBus.c) doesn't actually
        # *supply* a specification.  So if the user's gotten this far, it's good
        # enough.
        break
        ;;
      PCI:*)
        # Looks like a PCI bus ID specification; validate it.  (We can use &&
        # outside a conditional here because of the "set +e" above.)
        expr "$RET" : "PCI:[0-9]\{1,3\}:[0-9]\{1,3\}:[0-9]\{1,3\}$" >/dev/null \
          2>&1 && break
        ;;
      SBUS:*)
        # Looks like an SBUS bus ID specification; validate it.  (We can use &&
        # outside a conditional here because of the "set +e" above.)
        #
        # According to upstream (xf86ParseSbusBusString() in
        # xc/programs/Xserver/hw/xfree86/common/xf86sbusBus.c):
        #
        # The format is assumed to be one of:
        # * "fbN", e.g. "fb1", which means the device corresponding to /dev/fbN
        # * "nameN", e.g. "cgsix0", which means Nth instance of card NAME
        # * "/prompath", e.g. "/sbus@0,10001000/cgsix@3,0" which is
        #   PROM pathname to the device.
        #
        # Well, okay.
        #
        # Accept any non-null sequence of lowercase letters followed by a
        # non-null sequence of decimal digits.  This handles "fbN" and "nameN".
        expr "$RET" : "SBUS:[a-z]\+[0-9]\+" >/dev/null 2>&1 && break
        # Now for the PROM path.  I am lazy; accept a slash followed a non-null
        # sequence of letters and commas, an at sign, a non-null sequence of
        # hexadecimal digits, a comma, and another non-null sequence of
        # hexadecimal digits.  Furthermore, accept multiple occurences of this
        # entire sequence.  Whew.
        expr "$RET" : "SBUS:\(/[A-Za-z,]\+@[0-9A-Fa-f]\+,[0-9A-Fa-f]\+\)\+$" \
          >/dev/null 2>&1 && break
        ;;
      [0-9])
        # Accept a simple decimal integer for legacy buses that haven't been
        # properly implemented (e.g., for SGI Indigo2 XL).
        break
        ;;
      *)
    esac
    # we only get to this point if the input was invalid; restore the known good
    # value in case we are interrupted before the user provides a valid one
    db_set "$TEMPLATE" "$SAFE"
    db_fset "$TEMPLATE" seen false
    # now show the user the error message
    db_fset xserver-xorg/config/device/bus_id_error seen false
    db_input critical xserver-xorg/config/device/bus_id_error
    db_go
  done
  set -e
}

auto_answer () {
  # Syntax: auto_answer input_command priority template default_answer
  #
  # Used to auto-answer questions that don't have reasonable defaults.  Some
  # people insist on running the xserver-xorg config script with the
  # non-interactive frontend.  For this to work, the debconf database will need
  # to be pre-loaded with answers to several questions.  You have been
  # warned...
  if [ $# -ne 4 ]; then
    echo "internal error: auto_answer() called with wrong number of arguments: $*" >&2
    exit 1
  fi
  INPUT_COMMAND=$1
  PRIORITY=$2
  TEMPLATE=$3
  DEFAULT_ANSWER=$4
  set +e
  debug_echo "auto_answer() \"$INPUT_COMMAND $PRIORITY $TEMPLATE\" with default \"$DEFAULT_ANSWER\""
  db_fget "$TEMPLATE" seen
  # are we re-configuring?
  if [ -z "$FIRSTINST" ] && [ "$RET" = "true" ]; then
    # yes, we are reconfiguring
    db_get "$TEMPLATE"
    debug_echo "auto_answer: (reconfiguring) preserving existing answer \"$RET\""
  else
    # not reconfiguring; has the question been seen before?
    if [ "$RET" = "true" ]; then
      db_get "$TEMPLATE"
      debug_echo "auto_answer: (not reconfiguring) preserving existing answer \"$RET\""
    else
      debug_echo "auto_answer: auto-answering with \"$DEFAULT_ANSWER\""
      db_set $TEMPLATE "$DEFAULT_ANSWER"
    fi
  fi
  "$INPUT_COMMAND" "$PRIORITY" "$TEMPLATE"
  if [ $? -eq 30 ]; then
    debug_echo "auto_answer: $TEMPLATE is not being asked"
  else
    debug_echo "auto_answer: asking $TEMPLATE"
  fi
  set -e
  db_go
  db_get "$TEMPLATE"
  debug_echo "auto_answer: $TEMPLATE is \"$RET\""
}

priority_ceil() {
  # syntax: priority_ceil requested_priority
  #
  # Given a variable PRIORITY_CEILING and a "requested_priority" argument, echo
  # a debconf priority string corresponding to the lesser of the two.

  # Implementation note: a clever version of this could be done using "eval",
  # or embedding a Perl script, but those would be more difficult to maintain.
  # Better just to go the simple and stupid route.  Yes, I know this is not
  # very efficient.

  # Validate arguments.
  if [ $# -ne 1 ]; then
    debug_echo "priority_ceil() called with empty or bogus arguments \"$*\";" \
               "assuming argument of \"low\""
    _requested_priority=low
  else
    _requested_priority="$1"
  fi

  # If PRIORITY_CEILING is null or unset, it's same as not having one at all;
  # the sky's the limit.  We use a locally scoped priority_ceiling variable
  # because we don't want to affect the value of the global one.
  _priority_ceiling=${PRIORITY_CEILING:-"critical"}

  # Ensure the value of _priority_ceiling is reasonable.
  if [ "$_priority_ceiling" != "critical" ] && \
       [ "$_priority_ceiling" != "high" ] && \
       [ "$_priority_ceiling" != "medium" ] && \
       [ "$_priority_ceiling" != "low" ]; then
    debug_echo "priority_ceil() called with bogus value of \$PRIORITY_CEILING" \
               "\"$_priority_ceiling\"; treating as \"critical\""
    _priority_ceiling=critical
  fi

  case "$_requested_priority" in
    critical)
      # This is the highest priority, so there is nowhere to go but down.
      echo "$_priority_ceiling"
      ;;
    high)
      case "$_priority_ceiling" in
        critical)
          echo "$_requested_priority"
          ;;
        high|medium|low)
          echo "$_priority_ceiling"
          ;;
      esac
      ;;
    medium)
      case "$_priority_ceiling" in
        critical|high)
          echo "$_requested_priority"
          ;;
        medium|low)
          echo "$_priority_ceiling"
          ;;
      esac
      ;;
    low)
      # This is the lowest priority, so we can't go any lower.
      echo "$_requested_priority"
      ;;
    *)
      debug_echo "priority_ceil() called with bogus argument" \
                 "\"$_requested_priority\"; returning \"low\""
      echo low
      ;;
  esac
}

non_latin_keyboard () {
  NONLATINMAPS="am ar bg by cs el gr il ir iu lo mk ml mm mn ru th tj ua"
  for i in $NONLATINMAPS; do
    if [ "$XMAP" = "$i" ]; then
      NON_LATIN="true"
    fi
  done

  # Turkish F keyboards are non-Latin; Turkish Q aren't.
  if [ "$XMAP" = "tr" ] && [ "$VARIANT" = "f" ]; then
    NON_LATIN="true"
  fi
}

# analyze arguments; used by auto_answer()
if [ "$1" = "reconfigure" ] || [ -n "$DEBCONF_RECONFIGURE" ]; then
  RECONFIGURE=true
else
  RECONFIGURE=
fi

if [ -z "$2" ]; then
  FIRSTINST=yes
fi

# migrate from "expert" to "advanced"
db_get xserver-xorg/config/monitor/selection-method
if [ "$RET" = "Expert" ]; then
  db_set xserver-xorg/config/monitor/selection-method "Advanced"
fi

# The only supported protocol (per Zephaniah Hull) for the GPM repeater is
# IntelliMouse; migrate anyone using that mouse device to that protocol.  Other
# values used to work as well, but no longer do since the XFree86 mouse driver
# was rewritten for XFree86 4.3.0.  See Debian bug #233933 for more details.
db_get xserver-xorg/config/inputdevice/mouse/port
if [ "$RET" = "/dev/gpmdata" ]; then
  db_get xserver-xorg/config/inputdevice/mouse/protocol
  if [ "$RET" != "IntelliMouse" ]; then
    observe "migrating template" \
            "\"xserver-xorg/config/inputdevice/mouse/protocol\" from" \
            "\"$RET\" to \"IntelliMouse\""
    db_set xserver-xorg/config/inputdevice/mouse/protocol "IntelliMouse"
  fi
fi

debug_echo "Configuring $THIS_PACKAGE."

# default X server

# if the X server symlink file already exists and points to an executable X
# server, it's not as important to ask questions related to it (these questions
# "have a reasonable default")
PRIORITY_CEILING=
if [ -e "$SERVER_SYMLINK" ]; then
  if [ -x "$(readlink "$SERVER_SYMLINK")" ]; then
    debug_echo "X server symlink exists and points to executable X server;" \
               "capping X server question priority at medium."
    PRIORITY_CEILING=medium
  fi
fi

# priority of shared/default-x-server
PRIORITY=high

db_metaget shared/default-x-server owners
OWNERS="$RET"
db_metaget shared/default-x-server choices
CHOICES="$RET"

if [ "$OWNERS" != "$CHOICES" ]; then
  debug_echo "\$OWNERS does not equal \$CHOICES: \"$OWNERS\" != \"$CHOICES\""
  db_subst shared/default-x-server choices $OWNERS
  db_fset shared/default-x-server seen false
fi

if ! expr "$OWNERS" : ".*,.*" > /dev/null 2>&1; then
  debug_echo "\$OWNERS has only one value; shared/default-x-server will not be asked"
fi

# collect information about installed video card(s), if possible
if which discover > /dev/null 2>&1; then
  DISCOVERED_VIDEO=$(discover_video)
  MULTIHEAD=$(echo "$DISCOVERED_VIDEO" | wc -l)
  DISCOVERED_VIDEO=$(echo "$DISCOVERED_VIDEO" | head -n 1)
  if [ -n "$DISCOVERED_VIDEO" ]; then
    NCARDS=$(echo "$DISCOVERED_VIDEO" | wc -l)
    SERVERS=$(echo "$DISCOVERED_VIDEO" | awk 'BEGIN { FS="\t" } {print $2}' | grep -v unknown | sort | uniq)
    if [ -n "$SERVERS" ]; then
      NSERVERS=$(echo "$SERVERS" | wc -l)
    fi
    DRIVERS=$(echo "$DISCOVERED_VIDEO" | awk 'BEGIN { FS="\t" } {print $NF}' | grep -v unknown | sort | uniq)
    if [ -n "$DRIVERS" ]; then
      NDRIVERS=$(echo "$DRIVERS" | wc -l)
    fi
    if [ $MULTIHEAD -gt 1 ]; then
      MULTIHEAD=yes
    fi
  fi
fi

---

### Post by thunderfox933 on 2006-07-27
# set a failsafe default answer for shared/default-x-server
DEFAULT=$THIS_PACKAGE

if which discover > /dev/null 2>&1; then
  if [ -n "$FIRSTINST" ] || [ -n "$RECONFIGURE" ]; then
    PRIORITY="medium"
    if [ -n "$RECONFIGURE" ]; then
      PRIORITY="high"
    fi
    auto_answer db_input "$(priority_ceil $PRIORITY)" xserver-xorg/autodetect_video_card "true"
    db_get xserver-xorg/autodetect_video_card
    AUTODETECT_VIDEO_CARD="$RET"
    if [ "$AUTODETECT_VIDEO_CARD" = "true" ]; then
      # We're going to autodetect, so clear out the old values
      for param in use_fbdev driver video_ram identifier bus_id; do
          db_reset xserver-xorg/config/device/$param
      done

      if [ $NSERVERS -eq 0 ]; then
        debug_echo "could not autodetect X server: no video card detected," \
                   "or no server known for it"
        db_input "$(priority_ceil medium)" shared/no_known_x-server || debug_report_status "db_input $(priority_ceil medium) shared/no_known_x-server" "$?"
        db_go
      elif [ $NSERVERS -eq 1 ]; then
        debug_echo "autodetected X server: $SERVERS"
        if [ "$SERVERS" = "${THIS_SERVER##*/}" ] || [ "$SERVERS" = "XFree86" ]; then
          # the autodetected X server is the only one on the system, and the one
          # we're currently configuring; it's unlikely the user will want to use
          # something else
          PRIORITY=low
        else
          debug_echo "X server autodetected, but does not correspond to this package"
          # we do not set shared/default-x-server here, because the
          # autodetected X server might not be getting installed
        fi
      elif [ $NSERVERS -gt 1 ]; then
        debug_echo "could not autodetect X server: multiple servers for video cards"
        VIDEOCARD_SERVER_REPORT=$(echo "$DISCOVERED_VIDEO" | awk 'BEGIN { FS="\t"; printf " %-40s%20s\n .\n", "Detected Video Card", "Suggested X server" } { printf " %-50s%10s\n", $1, $2 } END { printf " .\n" }')
        # can't do this until there is a way to embed newlines into debconf command streams :(
        #db_subst shared/multiple_possible_x-servers detected_cards "$VIDEOCARD_SERVER_REPORT"
        debug_echo "$VIDEOCARD_SERVER_REPORT"
        db_input "$(priority_ceil high)" shared/multiple_possible_x-servers || debug_report_status "db_input $(priority_ceil high) shared/multiple_possible_x-servers" "$?"
        db_go
      fi
    else
      debug_echo "user declined video card autodetection"
    fi
  else
    debug_echo "upgrading package; not running autodetection script"
  fi
else
  debug_echo "could not autodetect X server: discover not found"
fi

# now the default-x-server question may be asked
db_fget shared/default-x-server seen
debug_echo "seen flag of shared/default-x-server is $RET"
debug_echo "db_input $(priority_ceil $PRIORITY) shared/default-x-server"
auto_answer db_input $(priority_ceil $PRIORITY) shared/default-x-server "$DEFAULT"

# is this the selected X server?
db_get shared/default-x-server
if [ "$RET" != "$THIS_PACKAGE" ]; then
  # nothing else to do in this script
  debug_echo "Skipping further configuration of $THIS_PACKAGE, because it is not the default X server package."
  exit 0
fi

# priority of xserver-xorg/config/device/driver
PRIORITY=medium
if [ -n "$RECONFIGURE" ]; then
  PRIORITY=high
fi

DRIVER_DIRS="/usr/X11R6/lib/modules/drivers /usr/lib/xorg/modules/drivers"
for i in $DRIVER_DIRS; do
  if [ -d $i ]; then
    REAL_DRIVER_DIRS="$REAL_DRIVER_DIRS $i "
  fi
done

if [ -n "$REAL_DRIVER_DIRS" ]; then
  # Build list of available video drivers, omitting the atimisc, r128, and
  # radeon sub-modules (the ati driver knows when and how to load these).
  # v4l is not a display driver, and dummy is for advanced users.
  DRIVER_LIST="$(find $REAL_DRIVER_DIRS -name '*_drv.*' \
                 | sed 's|^.*/\([^/]*\)_drv\.[^\._]*|\1|g' \
                 | egrep -v '(atimisc|dummy|r128|radeon|v4l)' | sort -u | xargs \
                 | sed 's/ /, /g' 2>/dev/null) "
fi

# Set a hard-coded module list (if necessary) and default driver module on an
# architecture-specific basis.

case "$ARCH" in
  alpha)
    DEFAULT_DRIVER=vga
    ;;
  amd64|hurd-i386|i386)
    DEFAULT_DRIVER=vesa
    ;;
  *)
    DEFAULT_DRIVER=fbdev
    ;;
esac

if [ -z "$DRIVER_LIST" ]; then
  observe "no video driver modules found in $DRIVER_DIRS; defaulting to $DEFAULT_DRIVER"
  DRIVER_LIST="$DEFAULT_DRIVER"
fi

observe "available video driver list set to \"$DRIVER_LIST\""

if [ -n "$FIRSTINST" ] || [ -n "$RECONFIGURE" ]; then
  if which discover >/dev/null 2>&1; then
    if [ "$AUTODETECT_VIDEO_CARD" = "true" ]; then
      if [ $NDRIVERS -eq 0 ]; then
        observe "could not autodetect X server driver: no video card" \
                "detected, or no driver known for it"
      elif [ $NDRIVERS -eq 1 ]; then
        observe "autodetected X server driver: $DRIVERS"
        PRIORITY=low
        DEFAULT_DRIVER="$DRIVERS"
      elif [ $NDRIVERS -gt 1 ]; then
        observe "could not autodetect X server driver: multiple drivers for" \
                "video cards"
        VIDEOCARD_DRIVER_REPORT=$(echo "$DISCOVERED_VIDEO" \
          | awk 'BEGIN { FS="\t"; printf " %-30s%30s\n .\n", "Detected Video Card", "Suggested driver module" } { printf " %-50s%10s\n", $1, $3 } END { printf " .\n" }')
        # can't do this until there is a way to embed newlines into debconf
        # command streams :(
        # db_subst shared/multiple_possible_x-drivers detected_cards \
        #   "$VIDEOCARD_DRIVER_REPORT"
        observe "$VIDEOCARD_DRIVER_REPORT"
        PRIORITY=high
        db_input "$(priority_ceil high)" xserver-xorg/multiple_possible_x-drivers || debug_report_status "db_input $(priority_ceil high) xserver-xorg/multiple_possible_x-drivers" "$?"
        db_go
      fi
    else
      observe "user declined video card autodetection (driver)"
    fi
  else
    observe "could not autodetect X server driver: discover not found"
  fi


  ## per arch driver specific overrides:
  #
  # make sure to ask the driver on sparc till we have a reliable way
  # to gather these info properly.
  #
  # make it possible to use vesa as default for x86*

  case "$ARCH" in
    sparc)
      PRIORITY=high
      ;;
    i386|amd64)
      if [ -n "$XFORCEVESA" ] || [ -n "$(grep xforcevesa /proc/cmdline)" ]; then
        DEFAULT_DRIVER=vesa
      fi
      ;;
  esac

  db_subst xserver-xorg/config/device/driver choices "$DRIVER_LIST"
  auto_answer db_input "$PRIORITY" \
    xserver-xorg/config/device/driver "$DEFAULT_DRIVER"

  # card identifier; try to set a sensible default
  DEFAULT=
  if [ -n "$(echo $NDRIVERS)" ] && [ $NDRIVERS -eq 1 ] && [ $NCARDS -eq 1 ]; then
    if which discover > /dev/null 2>&1; then
      if [ "$AUTODETECT_VIDEO_CARD" = "true" ]; then
        DEFAULT=$(echo "$DISCOVERED_VIDEO" | awk 'BEGIN { FS="\t" } {print $1}')
      fi
    fi
  fi
  if [ -z "$DEFAULT" ]; then
    # fall back to some language-specific generic text
    case "${LC_ALL:-${LC_MESSAGES:-$LANG}}" in
      ca_*) DEFAULT="Targeta de vídeo genèrica" ;;
      da_*) DEFAULT="Standard Video Kort" ;;
      de_*) DEFAULT="Standardgrafikkarte" ;;
      es_*) DEFAULT="Tarjeta de vídeo genérica" ;;
      fr_*) DEFAULT="Carte vidéo générique" ;;
      gl_*) DEFAULT="Tarxeta de Video Xenérica" ;;
      it_*) DEFAULT="Scheda video generica" ;;
      # ja
      # nl
      pt_BR) DEFAULT="Placa de Vídeo Genérica" ;;
      # ru
      # sv
      *) DEFAULT="Generic Video Card" ;;
    esac
  fi
  # this question requires input validation
  MAY_BE_NULL= auto_answer validate_string_db_input "$(priority_ceil low)" xserver-xorg/config/device/identifier "$DEFAULT"

  DEVICE_IDENTIFIER="$DEFAULT"

  # BusID
  PRIORITY=low
  DEFAULT=

  # Some PowerPCs need to be told where to find the video card even if there is
  # only one in the machine (broken PCI bus code in the XFree86 X server, most
  # likely).  If there are multiple video cards, we need to configure one as the
  # primary head.
  # Warty: always feed this info.
  MULTIHEAD=yes
  if [ "$ARCH" = "powerpc" ] || [ "$MULTIHEAD" = "yes" ]; then
    if [ "$ARCH" = "powerpc" ]; then
      PRIORITY=medium
    fi
    if [ "$MULTIHEAD" = "yes" ]; then
      PRIORITY=medium
    fi
    if which lspci > /dev/null 2>&1; then
      # Try to guess the correct BusID.
      VIDEO_CARD=$(LC_ALL=C lspci -n | grep -E "(Class )?0300:" | sort -n | head -n 1 \
        | cut -d\  -f1)
      if [ -n "$VIDEO_CARD" ]; then
        # Recent versions of lspci report a four-digit domain as the first field.
        if expr "$VIDEO_CARD" : ".*:.*:.*\..*" >/dev/null 2>&1; then
          # We have an entry in "hex:hex:hex.hex" format; we need
          # "PCI:decimal:decimal:decimal" (we don't use the domain).
          DOMAIN=$(printf "%d" 0x$(echo $VIDEO_CARD | cut -d: -f1) )
          BUS=$(printf "%d" 0x$(echo $VIDEO_CARD | cut -d: -f2) )
          DEVICE=$(printf "%d" 0x$(echo $VIDEO_CARD | cut -d: -f3 | cut -d. -f1) )
          FUNCTION=$(printf "%d" 0x$(echo $VIDEO_CARD | cut -d. -f2) )
          DEFAULT="PCI:$BUS:$DEVICE:$FUNCTION"
        elif expr "$VIDEO_CARD" : ".*:.*\..*" >/dev/null 2>&1; then
          # We have an entry in "hex:hex.hex" format; we need
          # "PCI:decimal:decimal:decimal".
          BUS=$(printf "%d" 0x$(echo $VIDEO_CARD | cut -d: -f1) )
          DEVICE=$(printf "%d" 0x$(echo $VIDEO_CARD | cut -d: -f2 | cut -d. -f1) )
          FUNCTION=$(printf "%d" 0x$(echo $VIDEO_CARD | cut -d. -f2) )
          DEFAULT="PCI:$BUS:$DEVICE:$FUNCTION"
        else
          warn "unrecognized output from lspci: \"$VIDEO_CARD\""
        fi
      fi
    fi
  fi

  # SGI Indigo2 XLs require a special hack, per Guido Guenther (see Debian
  # #249614).
  if [ -e /proc/cpuinfo ]; then
    if grep -q "system type.*:.*SGI Indigo2" /proc/cpuinfo; then
      PRIORITY=medium
      DEFAULT=1
    fi
  fi

  # this question requires input validation
  if [ -n "$DEFAULT" ]; then
    auto_answer validate_bus_id_db_input "$(priority_ceil $PRIORITY)" xserver-xorg/config/device/bus_id "$DEFAULT"
  else
    validate_bus_id_db_input "$(priority_ceil $PRIORITY)" xserver-xorg/config/device/bus_id || debug_report_status "validate_bus_id_db_input $(priority_ceil $PRIORITY) xserver-xorg/config/device/bus_id" "$?"
  fi

  # video RAM
  db_get xserver-xorg/config/device/driver
  DEFAULT=
  # this question requires input validation
  if [ -n "$DEFAULT" ]; then
    auto_answer validate_numeric_db_input "$(priority_ceil low)" xserver-xorg/config/device/video_ram "$DEFAULT"
  else
    validate_numeric_db_input "$(priority_ceil low)" xserver-xorg/config/device/video_ram || debug_report_status "validate_numeric_db_input $(priority_ceil low) xserver-xorg/config/device/video_ram" "$?"
  fi

  # use fbcon kernel functions?

  case "$ARCH" in
    alpha|hurd-i386|i386|amd64)
      USE_FBDEV=false
      ;;
    *)
      USE_FBDEV=true
      ;;
  esac

  if [ -e /proc/fb ]; then
    FB_TYPE="$(grep '^0 ' /proc/fb | sed 's/[^[:space:]] //')"
    # did we actually get back anything?
    if [ -n "$FB_TYPE" ]; then
      if echo "$FB_TYPE" | grep -Eiq '(OFfb|VESA|VGA16)'; then
        USE_FBDEV=false
      else
        # other framebuffers do support UseFBDEV
        USE_FBDEV=true
      fi
    fi
  else
    USE_FBDEV=false
  fi

  # it looks like Mac Mini need an extra kick. Make sure to give it to it.

  if [ "$ARCH" = powerpc ] && [ "$USE_FBDEV" = "false" ]; then
    # it looks like Mac Mini need an extra kick. Make sure to give it to it.
    if [ -e /proc/cpuinfo ]; then
      if [ -n "$(cat /proc/cpuinfo | grep "^machine.*PowerMac10,1")" ] && \
         [ -n "$(cat /proc/cpuinfo | grep "^platform.*PowerMac")" ]; then
        USE_FBDEV=true
      fi
    fi
    # Make sure to force UseFBDev with Rage 128 or stuff will go bad in some old
    # Macs.
    if echo "$DEVICE_IDENTIFIER" | grep -q "Rage 128"; then
      USE_FBDEV=true
    fi
  fi

  if [ -n "$XORG_USE_FBDEV" ] && [ "$XORG_USE_FBDEV" = "no" ]; then
    USE_FBDEV=false
  fi

  db_get xserver-xorg/config/device/use_fbdev || debug_report_status "db_get xserver-xorg/config/device/use_fbdev"
  if [ "$RET" = "true" ] && [ "$USE_FBDEV" = "false" ]; then
    debug_echo "xserver-xorg/config/device/use_fbdev is \"true\" but /proc/fb does not exist, is empty, or reports a framebuffer type with which UseFBDev cannot be used; setting template to \"false\""
    db_set xserver-xorg/config/device/use_fbdev false
  fi

  auto_answer db_input "$(priority_ceil medium)" xserver-xorg/config/device/use_fbdev "$USE_FBDEV"
fi

# keyboard setup
PRIORITY="medium"

if [ -n "$FIRSTINST" ]; then
  AUTODETECT_KB="true"
else
  AUTODETECT_KB="false"
fi

auto_answer db_input "$(priority_ceil $PRIORITY)" xserver-xorg/autodetect_keyboard "$AUTODETECT_KB" || debug_echo "db_input xserver-xorg/autodetect_keyboard"
db_get xserver-xorg/autodetect_keyboard || debug_report_status "db_get server-xorg/autodetect_keyboard"
if [ "$RET" = "true" ]; then
  DOKBDETECT="true"
  debug_echo "Redetecting keyboard layout; resetting flag to false."
  db_set xserver-xorg/autodetect_keyboard false
fi

if [ -n "$DOKBDETECT" ]; then
  # generated by a small bit of Perl from a static list of keymaps provided
  # by Matthias Urlichs
  db_get debian-installer/language || debug_report_status "db_get debian-installer/language"
  DI_LANG=${RET%%:*}
  DI_LANG=${DI_LANG%%@*}
  DI_LANG=${DI_LANG%%.*}

  db_get debian-installer/keymap || debug_report_status "db_get debian-installer/keymap"
  DI_KEYMAP="${RET##mac-usb-}"
  DI_KEYMAP="${DI_KEYMAP%%-latin1}"

  case "$DI_KEYMAP" in
    be2) XMAP="be";;
    bg) XMAP="bg"; VARIANT="bds";;
    br) XMAP="us"; VARIANT="intl"; MODEL="pc104";;
    br-abnt2) XMAP="br"; VARIANT="abnt2"; MODEL="abnt2";;
    by) XMAP="by";;
    cf) XMAP="ca"; VARIANT="fr";;
    croat) XMAP="hr";;
    cz-lat2) XMAP="cz";;
    de-latin1-nodeadkeys) XMAP="de"; VARIANT="nodeadkeys";;
    de) XMAP="de";;
    dvorak) XMAP="us"; VARIANT="dvorak"; MODEL="pc104";;
    dk) XMAP="dk";;
    es) XMAP="es";;
    et) XMAP="ee";;
    fr_CH) XMAP="ch"; VARIANT="fr";;
    fr_CH-latin1) XMAP="ch"; VARIANT="fr";;
    fr) XMAP="fr";;
    fi|fi-latin1) XMAP="fi";;
    fr-latin9) XMAP="fr"; VARIANT="latin9";;
    gb) XMAP="gb";;
    gr) XMAP="gr";;
    hebrew) XMAP="il";;
    hu) XMAP="hu";;
    is) XMAP="is";;
    it) XMAP="it";;
    jp106) XMAP="jp"; VARIANT="jp106";;
    la) XMAP="latam";;
    lt) XMAP="lt";; 
    # XXX should these be MODEL="macintosh"?
    mac-us-std) XMAP="us";;
    mac-de2-ext) XMAP="de"; VARIANT="nodeadkeys";;
    mac-fr2-ext) XMAP="fr";;
    mac-fr3) XMAP="fr";;
    mac-es) XMAP="es";;
    mk) XMAP="mk";;
    nl) XMAP="nl";;
    no) XMAP="no";;
    pl) XMAP="pl";;
    pt) XMAP="pt";;
    lv-latin4) XMAP="lv";;
    ro) XMAP="ro";;
    ru) XMAP="ru";;
    se) XMAP="se";;
    sg) XMAP="ch"; VARIANT="de";;
    sg-latin1) XMAP="ch"; VARIANT="de";;
    sk-qwerty) XMAP="sk"; VARIANT="qwerty";;
    slovene) XMAP="si";;
    sr-cy) XMAP="cs";;
    trf|trfu) XMAP="tr"; VARIANT="f";;
    trq|trqu) XMAP="tr";;
    ua) XMAP="ua";;
    uk) XMAP="gb";;
    us) XMAP="us"; MODEL="pc104";;
    *) XMAP="UNKNOWN";;
  esac

  if [ "$XMAP" = "us" ] && [ "${DI_LANG}" = "ko_KR" ]; then
          XMAP=kr # Uses US keyboard on the console.
          MODEL=
  fi

  if [ "$XMAP" = "UNKNOWN" ]; then
    warn "failed to infer keyboard layout from layout/lang '$DI_KEYMAP'"
    PRIORITY=medium
    XMAP="us"
    MODEL="pc104"
  # prompt for layout if we ended up with French Canadian; apparently having
  # US-layout keyboards is common there
  elif [ "$XMAP" = "ca" ] && [ "$VARIANT" = "fr" ]; then
    PRIORITY=high
  else
    PRIORITY=low
  fi

  # we can't do non-Latin usernames, so people with Latin layouts need a US
  # layout so they can log in, and then switch to writing native text.  Bit hard
  # to work out which one should be the default.
  non_latin_keyboard
  if [ -n "$NON_LATIN" ]; then
    warn "selected layout '$XMAP' from '$DI_KEYMAP--$REALLANG' is non-Latin; " \
         "adding us to the layout list, Alt+Shift toggles"
    if [ -z "$OPTIONS" ]; then
      OPTIONS="grp:alt_shift_toggle"
    else
      OPTIONS="$OPTIONS,grp:alt_shift_toggle"
    fi
    XMAP="us,$XMAP"
  fi
  
  if [ -n "$LEVEL2" ]; then
    warn "selected layout '$XMAP' from '$DI_KEYMAP--$REALLANG' is l2-only"
  fi

  XKBLAYOUT="$XMAP"
  XKBOPTIONS="$OPTIONS"
  XKBVARIANT="$VARIANT"
  XKBMODEL="$MODEL"
else
  db_get xserver-xorg/config/inputdevice/keyboard/layout || debug_report_status "db_get xserver-xorg/config/inputdevice/keyboard/layout"
  XKBLAYOUT="$RET"
  db_get xserver-xorg/config/inputdevice/keyboard/options || debug_report_status "db_get xserver-xorg/config/inputdevice/keyboard/options"
  XKBOPTIONS="$RET"
  db_get xserver-xorg/config/inputdevice/keyboard/variant || debug_report_status "db_get xserver-xorg/config/inputdevice/keyboard/variant"
  XKBVARIANT="$RET"
  db_get xserver-xorg/config/inputdevice/keyboard/model || debug_report_status "db_get xserver-xorg/config/inputdevice/keyboard/model"
  XKBMODEL="$RET"
  PRIORITY=low
fi

MAY_BE_NULL= auto_answer validate_string_db_input "$(priority_ceil $PRIORITY)" xserver-xorg/config/inputdevice/keyboard/layout "$XKBLAYOUT"

# these questions require input validation
PRIORITY=medium

DEFAULT=xorg

MAY_BE_NULL= auto_answer validate_string_db_input "$(priority_ceil $PRIORITY)" xserver-xorg/config/inputdevice/keyboard/rules "$DEFAULT"

if [ -z "$XKBMODEL" ]; then
  db_get xserver-xorg/config/inputdevice/keyboard/rules
  if [ "$RET" = "sun" ]; then
    db_set xserver-xorg/config/inputdevice/keyboard/rules "xorg"
    XKBMODEL=pc105
  elif [ "$RET" = "xorg" ]; then
    if [ "$ARCH" = "powerpc" ] && \
        [ -e /proc/sys/dev/mac_hid/keyboard_sends_linux_keycodes ] && \
        [ "$(cat /proc/sys/dev/mac_hid/keyboard_sends_linux_keycodes)" = "0" ]; then
      XKBMODEL=macintosh_old
    else
      XKBMODEL=pc105
    fi
  fi
fi
MAY_BE_NULL= auto_answer validate_string_db_input "$(priority_ceil $PRIORITY)" xserver-xorg/config/inputdevice/keyboard/model "$XKBMODEL"

# ugly kludge, I know; map Apple->AltGr for most European Macs
db_get xserver-xorg/config/inputdevice/keyboard/model
if [ "$ARCH" = "powerpc" ] && [ "$RET" = "pc105" ]; then
  if [ -n "$XKBOPTIONS" ]; then
    if ! echo "$XKBOPTIONS" | grep -q "lv3:"; then
      XKBOPTIONS="$XKBOPTIONS,lv3:lwin_switch"
    fi
  else
    XKBOPTIONS="lv3:lwin_switch"
  fi
fi

# kill me now.
if echo "$XKBOPTIONS" | grep -q "nodeadkeys"; then
  if [ -z "$XKBVARIANT" ]; then
    XKBVARIANT="nodeadkeys"
    NEWOPTIONS=""
    IFS_SAVE="$IFS"
    IFS=","
    for i in $XKBOPTIONS; do
      IFS="$IFS_SAVE"
      if [ "$i" != "nodeadkeys" ]; then
        NEWOPTIONS="${NEWOPTIONS:+$NEWOPTIONS,}$i"
      fi
      IFS=","
    done
    IFS="$IFS_SAVE"
    XKBOPTIONS="$NEWOPTIONS"
    db_set xserver-xorg/config/inputdevice/keyboard/variant "$XKBVARIANT"
    db_set xserver-xorg/config/inputdevice/keyboard/options "$XKBOPTIONS"
  else
    warn "wanted to migrate nodeadkeys from options -> variant, but variant" \
         "is already $XKBVARIANT; not migrating"
  fi
fi

MAY_BE_NULL=yes auto_answer validate_string_db_input "$(priority_ceil low)" xserver-xorg/config/inputdevice/keyboard/variant "$XKBVARIANT"

MAY_BE_NULL=yes auto_answer validate_string_db_input "$(priority_ceil $PRIORITY)" xserver-xorg/config/inputdevice/keyboard/options "$XKBOPTIONS"

AUTODETECTED_PORT="/dev/input/mice"
AUTODETECTED_PROTOCOL="ImPS/2"

db_subst xserver-xorg/config/inputdevice/mouse/port choices $AUTODETECTED_PORT
auto_answer db_input "$(priority_ceil low)" xserver-xorg/config/inputdevice/mouse/port "${AUTODETECTED_PORT}"

db_get xserver-xorg/config/inputdevice/mouse/port
case "$RET" in
  *psaux)
    MOUSE_PROTOCOL_CHOICES="PS/2, ImPS/2, GlidePointPS/2, NetMousePS/2, NetScrollPS/2, ThinkingMousePS/2, MouseManPlusPS/2, ExplorerPS/2"
    DEFAULT_PROTOCOL="PS/2"
    ;;
  *ttyS*|*tts/*)
    MOUSE_PROTOCOL_CHOICES="Auto, Microsoft, MouseSystems, GlidePoint, ThinkingMouse, ValuMouseScroll, MouseMan, Logitech, IntelliMouse, MMSeries, MMHitTab"
    DEFAULT_PROTOCOL="Auto"
    ;;
  *input/mice)
    MOUSE_PROTOCOL_CHOICES="ImPS/2, ExplorerPS/2"
    DEFAULT_PROTOCOL="ImPS/2"
    ;;
  *atibm|*atixl|*sunmouse)
    MOUSE_PROTOCOL_CHOICES="BusMouse"
    DEFAULT_PROTOCOL="BusMouse"
    ;;
  *gpmdata)
    MOUSE_PROTOCOL_CHOICES="IntelliMouse"
    DEFAULT_PROTOCOL="IntelliMouse"
    ;;
esac
db_subst xserver-xorg/config/inputdevice/mouse/protocol choices $MOUSE_PROTOCOL_CHOICES
if ! expr "$MOUSE_PROTOCOL_CHOICES" : ".*,.*" > /dev/null 2>&1; then
  debug_echo "\$MOUSE_PROTOCOL_CHOICES has only one value; setting xserver-xorg/config/inputdevice/mouse/protocol to \"$DEFAULT_PROTOCOL\""
  db_set xserver-xorg/config/inputdevice/mouse/protocol "$DEFAULT_PROTOCOL"
else
  auto_answer db_input "$(priority_ceil $PRIORITY)" xserver-xorg/config/inputdevice/mouse/protocol "${AUTODETECTED_PROTOCOL:-$DEFAULT_PROTOCOL}"
fi

auto_answer db_input "$(priority_ceil low)" xserver-xorg/config/inputdevice/mouse/emulate3buttons true || debug_report_status "db_input $(priority_ceil low) xserver-xorg/config/inputdevice/mouse/emulate3buttons" "$?"
db_go

# server modules to load
db_fget xserver-xorg/config/modules seen
# if it's seen but empty, then give it a default value.  fixes stuff for people
# upgrading through breezy, and no modules is enough of a pathological case that
# people doing that would've modified their config in other ways anyway.
if [ "$RET" = "true" ]; then
  db_get xserver-xorg/config/modules
  if [ -z "$RET" ]; then
    db_reset xserver-xorg/config/modules
  fi
fi

# kill me now.
if echo "$MODULES" | grep -q "GLcore"; then
  NEWOPTIONS=""
  IFS_SAVE="$IFS"
  IFS=","
  for i in $MODULES; do
    IFS="$IFS_SAVE"
    if [ "$i" != "GLcore" ]; then
      NEWMODULES="${NEWMODULES:+$NEWMODULES,}${i%% }"
    fi
    IFS=","
  done
  IFS="$IFS_SAVE"
  MODULES="$NEWMODULES"
  db_set xserver-xorg/config/modules "$MODULES"
fi

auto_answer db_input "$(priority_ceil low)" xserver-xorg/config/modules "i2c, bitmap, ddc, dri, extmod, freetype, glx, int10, type1, vbe" || true
db_go

# files and dri sections
auto_answer db_input "$(priority_ceil low)" xserver-xorg/config/write_files_section true || debug_report_status "db_input $(priority_ceil low) xserver-xorg/config/write_files_section" "$?"
db_go

exit 0

# vim:set ai et sts=2 sw=2 tw=80:

---

### Post by Ziox on 2006-07-27
wow! i'm so sorry...i meant sources.list...sorry sorry sorry...had been editing my xorg.conf file for like 6 hours straight...got tired i guess...

---

### Post by thunderfox933 on 2006-07-27
here is the sorces

# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by Ziox on 2006-07-27
> **thunderfox933 said:**
> here is the sorces

# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Uncomment all the lines that start with "deb" and the sudo aptitude update

---

### Post by thunderfox933 on 2006-07-27
i did a reinstall and it dosent work should i repost the file again

---

### Post by thunderfox933 on 2006-07-28
it looks like this now

eb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by thunderfox933 on 2006-07-28
what do you mean by uncomment

---

### Post by Ziox on 2006-07-28
> **thunderfox933 said:**
> what do you mean by uncomment

copy this to the file, its mine...with a few extra that's fairly useful...:

```
## Automatix sources.list
## This is automatically generated by Automatix


####################################
### Official Ubuntu Repositories ###
####################################

# Dapper Final Release Repository
deb http://archive.ubuntu.com/ubuntu dapper main
deb-src http://archive.ubuntu.com/ubuntu dapper main

deb http://archive.ubuntu.com/ubuntu dapper restricted
deb-src http://archive.ubuntu.com/ubuntu dapper restricted

deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

# Dapper Security Updates
deb http://archive.ubuntu.com/ubuntu dapper-security main
deb-src http://archive.ubuntu.com/ubuntu dapper-security main

deb http://archive.ubuntu.com/ubuntu dapper-security restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-security restricted

deb http://archive.ubuntu.com/ubuntu dapper-security universe
deb-src http://archive.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper-security multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-security multiverse

# Dapper Bugfix Updates
deb http://archive.ubuntu.com/ubuntu dapper-updates main
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main

deb http://archive.ubuntu.com/ubuntu dapper-updates restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates restricted

deb http://archive.ubuntu.com/ubuntu dapper-updates universe
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe

deb http://archive.ubuntu.com/ubuntu dapper-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Project)
# deb http://archive.ubuntu.com/ubuntu dapper-backports main
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports main

# deb http://archive.ubuntu.com/ubuntu dapper-backports restricted
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports restricted

deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# deb http://archive.ubuntu.com/ubuntu dapper-backports universe
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports universe

# deb http://archive.ubuntu.com/ubuntu dapper-backports multiverse
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports multiverse

deb http://archive.canonical.com/ubuntu dapper-commercial main


##############################
### Automatix Repositories ###
##############################

deb http://www.getautomatix.com/apt dapper main

## created by automatixrepo3

##########
##Others##
##########

deb http://squentin.free.fr/gmusicbrowser ./
deb http://people.ubuntu.com/~seb128/deb ./
```

---

### Post by thunderfox933 on 2006-07-28
still dosent work

---

### Post by Ziox on 2006-07-28
weird...

can you connect to the internet with the computer?

---

### Post by thunderfox933 on 2006-07-30
yes

---

### Post by Ziox on 2006-07-31
sorry...what's the output with the new sources.list file?

sudo aptitude update

---

### Post by thunderfox933 on 2006-08-11
sorry for taking a week to reply my computers harddrive crashed and still have to get a new.

---

### Post by SammyB on 2006-08-28
Nothing works. Followed the instructions in this thread with same result. apt-get doesn't work. GUI doesn't work. Downloading the DEB with firefox and manually installing with dpkg -i does work. The odd thing is both apt-get and GUI can connect to tell me what my disk requirements are before getting the dreaded "connection failed" messages. Hopefully this thread will restart...

---

