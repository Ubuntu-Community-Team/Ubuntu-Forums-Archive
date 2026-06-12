---
title: "Another Unity shortcut/workspace question"
date: 2012-07-06
forum: Desktop Environments
---

### Post by iridium191 on 2012-07-06
Hi forum,

Is there any way to see all open windows for a particular application across ALL workspaces? If I use ALT-TAB and select an application I can see all instances of the application in the CURRENT workspace. However, I can't see open windows for that application that may be hidden on other workspaces.

For example, if I'm using multiple Terminal windows across all four workspaces I can't see a summary of all the Terminal Windows. Instead I have to vistit all four workspaces and ALT-TAB to find them.

I'm sure I could do this in 11.10 (for Terminal at least - some apps like Remmina always seemed to be a problem ). 

 Any help would be much appreciated

---

### Post by Ceannfaolaidh on 2012-07-06
There are actually a couple different ways you can go about doing this. First, if you don't have it already, install CompizConfig Settings Manager (CCSM):
```
sudo apt-get install compizconfig-settings-manager
```
...or grab it from the Ubuntu Software Center.

Next, open CCSM from the dash and navigate to Desktop > Ubuntu Unity Plugin > Switcher. Uncheck the box that says "Bias alt-tab to prefer windows on the current viewport."

If you'd like to preserve the functionality of Alt-Tab when you aren't spread across workspaces, you can just use Ctrl+Alt+Tab, but it's an awkward combination. If you like, you can change it from the same tab of CCSM by modifying the "Key to start the switcher for all viewports" setting.

---

### Post by iridium191 on 2012-07-06
Thanks Ceannfaolaidh,

That did the the job and as a bonus I get to play around with CCSM settings!

Even Remmina seems to play nice - I'm productive again!

---

