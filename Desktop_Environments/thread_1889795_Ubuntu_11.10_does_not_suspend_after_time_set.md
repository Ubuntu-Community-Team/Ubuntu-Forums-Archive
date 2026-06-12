---
title: "Ubuntu 11.10 does not suspend after time set"
date: 2011-12-02
forum: Desktop Environments
---

### Post by WhiteDogBe on 2011-12-02
Dear Ubuntu Forum,

After an upgrade from Ubunto 11.04 to 11.10 my Ubuntu no longer suspends after the time set. Suspend itself works fine, but I would like to suspend my machine automatically to save some money on the energy bill :)

As I also run XBMC on that machine, suspend is toggled on / off with my XBMC launch script. These are the commands I use to enable suspend:
```
gsettings set org.gnome.settings-daemon.plugins.power sleep-display-battery 600
gsettings set org.gnome.settings-daemon.plugins.power sleep-display-ac 600
gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac true
gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 1800
gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type 'suspend'
```System Settings > Power also reflects these settings with "Suspend when inactive for: 30 minutes".

I totally understand that there are probably a lot of reasons why this is not working as intended, but if someone could point me in the right direction:
- Which log files I could check
- Check if the idle timer is running OK
- Alternative methods to force this
- Other settings that might affect this

It would really help a lot :)

---

### Post by oscarivera9 on 2011-12-11
I am looking for a similar answer to what you are asking.  I imagine that after your update to 11.10 the suspend setting doesn't work the same as before because prior to 11.10 we had more options regarding shutdown and suspend.  So maybe your old settings are incompatible with the new options.  But that is just a guess.
Regardless, I want to find out what other people say in response to your question.

---

### Post by Ai1dRo0kNotBot on 2012-01-07
Found solution over here:
[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

---

