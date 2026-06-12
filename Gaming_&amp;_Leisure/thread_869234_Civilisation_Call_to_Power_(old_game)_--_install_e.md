---
title: "Civilisation: Call to Power (old game) -- install error"
date: 2008-07-24
forum: Gaming &amp; Leisure
---

### Post by Skara Brae on 2008-07-24
L.S. (*no, not the UNIX command* :) ),

I have this (very, this being from 1999) old linux game: "Civilisation: Call to Power".

Just for the 'fun' of it, I tried to install it on Ubuntu 7.10 (the 64-bit version). However I get an error message, which I will quote here.

The GUI error says:

---------------------------------------------------------
[I]#!/bin/sh
#
# Installer for Civilization: Call To Power (Linux version)

# Try a GUI install first
cd `dirname $0`
if wish -f setup/checkwish.tk 2>/dev/null; then
  wish=wish
else
  #echo "Your version of wish (Tcl/Tk) is not compatible"
  wish=${HOME}/.ctpwish
  cp setup/Tcl-Tk/bin/wish8.0 $wish
  chmod 755 $wish
  trap "rm -f $wish" 0 1 2 15
fi
$wish -f setup/setup.tk && exit 0

# Oh well, drop back to a cheesy script. :)
echo ""
echo "GUI install failed, see the README for manual setup instructions."
exit 1[/I]
---------------------------------------------------------


When I try a command-line install, I get this:

---------------------------------------------------------
[I]"Unsupported Platform

setup/printlibc: 3: function: not found
setup/printarch: 3: function: not found
This installation of CivCTP doesn't support glibc-2.0 on unknown
Please contact Loki Technical Support,[/I] etc, etc, etc...
---------------------------------------------------------

Many, many years ago, when I first tried linux (SuSE 6 or 7, I don't remember exactly...), I remember it ran fine. With 7.10, unfortunately, I get either one of these two errors.

I am (after all these years) still not much more than a newbie who (only) knows the most basic commands (like, in a terminal window), so what this error is about - something about Tcl/Tk, a scripting language or something? - is not all too clear for me.

Is there *any* way to get this game to run on "Gutsy Gibbon"?

Oh, I hope this is the right place to post this?

---

### Post by kidux on 2008-08-21
I know this thread is older, but it looks like the installer is looking for an older version of glibc. This makes sense as it is from '99. Unfortunately, LokiGames isn't around anymore so updates aren't possible AFAIK.

---

### Post by CoercibleGerm on 2008-12-09
> **kidux said:**
> I know this thread is older, but it looks like the installer is looking for an older version of glibc. This makes sense as it is from '99. Unfortunately, LokiGames isn't around anymore so updates aren't possible AFAIK.

Sorry to necro a previously necro'd thread, but I didn't feel it would be appropriate to start a new one.

Anyways...

Might there be a way to fool the installer into thinking the older version is present, or maybe to have the older version and the newer version exist simultaneously? I ask only because I am also having this problem... had zero luck running my windows copy of civ2 via wine... freeciv feels awkward to me... so I figured I'd shell out some bucks and buy a linux-native civ, only to find it doesn't work for me and I'm now out $27. If anyone has any ideas on getting this to run, I'm willing to try...

---

