---
title: "Unity/background misbehaving"
date: 2013-08-25
forum: Desktop Environments
---

### Post by niemand on 2013-08-25
Let me start with I have been searching for similar problems for two days now with no real luck.

I just ran the software updates for Ubuntu 13.04 and now Unity is really misbehaving. I have been running Ubuntu since the Dapper Drake days and have become so accustomed to the software updates just working that I do not even pay attention to them anymore. So, I am not even sure what all changed.

One thing I did notice is that the kernel updated. So, using grub I booted the previous kernel. Problem persists. So, I doubt it is a driver problem, but for clarity I have a recent model NVidia Optimus card and use bumblebee to even get it working.

So, I thought it might be some setting because I heavily customize Unity. I logged in as guest to test this idea and sure enough, the guest account works just fine with the latest kernel. So, I think I have eliminated the kernel changes and the NVidia driver plus bumblebee. I think it also points clearly to come configuration item.

Searching the web, I found all of the same suggestions on how to reset Unity. I did the dconf reset -f /org/comviz and unity --reset-icons but this did not reset enough of them because Unity still misbehaves. I then tried setting most of the options back to the defaults by hand and found that I cannot change the background at all. I can change it in any of the various setting tools that I have and it remembers that change in the setting tool, but I always see my custom picture. I am starting to narrow it down, but I have run out of tests to further pinpoint the problem.

Here is a more or less complete list of the symptoms that I am seeing:

1) on first log in after boot, my custom wallpaper picture never updates independent of what is selected in my settings. I continue to see the grid dots, login dialog, and all other launcher popups that come up.

2) on subsequent logins (after a logout but not reboot) I have a totally black background. Launcher popups do not stick.

3) I cannot change my background. I can use system settings to change it and the settings remembers my selection, but I always see the backgrounds in (1) and (2).

4) When logged in, using <super> does nothing. I can open the dash from the upper left button and get any program started. After that, <super> works. If I moved to a clean worksapce, then <super> does not work until there is an application on the workspace. This bad behavior is the most annoying as I use many workspaces and really became attached to the <super> key. I should also note that this is NOT the behavior in the guest account.

At this point, I think I am most interested in a way to get my settings to be that of a fresh account like guest. As I already stated, the dconf reset and unity --reset-icons is not sufficient. I really need to wipe it clean and start again.

Another idea is to keep trying to isolate the real problem from this mass of symptoms, but I am at a loss for more testing. I am willing to test away if given some suggestions.

Any and all help is appreciated. Thanks.

---

### Post by mc4man on 2013-08-26
As far as background if you are using a solid color or gradient then that's bugged, a fix is in raring-proposed for the gnome-control-center-unity package (1.3daily13.06.14.1-0ubuntu1

To totally reset is a little involved but quite easy.
Open System Settings > Layout Settings > Options & enable "Key sequence to kill X server" (ctrl+alt+backspace) - screen
or running this command should do the same
```
gsettings set org.gnome.libgnomekbd.keyboard options "['terminate\tterminate:ctrl_alt_bksp']"
```

Then navigate in nautilus to ~/.cache, if there is a dconf folder then delete it. (not as important as the one below but get rid of if it exists.

Then navigate to ~/.config/dconf & delete the user file inside 
Immediately after deleting the above file go ctrl+alt+backspace to kill X, should bring you to the login screen, login in & you'll have the default installed settings again

(- The reason to kill X instead of just deleting the user file & restarting or logging out is your old user settings will be re-created if done that way. This behavior is new in 13.04 so you either must delete the file & immediately kill X or delete that file from a different install or user account.

---

### Post by coolcat1979 on 2013-08-26
I seem to have this with every major update not sure why but the way I fix it because I can't see anything but my shortcuts and folders on my desktop is right click and change desktop then go to all settings then software & update, additional drivers and change my proprietary vid driver then ctrl+alt+t .....in terminal go ccsm and reenable unity plugin (for some reason it becomes unenabled) then ctrl+alt+del to log out and restart my comp comes back like normal......... seems to be an ongoing bug with Unity hope this helps

---

### Post by niemand on 2013-08-26
Well, I do not want to call this solved, but it kind of is. I used the directions given by mc4man above to clean my unity settings. I hate to say that even deleting the two dconf directories, many of the settings remain. Luckily it did erase the one causing the problem. I then went through the system settings, ubuntu tweaks, and unity tweaks to customize unity again. Problem immediately returned. Deleted dconf again. Customized unity through system settings and ubuntu tweaks. Problem returned immediately. Deleted dconf yet again. Customized just through system settings. Everything is fine. I am kindo of bored tweaking it, but I need to try unity tweaks without ubuntu tweaks to see if I get lost again. At any rate, it is simply a customization value that is causing the problem.

---

### Post by mc4man on 2013-08-26
> **niemand said:**
>  At any rate, it is simply a customization value that is causing the problem.
There should be  nothing that any of those tweak apps do that you can't do yourself, either thru dconf-editor or ccsm
(what were you using that/those apps to 'tweak'?

---

### Post by niemand on 2013-08-26
Further tested it. If I use ubuntu tweak or unity tweak, it really messes up the display. If I use ccsm and set all the value, then it works just fine. I guess it is back to ccsm. I am not trying to explain it, but this is how it is working out. At least I can have my customization and still be able to use the <super> key with indiscretion.

---

### Post by niemand on 2013-08-26
number of workspaces, sloppy pointer, and other stuff not in system setting but all dealing with unity customization.

---

### Post by mc4man on 2013-08-27
> **niemand said:**
> number of workspaces, sloppy pointer, and other stuff not in system setting but all dealing with unity customization.
While I'm sure those tweak tools are convenient obviously they may cause issues from time to time & so should be used judicially or not at all
In regards to what you mentioned - 
sloppy mouse - screen 1
number of workspaces in unity/compiz - best done in ccsm (compizconfig-settings-manager),  as compiz settings in dconf are sparse & some don't show until you actually make a change elsewhere (like in ccsm
screen 2

---

