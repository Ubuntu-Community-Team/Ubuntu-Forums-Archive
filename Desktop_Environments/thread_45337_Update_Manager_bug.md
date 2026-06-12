---
title: "Update Manager bug?"
date: 2005-06-29
forum: Desktop Environments
---

### Post by blueturtl on 2005-06-29
The Update Manager in the upper right corner of my screen tells me there is an update available for the WGET utility. However the version installed and the version suggested are identical (1.9.1-10ubuntu2.1). If I try reinstalling it the program simply ignores the apply command. I take it somehow the Update Manager just doesn't see the new wget is already installed. Where do I need to go and what do I need to do to remove the unnecessary update from my recommended updates list?

Note: the problem first appeared with two updates available this morning, one of them being this WGET utility (I can't remember what the other package was).. anyway: after downloading and installing the new packages the WGET utility still remains in the listed available updates. Help would be appreciated, although this isn't a very serious bug.

---

### Post by nocturn on 2005-06-30
Maybe purging wget (with synaptic) and reinstalling it does the trick....

---

### Post by blueturtl on 2005-06-30
What, you mean like uninstalling and then reinstalling it? It did cross my mind, but removing wget would also remove a lot of other vital system packages so I didn't feel like taking any chances. Simply reinstalling the package with Synaptic didn't change the situation. This is just wild speculation, but my system was reset quite recently by a thunderstorm and I was wondering if this bug could be caused by some sort of file system corruption? I know EXT3 is supposed to be very fault tolerant, but right now I have no other clues as to what could be wrong... Is there a tool to check the filesystem included with Ubuntu?

---

### Post by blueturtl on 2005-06-30
Ok, it was my bad. For some reason I didn't remember anymore I had Synaptic set up to prefer packages from Hoary instead of the latest available packages (in this case from Hoary Security). Once I checked this setting I was able to download and install the latest version of WGET which was the same version number, however ending with 2.1 instead of 2.0. All is well in Ubuntuland once again (and to think I actually thought I'd found a bug..)  :wink: 

I would like to know though if there is a way to check the filesystem for damage.

---

### Post by varunus on 2005-06-30
You can use the fsck utility to check for filesystem integrity.  It can fix most problems too.  You'll have to have the partition unmounted to check it though.

---

### Post by obaeko on 2005-07-22
[QUOTE=blueturtl]The Update Manager in the upper right corner of my screen tells me there is an update available for the WGET utility. However the version installed and the version suggested are identical (1.9.1-10ubuntu2.1). If I try reinstalling it the program simply ignores the apply command. I take it somehow the Update Manager just doesn't see the new wget is already installed. Where do I need to go and what do I need to do to remove the unnecessary update from my recommended updates list?

Note: the problem first appeared with two updates available this morning, one of them being this WGET utility (I can't remember what the other package was).. anyway: after downloading and installing the new packages the WGET utility still remains in the listed available updates. Help would be appreciated, although this isn't a very serious bug.[/QUOTE]

Hi,
I have a similar problem. The update manager tells me: "There are 8 updates available", and the icon has a red sign (Ø) (it is a "not allowed" sign like 'Ø' except that the slash is the other way (back slash). I'm not sure, but I would guess that the red sign indicates that something is wrong.

When I open the update manager I get a list of 8 packages to install. (I have also tried reload)
When I click Install, nothing happens for about 10 seconds, and the same list is still presented.
When I open 'Synaptic package manager' it is telling me that the latest versions of the listed packages are installed. (The same versions as the update manager wants to install) I have only checked the 3 first packages.



Can anyone help me? 

Please  ](*,)

---

### Post by blueturtl on 2005-07-25
To be more spesific on how I fixed this: to me the version numbers seemed to be exact, but there was a slight difference at the very end you might not notice if you look at them quickly.

How I solved it:
Open Synaptic
Goto Settings menu, open Preferences
Select the Distribution tab
Check that you have Always prefer the highest version enabled.

If you have any of the other options, it might not update a package with a higher version since it's set to favour packages by either the team or the security branch.

**NOTE: If you have added new repositories please keep in mind that some of the new repositories may contain software that isn't verified by the Ubuntu team. These packages will be suggested for update by the Update manager when set to prefer the highest version although their level of security or stability might not be flawless.**

---

