---
title: "Red Triangle with Exclamation Point Inside"
date: 2015-03-18
forum: Desktop Environments
---

### Post by gabmuks on 2015-03-18
I keep getting this triangle at top of screen.

When I click on it, it says to click on "show updates".

After clicking on "Show Updates", it says...

"The Software On This Computer Is Up To Date"

How can I get rid of this triangle?

---

### Post by dino99 on 2015-03-18
sudo apt-get purge update-notifier

---

### Post by grahammechanical on 2015-03-18
It says more than "show updates, " is this not true? It also advises us that there is a problem with our internet connection or the installed packages.

I am using the development version of Ubuntu. I update daily as soon as I am logged in. And later in the day I get that red warning triangle and I know why I am getting it. The development version does not have all the repositories open. Later in the day when Update Manager does a check for updates it finds that it cannot access all the repositories in my software sources list. So, it assumes that there is a problem with my internet connection and it posts that warning indicator. Update Manager offers a couple of possible reasons for the problem and includes an option to check for updates (show updates). Which is a way of testing the internet connection.

Have you installed software from a PPA? If so disable that PPA. That is just one thing we can do to stop that warning indicator from appearing. But what we do depends on what the problem is.

Regards.

---

### Post by vasa1 on 2015-03-18
> **9d9 said:**
> sudo apt-get purge update-notifier
Is that a good idea?

---

### Post by slickymaster on 2015-03-18
> **9d9 said:**
> sudo apt-get purge update-notifier
Why would the OP purge the update-notifier from his system? Like grahammechanical pointed out, it's there to serve several purposes, which are very well described [here]("https://wiki.ubuntu.com/SoftwareUpdates").

And besides, if the idea was to remove in order to add it back again to the system, the purge option wouldn't be advisable since it would delete the OP's local/config files for it, and those can not be restored by reinstalling the package.

---

### Post by vasa1 on 2015-03-18
> **slickymaster said:**
> ...
And besides, if the idea was to remove in order to add it back again to the system, the purge option wouldn't be advisable since it would delete the OP's local/config files for it, and those can not be restored by reinstalling the package.
Won't purge only remove config files located in the "system" and not local files? 

Anyway, I don't think recommending purging crucial software should be recommended lightly.

---

### Post by QIII on 2015-03-18
When the "check engine" light comes on, it is not wise to unplug the power to the lamp behind the instrument cluster to avoid irritation.

---

### Post by slickymaster on 2015-03-18
> **vasa1 said:**
> Won't purge only remove config files located in the "system" and not local files? 

Anyway, I don't think recommending purging crucial software should be recommended lightly.
When I say local, I'm not referring to ~. Configuration files residing in ~ are not usually affected by this command.

---

### Post by gabmuks on 2015-03-18
> **grahammechanical said:**
> It says more than "show updates, " is this not true? It also advises us that there is a problem with our internet connection or the installed packages.

I am using the development version of Ubuntu. I update daily as soon as I am logged in. And later in the day I get that red warning triangle and I know why I am getting it. The development version does not have all the repositories open. Later in the day when Update Manager does a check for updates it finds that it cannot access all the repositories in my software sources list. So, it assumes that there is a problem with my internet connection and it posts that warning indicator. Update Manager offers a couple of possible reasons for the problem and includes an option to check for updates (show updates). Which is a way of testing the internet connection.

Have you installed software from a PPA? If so disable that PPA. That is just one thing we can do to stop that warning indicator from appearing. But what we do depends on what the problem is.

Regards.

Yes I also get all the other messages that you have posted.

I will try to post here the details that are shown, perhaps
you could direct me what to do.

```

W:Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64+mac (20140722.2)/dists/trusty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64+mac (20140722.2)/dists/trusty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64+mac (20140722.2)/dists/trusty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64+mac (20140722.2)/dists/trusty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by slickymaster on 2015-03-18
> **gabmuks said:**
> Yes I also get all the other messages that you have posted.

I will try to post here the details that are shown, perhaps
you could direct me what to do.

```

W:Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64+mac (20140722.2)/dists/trusty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64+mac (20140722.2)/dists/trusty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64+mac (20140722.2)/dists/trusty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64+mac (20140722.2)/dists/trusty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.
```
You have your cdrom files enabled. So every time it tries to update it automatically looks for those files, which by definition are outdated. Just unselect that option in your Software & Updates GUI and uncheck the check-box near "Cdrom with Ubuntu 14.04"  and afterwards run```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by gabmuks on 2015-03-18
> **slickymaster said:**
> You have your cdrom files enabled. So every time it tries to update it automatically looks for those files, which by definition are outdated. Just unselect that option in your Software & Updates GUI and uncheck the check-box near "Cdrom with Ubuntu 14.04"  and afterwards run```
sudo apt-get update && sudo apt-get upgrade
```

Yes. Very good. Thank you, that worked. Triangle gone.

But can you tell me what that CDROM check box is for?

Is it for creating an Ubuntu install CD?

---

### Post by slickymaster on 2015-03-18
That's the software installation from CD ROM, the one you used to install Ubuntu in the first place. If you keep that check-box selected, your system will use the repositories on the CD as a possible software source but cannot access them (potentially because the CD is not in the drive). Assuming that you have an internet connection that you can use for installing new software (and updates) you can safely disable the repositories on the CD.

---

### Post by slickymaster on 2015-03-18
Please don't forget to mark the thread as [SOLVED]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") so other people searching the forums know that it provides a working solution.

---

### Post by gabmuks on 2015-03-18
> **slickymaster said:**
> That's the software installation from CD ROM, the one you used to install Ubuntu in the first place. If you keep that check-box selected, your system will use the repositories on the CD as a possible software source but cannot access them (potentially because the CD is not in the drive). Assuming that you have an internet connection that you can use for installing new software (and updates) you can safely disable the repositories on the CD.

Cool! Thank you all for your kind assistance.
And good day to you.

---

### Post by slickymaster on 2015-03-18
You're welcome. Happy *buntuing. ;)

---

### Post by Chevymaher on 2016-03-14
> **QIII said:**
> When the "check engine" light comes on, it is not wise to unplug the power to the lamp behind the instrument cluster to avoid irritation.
If the light is on due to a dealer issue(Repository) and the light is always on. And can not be turned off for the dealer problem. It has become useless. Ignored because it is always on. It is now the same as it having the bulb pulled. So if the issue cannot be fixed on this end the security issue is caused by the lack of ability to disable the empty repository signal. 

No AMD updates. I have followed all threads and nothing will make it stop. I can't upgrade because I have AMD. So in essence Ubuntu has abandoned this type of computer. The kernal did work. Now it will not. 

This is from the terminal. As suggested in the other thread. 

W: Failed to fetchhttp://archive.ubuntu.com/ubuntu/dists/trusty/Release  Unable to findexpected entry 'main'./binary-amd64/Packages' in Release file (Wrongsources.list entry or malformed file) 


E: Some index filesfailed to download. They have been ignored, or old ones used instead. 

All other updates were acquired from this terminal.

---

### Post by Chevymaher on 2016-03-19
For anyone interested. I re-formatted then re-installed. For whatever reason now it can find the files in the same repository it could not find before.

---

### Post by oldos2er on 2016-03-19
Old thread closed.

---

