---
title: "Sharing Firefox profile, working slow, very slow"
date: 2009-11-20
forum: Desktop Environments
---

### Post by darkod on 2009-11-20
Hello.
I am new to Ubuntu but I can find my way around computers so any advice doesn't need to be too detailed. I need some help about sharing my Firefox profile with Windows 7.
I have a ntfs data partition, I put my profile folder there. Changed the profiles.ini in Windows, that's working fine.
In Ubuntu, I used ntfs-config and set up automatic mounting of the data partition, it's in /etc/fstab, all is working fine. In profiles.ini I entered the appropriate path.
Firefox is finding the profile OK, but it seems really slow. On few occasions when I clicked the X to close firefox in Ubuntu, it didn't close right away and after few seconds window popped up about being not responsive or similar, that you can force quit but risk unsaved data. Before even making up your mind about the force quit that window closes and firefox shuts down by itself, no crashing. However that already happened few times.
Temporary I edited profiles.ini in Ubuntu back to the Ubuntu default profile.
Am I doing something wrong? Anything needed for such sharing of profiles for firefox to work?
I have no special add-ons, just standard ones for flash, and similar.
I did the same for Thunderbird and it seems it's working fine. I can't really say that it's slower. But with firefox it's really noticeable.
Thanks in advance for any ideas.

---

### Post by lovinglinux on 2009-11-20
I don't recommend sharing a profile between two different OS the way you are doing, since there are extensions and Firefox settings that are OS dependent. Instead, use [Mozilla Labs - Weave Sync](https://addons.mozilla.org/en-US/firefox/addon/10868) extension.

Additionally, your Firefox might be needing some maintenance. See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by oldfred on 2009-11-20
I created a FAT32 partition (before NTFS linux driver wrote reliably) 2-3 years ago and moved both firefox and thunderbird to the shared partition. I then edited the profiles in windows and linux to look the the common partition rather than the local one. It still worked even when I converted from Firefox version 2 to 3 on both windows & ubuntu. 
More info:

[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)

I have noticed with 3.5 in 9.04 that it seems a little slower but not as bad as you have said. I was blaming that on it being Shiretoko, not a true Firefox. I am as we speak in the process of converting from my Fat32 partition to NTFS. I have a clean install of Karmic in another partition and have to move home and change all sorts of stuff since I have upgraded every 6 months for about 3 years. Too much cruft but many customized settings.

---

### Post by oldfred on 2009-11-21
An update, I copied the shared partition to NTFS and modified my Karmic profile to use the new copy in the NTFS. It runs just fine, slight hesitation on initial start-up and everything else is noticeably faster than in 9.04. I still need to run the cleanup of the database, I know it has lots of stuff in it.

---

### Post by darkod on 2009-11-21
Thanks for the replies. I noticed with firefox extensions and add-ons can be a problem but I'm not using anything special.
Thunderbird seems fine with working this way maybe because there are no plugins like firefox has for flash etc. At the moment I returned to separate profiles for firefox, I'll take a look at the links for sure. At the moment as a partial solution for firefox I am using Xmarks add-on which syncs bookmarks and that was most important for me. In fact it can sync them on my netbook too which is even better solution so I might leave as it is, one win profile and one ubuntu profile.

---

