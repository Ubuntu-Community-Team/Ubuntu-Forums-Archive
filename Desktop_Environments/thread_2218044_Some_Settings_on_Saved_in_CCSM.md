---
title: "Some Settings on Saved in CCSM"
date: 2014-04-19
forum: Desktop Environments
---

### Post by milliman on 2014-04-19
Since my upgrade to 14.04, my Compiz settings come and go.  After the upgrade I had to restore many of my Compiz settings but some will spontaneously disappear or revert back to default values.  The most problematic are the desktop size settings under General Options.  Once I set the values, they revert to their default values when I to back to the tab.  This affects my ability to use Desktop Cube and other plugins.  I have searched high and low for a remedy but I cannot find how to keep the values set to what I want.  I thought that the problem may be related to my profile so I logged into a "clean" account and I could not set the number of desktops either.  This seems to be an issue that has crept in this release, but I find it hard to believe that it made it into the release.  I have even tried to set these values through Unity Tweak and Ubuntu Tweak.  Does anyone have any suggestions?

Thanks,
Mark

---

### Post by grahammechanical on 2014-04-19
Is this a clean install of 14.04 or an upgrade from a previous version of Ubuntu. You could try re-installing CCSM and compiz-plugins-extra.

A lot of the Compiz Configuration Settings Manager plugins were removed from CCSM and we need to install compiz-plugins-extra to get some of them back. If you upgraded from an earlier version of Ubuntu there may be settings from plugins that are no longer supported and they may be causing this problem.

Compiz window/compositor manager is part of the Ubuntu 14.04 release but Compiz Configuration Settings Manager is not part of the 14.04 release. There is a difference. And things like CCSM need to be tested during the 26 weeks development period. And that in turn needs people willing to test the development version. Otherwise bugs make it into the final release. 

Regards.

---

### Post by kansasnoob on 2014-04-19
It's not limited only to Compiz. I've been testing Flashback w/Metacity and some settings in dconf revert on reboot or logout :(

Something broke in the last 10 days or so :cry:

This is why I wait until the first point release of each LTS to start upgrading my production machines.

---

### Post by milliman on 2014-04-19
This is an upgrade from 13.10.  I already reinstalled compiz-plugins-extra and apt said that I am at the latest version.  The problem with keeping the desktop settings is not limited to CCSM.  My settings to stick using the Unity Tweak Tool either.  I think it has something to do with dconf, but I need to play with it more.

---

### Post by milliman on 2014-04-19
I didn't jump on the beta bandwagon this time around so I cannot vouch for how it may have worked earlier.  I'll have to search to see if there are any bugs that are related to this issue.

---

### Post by mc4man on 2014-04-19
"The most problematic are the desktop size settings under General Options. Once I set the values, they revert to their default values when I to back to the tab"
Well once you set it there's no good  reason to re-open that tab unless you want to change the values, otherwise it should stay at what you set.

There are a couple of factors at work  here, but if you wish you can do a simple workaround. 
(though as mentioned why go there unless you mean to change anyway..

The default for hsize & vsize are 1, set both in /usr/share/compiz/core.xml & /usr/share/glib-2.0/schemas/org.compiz.core.gschema.xml
You **want to leave /usr/share/compiz/core.xml as is** but edit /usr/share/glib-2.0/schemas/org.compiz.core.gschema.xml to whatever you want, typically 4 for hsize. 
So open the file in a root text editor & change hsize, line 200 - 
Ex.
```
 </key>
    <key type="i" name="hsize">
      <default>4</default>
      <summary>Horizontal Virtual Size</summary>
      <description>Screen size multiplier for horizontal virtual size (1 - 32)</description>
 </key>
```
save & exit editor
Then in terminal - 
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas/
```
This command **must complete without error or comment**, if not for some reason don't log out till it does.
Then log out/in, go to the setting in ccsm. It will likely show 1 then will auto switch to your chosen number

Otherwise the only custom settings I see that get reverted or 'lost' are those for the commands plugin. In this case the only way around is to integrate the command & it's binding(s) which is a bit more complicated & has to be done in source.

---

### Post by PJs Ronin on 2014-04-19
> **kansasnoob said:**
> It's not limited only to Compiz. I've been testing Flashback w/Metacity and some settings in dconf revert on reboot or logout :(

**Something broke in the last 10 days or so** :cry:

This is why I wait until the first point release of each LTS to start upgrading my production machines.

I am of the same opinion.   Trusty was humming for me all through the dev cycle and actually became my production system about 2 weeks ago.   However, something changed in the last 3-5 days that has made themes/fonts a nightmare for me.   I'm back on Saucy for the time being.

---

### Post by milliman on 2014-04-19
Thanks for the effective workaround, but there is still a bug between how Unity and Compiz handle these settings.  I have found other ways to do what the Commands plugin does too.  I think that CCSM needs to catch up with this release of Ubuntu.

---

