---
title: "Emerald Theme Manager-no themes show up"
date: 2008-01-16
forum: Desktop Effects &amp; Customization
---

### Post by Horrendus01 on 2008-01-16
Okay, I know other people have made threads about this before, but I have yet to find an answer as to why this happens or a fix for it.  I am using the Official Compiz that comes with Gutsy, and I installed Emerald.  I open the Emerald Theme Manager, type in the svn command, and click the buttons to fetch the themes.  Dialog shows up, I think things are going great.  I switch to the themes tab, nothing shows up.  I open Synaptic, I search for Emerald, no Emerald-themes package shows.  I looked on other sites and have found no fix to this issue.  Not even the theme that it is using as default is showing up.  Before I did this install, I had Fiesty, where I used a Beryl/Emerald setup, which worked fine, and all my themes showed up.  Can anyone shed some light on the issue for me and perhaps let me know what I am doing wrong?  Any help would be greatly appreciated.

Edit:

I was able to manually add a theme from Gnome-look.org, but I would like to have the option of listing the themes that come with the emerald-themes package as well, as I did like a few of them.

---

### Post by FuturePilot on 2008-01-17
Do you have subversion installed? You need to 
```
sudo apt-get install subversion
```
for that svn command listed in Emerald Theme Manager to work.
When you run the command make sure you accept the certificate permanently. Then try fetching them.

---

