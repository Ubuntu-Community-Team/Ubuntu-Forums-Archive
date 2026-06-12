---
title: "Thunderbird"
date: 2005-08-08
forum: Desktop Environments
---

### Post by awilisch on 2005-08-08
I've been having a curious issue lately. I reset the Preferred Applications settings in GNOME to use Thunderbird for email rather than Evolution. Now however whenever I click on a email link in Firefox it tries to open a new Thunderbird instead of just opening an email window. The problem is when I have thunderbird running already it opens up a profile window asking me which profile I want to use, when it should just open an email window.

Has anyone else experienced this problem?

Aric

---

### Post by RicgorE on 2005-08-08
Yes Thunderbird behaves this way for me too. I wish I knew of a solution. It can be annoying

---

### Post by RikoW on 2005-08-09
Hi,

some time ago I found a scripting solution for this:

create a shell script mailto.sh:

[I]#!/bin/sh
url="$1"
export MOZILLA_FIVE_HOME=/usr/bin
if [ $(pidof mozilla-thunderbird-bin | wc -w) -gt 0 ]; then

# Thunderbird is running
    url=`echo "$url" | sed -e's/^mailto://'`
    $MOZILLA_FIVE_HOME/mozilla-thunderbird -remote "mailto($url)"
else
# Thunderbird is not running
    $MOZILLA_FIVE_HOME/mozilla-thunderbird -P your-profile -compose $url
fi[/I]

this will just open a composer window for you, if thunderbird is already running. you should replace *-P your-profile* with the name of the profile you're using.

Then, open the Preferred Application Settings and enter "path-to/mailto.sh %s" as custom mail reader.

Hope that helps!

       - Riko

---

