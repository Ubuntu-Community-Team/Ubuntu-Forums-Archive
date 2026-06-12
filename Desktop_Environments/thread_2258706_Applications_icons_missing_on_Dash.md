---
title: "Applications icons missing on Dash"
date: 2014-12-29
forum: Desktop Environments
---

### Post by mary2 on 2014-12-29
I am unable to use dash to find applications.  I can find folders, music, etc. but the applications icons are all missing.  

When I log in as a "guest" dash works normally.  

I have tried deleting the .cache/unity folder and that does not fix the issue.

I have tried re-installing unity and updating unity and that does not work.  

I have tried the command: unity --reset in a terminal and it replies: 
ERROR: the reset option is now deprecated

I have tried unity --reset-icons and it returns a long list of errors and does not fix anything

I have installed the Unity Tweak Tool and used that to attempt to restore defaults.

The only way we can run applications is to copy the start icons to the desktop from the computer/user/share/applications directory.   We are not very good at Ubuntu and have tried to fix this ourselves but cannot find the solution.  Any help would be greatly appreciated.

---

### Post by mc4man on 2014-12-29
Edit: would be good to know what Ubuntu release, am assuming 14.04 (Trusty

On the odd chance you disabled it run this command in a terminal (ctrl+alt+t
```
gsettings get com.canonical.Unity.Lenses disabled-scopes
```
post the result 
(- default would be @as [ ] meaning no scopes disabled

---

### Post by mary2 on 2014-12-29
Sorry I omitted the Ubuntu release.  Yes, we are using Trusty and have been using it successfully for about three months.   This problem had happened intermittently a few times in the past week and had resolved on a re-boot.  Now it is permanent.  I have tried to figure out if we changed a setting but can't see anything unusual that we did.  If we made a change it was unintentional.  

To the following command in a terminal
"gsettings get com.canonical.Unity.Lenses disabled-scopes"

I get 
**['applications-applications.scope']**

Does that mean it is not disabled?

Thanks so much for your help.

---

### Post by mc4man on 2014-12-29
No it means you've disabled it, so a simple fix - in a terminal run - 
```
gsettings set com.canonical.Unity.Lenses disabled-scopes "[]"
```

edit:
Just as a quick follow up -  (assuming the command above fixes
What likely happened is this - 
In the Applications lens (r. click on Dash icon > Applications),  if you scroll down a bit is a section called "Dash Plugins"
When you click on a plugin it gives you the option to Disable (if enabled) or Enable (if disabled.

So probably you or your's inadvertently disabled the Applications scope.
An alternate to the command I gave you would have been to do that in the Dash, ie. re-enable the Dash plugin - Applications by clicking on it in the Dash Plugins section which should always be there in the Applications lens
( in your current case where only 1 scope was disabled a command was easier to initially relay..

---

### Post by mary2 on 2014-12-30
Thank you so much.  Your quick fix worked and we very much appreciate your explaining how it might have happened.  We really do love Ubuntu and I'm so appreciative that there are people that give their time to help us learn.

---

