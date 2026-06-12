---
title: "how to update Firefox?"
date: 2009-01-11
forum: General Help
---

### Post by TimDaniels on 2009-01-11
My v. 3.0.3 Firefox has been superceded by v. 3.0.5 .
What is the usual way to update Firefox (in detail, please)?
Does one remove the ~/.mozilla/firefox folder and then download
the v.3.0.5 .tar file and install that?  If so, to where does
one put the extracted files and how does one start the
installation?

Or does one go to Synaptic Manager and tell it to update
Firefox?  If so, how?

*TimDaniels*

---

### Post by gettinoriginal on 2009-01-11
Firefox 3.05 should be in your Synaptic Package Manager.  You do not have to delete individual files, but deleting 3.02 (Also in Synaptic) before installing 3.05 is recommended.

---

### Post by namdung on 2009-01-11
```
sudo apt-get update
sudo apt-get upgrade
```

This should not only upgrade your Firefox but also other applications.

Hardy has Firefox 3.0.4 in and Intrepid has 3.0.5 the repositories as of today.

---

### Post by TimDaniels on 2009-01-11
> **gettinoriginal said:**
> Firefox 3.05 should be in your Synaptic Package Manager.  You do not have to delete individual files, but deleting 3.02 (Also in Synaptic) before installing 3.05 is recommended.

Synaptic Package Manager listed Firefox 3.0.3.  I didn't know
how to tell it to delete an app, so I tried updating with
Update Manager.  After it updated 101(!) files, I checked again
with Synaptic Package Manager, and it listed Firefox 3.0.5, so
I guess Firefox got updated.  Unfortunately, I had deleted the
old Firefox icon from the menu bar, and it hasn't been replaced
by the upgrade.  So I got a couple questions:

1) How does one put the clickable icon for Firefox back in the
   menu bar at the top of the screen?

2) How does one tell Synaptic Package Manager to delete an
   app and then to install the app's newer version?

Tx for any info.

*TimDaniels*

---

### Post by TimDaniels on 2009-01-11
> **namdung said:**
> ```
sudo apt-get update
sudo apt-get upgrade
```

This should not only upgrade your Firefox but also other applications.

Hardy has Firefox 3.0.4 in and Intrepid has 3.0.5 the repositories as of today.

Thanks for the command lines.  Would they also upgrade
Ubuntu from 8.04 to 8.10 (which I would want to avoid doing)?

How does one upgrade Firefox using just a GUI wizard (which I
presume would be Synaptic Package Manager)?  Which buttons
must one click to remove an app and then install the app's
newer version?

*TimDaniels*

---

### Post by gettinoriginal on 2009-01-11
For Synaptic, just click on the one you are installing or uninstalling, and choose the correct function.
To get the firefox icon back on your panel, go to Applications > Internet > Firefox, right click and choose add to panel.  :p

---

### Post by bliffle on 2009-01-11
I'm trying to upgrade my Firefox (which HELP...ABOUT says is 3.04b) with the latest, so I DLed the 3.05 package, which is a "*.bz2" file. 

I couldn't figure out what to do next so I poked around some more and ended up with "ubuntuzilla", read the instructions and followed th install instructions and firefox still says it's 3.04b.

I don't know what to try next.

I already tried Synaptics, which found nothing.

---

### Post by mcduck on 2009-01-11
The Update Manager (in System/Administration) will update all your programs. Start it, click "check"-button and if any updates appear, then the "Install Updates"-button.

You can do the same with Synaptic Package Manager: Open Synaptic, click "Reload" to update package information, then click "Mark All Upgrades" and after that, "Apply".

If you want to see available updates before pressing "Apply", you can select "Custom Filters" from the menu in bottom left corner, and then "Upgradeable(upstream) from the list on the left side. (You still need to reload the package information first).

To upgrade only one package with Synaptic you can right-click the package and select "Mark for Upgrade", and then the "Apply"-button. But the update manager really handles all of this automatically, as soon as new package versions get into Ubuntu's repositories it will inform you about available updates..

(Doing any of these will _not_ upgrade you to next Ubuntu version)

---

### Post by nanotube on 2009-01-11
> **bliffle said:**
> I'm trying to upgrade my Firefox (which HELP...ABOUT says is 3.04b) with the latest, so I DLed the 3.05 package, which is a "*.bz2" file. 

I couldn't figure out what to do next so I poked around some more and ended up with "ubuntuzilla", read the instructions and followed th install instructions and firefox still says it's 3.04b.

I don't know what to try next.

I already tried Synaptics, which found nothing.

did the ubuntuzilla install go through ok? did you restart firefox?

---

### Post by bliffle on 2009-01-11
The ubuntuzilla seemed to go smoothly, went to completion and end nicely.

I stopped firefox before running 'zilla and restarted afterwards.

---

### Post by nanotube on 2009-01-11
> **bliffle said:**
> The ubuntuzilla seemed to go smoothly, went to completion and end nicely.

I stopped firefox before running 'zilla and restarted afterwards.

hmm, could you please post the output of the following two commands:
```
ls -al /usr/bin/firefox
```
```
firefox --version
```

---

### Post by Slim Odds on 2009-01-11
Enable "backports" in the Sofware Sources->Updates

---

### Post by TimDaniels on 2009-01-11
> **gettinoriginal said:**
> For Synaptic, just click on the one you are installing or uninstalling, and choose the correct function.
To get the firefox icon back on your panel, go to Applications > Internet > Firefox, right click and choose add to panel.  :p

Thanks for both comments.  The icon is back on the menu bar, and
the Firefox help panel says that it's version 3.0.5.

*TimDaniels*

---

### Post by gettinoriginal on 2009-01-11
Glad it's fixed, please go to thread tools and mark this as solved.  :p

---

### Post by TimDaniels on 2009-01-11
> **mcduck said:**
> The Update Manager (in System/Administration) will update all your programs. Start it, click "check"-button and if any updates appear, then the "Install Updates"-button.

Can the Update Manager be told to update just a particular app?


> You can do the same with Synaptic Package Manager: Open Synaptic, click "Reload" to update package information, then click "Mark All Upgrades" and after that, "Apply".

If you want to see available updates before pressing "Apply", you can select "Custom Filters" from the menu in bottom left corner, and then "Upgradeable(upstream) from the list on the left side. (You still need to reload the package information first).

To upgrade only one package with Synaptic you can right-click the package and select "Mark for Upgrade", and then the "Apply"-button. But the update manager really handles all of this automatically, as soon as new package versions get into Ubuntu's repositories it will inform you about available updates..

When I right-click on Firefox in Synaptic Package Manager now,
the option to Mark for Upgrade is greyed out.  In the future,
if Reload finds that Firefox has an upgrade available, will
Mark for Upgrade then become a selectable option?

> (Doing any of these will _not_ upgrade you to next Ubuntu version)

Thanks for the info!

*TimDaniels*

---

### Post by gettinoriginal on 2009-01-11
question 1 = no
question 2 = I have always found it preferable to uninstall an old version of firefox before installing the new one, but yes, upgrade will be available to you.

---

