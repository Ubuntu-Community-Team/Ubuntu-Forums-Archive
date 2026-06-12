---
title: "Discussion - https://help.ubuntu.com/community/MountingWindowsPartitions"
date: 2012-11-22
forum: Documentation and Community Wiki Discussions
---

### Post by coffeecat on 2012-11-22
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

This wiki page dates back to early 2006, was revised regularly until about about the middle of 2008, but has had only a few edits since and has been neglected (except for one minor edit in January this year) for two years now. My view: it needs a fundamental rewrite - or jettisoning. Just for starters, this would be my shopping list of changes:

[list][*]A new section near the beginning describing automounting NTFS/FAT32 partitions from the file manager. Why jump straight into configuring /etc/fstab when file manager mounting will be enough for many people? The "Mounting at Boot" section near the end could be brought up and incorporated with a few pros and cons about the use of the file manager or fstab.
[*]A warning about the potential hazards of mounting and writing to the Windows C: partition, the problems associated with hibernation in Windows 7/8, and leaving system and recovery partitions well alone.
[*]The misconception about ntfs-3g in Oneiric needs clearing up. (For the record - ntfs-3g does come as standard in Oneiric, but if you unnecessarily install ntfsprogs and don't pay attention to what the package manager is telling you, ntfs-3g will be uninstalled. I believe this is true of Precise as well but this point can be checked.)
[*]The section on ntfs-config needs to go, or be bracketed in a health warning. Also - a health warning about other GUI config software such as PySDM.
[*]The section on manual configuration of /etc/fstab needs a lot of attention. The suggested fstab line is not ideal and perhaps a short discussion on the pros and cons of some commonly used mount options would be useful.[/list] 

Well - just for starters. I'm sure there's a lot else that needs attention.

I'm happy to start work on this but I would appreciate help, even if just comments and suggestions, hence this thread. But first:

Does anyone know if there is already a better wiki page that covers this material? I haven't found one.

As always - this is just for discussion about this wiki page. Requests for support should be posted in support forums.

---

### Post by coffeecat on 2012-11-24
New sections "General Considerations" and "Using the File Manager" added and various health warnings added.

If anyone is unhappy about the wording of either of those two sections, please say so. Everything under the new (temporary) heading "Configuring /etc/fstab" is a bit of a presentational mess, apart from anything else, and I will work on this soon.

I have it in mind to suggest three different basic gets-you-going NTFS /etc/fstab lines for these common situations:

[list][*]Workable read-write - probably "defaults,windows_names,locale=en_US.utf8" mount options (with instructions how to find your locale to replace en_US.utf8 ).
[*]Mount read-only
[*]Hide NTFS partition so that it doesn't appear in file browser and is inaccessible.[/list]

And then refer readers to man pages or other resources such as this forum if they need help with other options. Otherwise it becomes an unwieldy fstab howto. Talking of which....

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

...hasn't been edited for 18 months. It probably needs looking at too. Any takers?

---

### Post by coffeecat on 2012-11-30
Rewrite mostly done but it still needs constructively critical feedback from others. I've still to add a link for disabling hybrid hibernate/shutdown in Windows 8. This one would do perhaps:

[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

Also - the section on FAT32 under manually configuring /etc/fstab could do with some improvement.

---

### Post by louibourque on 2014-02-10
Dear Madam, Sir,

First, I want to thank you for your efforts, especially this comprehensive page : MountingWindowsPartitions (dernière édition le 2013-12-14 11:21:34 par knome). I use Xubuntu to do extensive volunteer work in Urban Planning but do not know about logical systems and machine language. I sought this page to decide which filesystem (format) imprint on a virgin external HDD, for all possible considerations.

As a novice end-user, I found this page excellent for its unambiguity and sufficient, consistent, closing of topics opened (the read-only thread of the page being a good example). The contextual indications seems breif but not superfluous, logically flawless in their effective proceedings. I find important to note these (rare) inherent qualities of the page, to be perpetuated; Please let me first report my novice appreciation of the page; and secondly, add two element of content that could be included :

I find the summary (the titles of the page) included essential and relevant structural explanation helpful to understand behavioral and logical implication of filesystems, even when linked to LinuxFilesystemsExplained[/COLOR]» is provided.

I appreciate systematic incursion of Ubuntu's derivatives such as Xubuntu when necessary. 

Geo-logical indication, such as this one found in the «Using the File Manager » section, are clear and essential for end users : « (...) Simply look in the left pane of the file manager for the partition you wish to mount and click on it - it will be mounted and its contents will show up in the main pane. Partitions show with their labels if labelled, or their size if not». 

Likely, when indications for manual config is given (in Terminal representation), I truly appreciate when non-config (operational) directions are explicitely written along config ones like here : « Now open /etc/fstab in a text editor with root privileges. In Ubuntu: gksudo gedit /etc/fstab» : This also allows me to proceed without knowing the implications and manners of root privileges, commit in Urban Planning or learn syntax along the way.

Similarly, I appreciate the perfect distinction between what is examplary and what is mandatory in the command line indicated.

Of course, I appreciate the well advised panoptical look over the prodecure, which guides us through a linear and progressive path where eventualities, and casualities are foreseen and adressed in the right moment like : « Before editing /etc/fstab directly, it is a good idea to make a backup. From a terminal:» or «You will also need to change the &#8220;locale=en_US.utf8&#8221; option to one suitable for your location and language».

Secondly in terms of content, I think a small section devoted to the behavior or the creation of external partition (drives) could be included. It would relate, for instance, to the descriptive warning given about the hibernation's consequences, to prevent data loss when sharing the partition with Win7/8. I suppose Win7/8 recovers (re-write) pre-existing system (data) state on a device or not, depending on its mount point or status, internal or external.

Given the title of this page also think a few more consideration could be provided regarding the implications of mounting (and accessing) Window's Boot and Recovery partitions, especially when performing instalation and partitioning operation. This, maybe with a contextual link to pages addressing Linux startup issues, since MBR corruption and Grub issues seems to be common among users.


Hope this helps,
Thank you very much for your time and consideration!

---

### Post by aplatypus on 2018-10-02
Good morning,

Some feedback on this page, as I've just followed it to mount an NTFS partition on a new PC.


[LIST]
[*]Before using the `mount -a` command, I checked my fstab file with,
[LIST]
[*]`findmnt --verify` 
[*]as recommended by the mount man page. 
[/LIST]
  
[*]I used "ntfs" -- "ntfs-3g" failed. 
[*]Personally I don't edit system config files like /etc/fstab directly (*in situ*).
[LIST]
[*]I prefer to copy the origianal file to a work area and do my edits there first. 
[*]I make a back-up of that original. 
[*]Then edit the working copy 
[*]After checking, I copy the file back. 
[*]It may seem like a small thing, however I think some of these fundementals should be encouraged especailly with "fresh faces". 
[/LIST]
  
[/LIST]

In general I found the page very helpful.  Thank you for the efforts.

Kind regards  ... aplatypus

---

