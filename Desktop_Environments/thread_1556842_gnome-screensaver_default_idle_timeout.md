---
title: "gnome-screensaver default idle timeout"
date: 2010-08-20
forum: Desktop Environments
---

### Post by nephew.tim on 2010-08-20
Hi All,

Perhaps we are overcomplicating this, but have been battling with the following for a few days now, on and off...thought it best to scream for help!! ;)

We have created a custom distribution disk for Ubuntu and plan on giving it to our hardware vendors, with all our standard settings already integrated. We have already setup a variety of applications, amongst them gnome-screensaver, in order to use our organisational title on the flying GLText Screensaver. However, our issue is that we cannot find where to modify the idle timeout. Currently the users will complain about the timeout being too short (they socialise alot :lolflag: )!!...

It seems that Ubuntu (or Gnome) defaults to 5mins, but other than the gnome-screensaver-preferences, there seems to be no other way to adjust the time to our "standard" of 15-minutes. As new users are constantly being added to our training machines etc., we need this default to be applied to all new users.

We have tried to search for all "timeout" or "idle" values under the installed files for gnome-screensaver (dpkg -L), without any results. 

In an attempt to find the differences: we even created a new user, copied their home directory (-a) after modifying the setting using gnome-screensaver-preferences and then removing/re-added the user, in order to do a comparison(diff/sort), does not give us clue as to where to insert our "custom" timeout value. It seems to be embedded into the binary, but we cannot see it...

We have tried the "gconftool-2", also without any success at all...

We have also tried to contact the author of gnome-screensaver, however, he has not come back to us as yet...:(

Anyone out there, who could assist? :KS

---

### Post by nephew.tim on 2010-08-23
After much investigation (and a change of search variables), we found the following:

In order to manipulate the idle-timeout, just include the following in your /etc/skel/.gconf/desktop/gnome/

1. mkdir /etc/skel/.gconf/desktop/gnome/session
2. vi %gconf.xml
3. Add the following into the XML file:

> 
<?xml version="1.0"?>
<gconf>
	<entry name="idle_delay" mtime="1282047258" type="int" value="2"/>
</gconf>


This will give the session a delay of 2-minutes, as per the value.

Hope this helps...

:p

---

