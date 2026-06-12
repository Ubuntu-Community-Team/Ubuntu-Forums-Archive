---
title: "Removable media handling via media:/ VERY erratic (KDE 3.5)"
date: 2005-12-06
forum: Desktop Environments
---

### Post by mrowth on 2005-12-06
Upgraded to Breezy via fresh install, then apt update'd and upgrade'dd because KDE would crash horribly within minutes (complete with psychedelic display chaos). That helped. 

Then I upgraded to KDE 3.5 hoping to fix the problems detailed below. That didn't help.

None of my hard disk partitions showed up under media:/. The floppy did, and removable media (mostly!) did as well. I've seen this bug described several times, including here: [http://ubuntuforums.org/archive/index.php/t-79204.html](http://ubuntuforums.org/archive/index.php/t-79204.html). I followed the /etc/default/hal workaround, and that took care of the missing partitions.

CDs/DVDs behave just as erratically as before, though, and that's much more annoying. 

Some typical "just inserted a CD/DVD"-scenarios (no idea what happens when or why, even the very same disc in the very same drive can have different outcomes):

**Scenario 1: No access through media:/ at all**

1) Icon appears on desktop, labeled "DVD-ROM Disc" instead of the volume label.

2) Konqueror automatically opens a tab to "media:/hdc" (or hdd), but the disc appears to be blank (although it isn't) - ejecting and reinserting the disc may or may not help. 

3) Additionally, a dialogue box pops up: 
    "Open 'media:/hdc'? Type: Blank DVD -- Save As.../Open With.../Cancel" 
(Apparently the file to be opened/saved is "hdc"...). The same thing happens when I point Konq at media:/hdc.

4) I have to manually mount /media/cdrom0 (or /media/cdrom1 etc) to access the disc. This does not affect the broken-ness of the desktop and media:/ icons.

5) Sometimes, the disc never stops spinning noisily until it is unmounted.

6) Ejecting via "eject" in the icon's context menu may work... or not. There's no "unmount", this has to be done via a manual umount.


**Scenario 2: One Auto-open too many, but it mostly works**

1) Icon appears on desktop, labeled after the disc. 

2) Konqueror opens a tab to "media:/hdc" (or hdd) automatically. The contents are shown correctly.

3) Additionally, a dialogue box pops up: "A new medium has been detected. What do you want to do? Medium type: Unmounted CD Writer/Unmounted DVD/Mounted DVD...". 

When I select "Open in New Window":

4) A new tab opens to system:/media/hdc and shows the correct contents. not exist." 

5) The icon's "right-click-menu" has an option "Open Medium System Folder", which results in an error dialogue: "Could not find the program 'kio_media_realfolder'"

6) "Eject" and "unmount" in the same menu work.


[SIZE="1"]Those were the extreme cases, here're two more variations...

**Scenario 3: first it doesn't work, then it kinda does**

1) Icon appears on desktop, labeled after the disc or "K3b data project". 

2) Konqueror opens a new **empty** tab automatically.

3) Additionally, a dialogue box pops up: 
    "A new medium has been detected. What do you want to do? Medium type: Unmounted CD Writer/Unmounted DVD/Mounted DVD..." (alternates with no pattern I could detect even with the same discs inserted into the same drive). 

When I select "Open in New Window":

4) Another Konq tab opens, this time to"system:/media/hdc". This tab shows the correct directory.

5) The icon's "right-click-menu" has an option "Open Medium System Folder", which results in an error dialogue: "Could not find the program 'kio_media_realfolder'"

6) "Eject" and "unmount" in the same menu work.


**Scenario 4: first it kinda works, then it kinda doesn't**

1) Icon appears on desktop, labeled after the disc. 

2) Konqueror opens a tab to "media:/hdc" (or hdd) automatically. The contents are shown correctly.

3) Additionally, a dialogue box pops up: "A new medium has been detected. What do you want to do? Medium type: Unmounted CD Writer/Unmounted DVD/Mounted DVD...". 

When I select "Open in New Window":

4) The tab shows an error message: "An error occurred while loading system:/media/hdc: The file or folder media:/hdc does not exist." 

5) The icon's "right-click-menu" has an option "Open Medium System Folder", which results in an error dialogue: "Could not find the program 'kio_media_realfolder'"

6) "Eject" and "unmount" in the same menu work.[/SIZE]


So. Uhm. Help?

Oh, and Konq seems to have lost the menu item for choosing View Profiles. All I can do is save the profile it was launched with. Or perhaps I forgot where to look, there's nothing in any of the available menus though...

---

