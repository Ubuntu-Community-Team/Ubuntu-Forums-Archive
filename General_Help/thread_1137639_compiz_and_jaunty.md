---
title: "compiz and jaunty"
date: 2009-04-25
forum: General Help
---

### Post by skippymo on 2009-04-25
is compiz broke with jaunty i have the manager and none of my settings applying....help.

---

### Post by Sef on 2009-04-25
How did you update to Jaunty: clean install, upgrade, or other?

---

### Post by skippymo on 2009-04-25
upgrade, took forever to download the packages tho, seems fine everything is good except the eyecandy a.k.a compiz


thanks

---

### Post by lovinglinux on 2009-04-25
Try creating a new profile. It wasn't saving my settings until I did this and imported the profile backup to the new profile.

---

### Post by skippymo on 2009-04-25
i'm not sure how to do that. can you walk me thru it?

thanks again

---

### Post by wfp on 2009-04-25
Also under compizConfig Setting Manager, and under effects do you have Animations Add-on Checked.

---

### Post by skippymo on 2009-04-25
yea it's checked..

---

### Post by lovinglinux on 2009-04-25
> **skippymo said:**
> i'm not sure how to do that. can you walk me thru it?

Sure.  

[list][*] open CompizConfig Settings Manager
[*] click the preferences button in the lower left
[*] click the "+" button next to the Profile drop-down menu
[*] type the name of the profile
[*] click "+ Add" button[/list]

It will auto select the new profile. You can also export and import profiles from there.

---

### Post by wfp on 2009-04-25
To Create a new Profile Open CompizConfig-Settings-Manger. Now open Preferences it's on the bottom> Now under Profile click the add button> Put in new name of profile> now add what ever eye candy you want your starting fresh. Or you can import your old profile back to your new profile. Gee I am getting older and slower at typing lol. ^

---

### Post by skippymo on 2009-04-25
no dice guys....created a new profile and everything looks good in it, but still no animations

---

### Post by wfp on 2009-04-25
Sorry have to ask do you have desktops effects enabled.

---

### Post by skippymo on 2009-04-26
yea animations are on and i can't find a desktop effects button or plugin am i stupid or just missing it?

thanks

---

### Post by wfp on 2009-04-26
Right click your desktop: Choose Change Desktop Appearance from the drop down menu:> Click on the Visual Effects tab and make sure you have normal or extra checked. Make sure your driver is enabled also. On your Top or bottom panel Go to > system>Administration>Hardware Driveres.

---

### Post by skippymo on 2009-04-26
desktop effects cannot be enabled

is this a driver issue? if so i have a dell d630. any pointers to get the right driver? why did it work with intrepid and not jaunty then? pulling my hair out.

thanks for the help so far.

---

### Post by wfp on 2009-04-27
Did you do as I suggested to enable your driver. On your panel System>Administration>Hardware Drivers

---

### Post by duanedesign on 2009-04-27
What graphics card are you using

```
lspci
```

here is a list of cards blacklisted with the new release. Issues with these cards have been known for awhile and were discussed in the release notes.

[http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist)

here is a bug report discussing the problem

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363967](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/363967)

here is a Launchpad Question on the issue

[https://answers.launchpad.net/ubuntu/+question/67975](https://answers.launchpad.net/ubuntu/+question/67975)

there is a workaround to un blacklist your card. Though this is not recommended.

Also I have seen people running Metacity with compositing enabled has prevented them from turning on Compiz. If you have enabled compositing in Metacity

this is the command to disable it:

```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool false
```

---

