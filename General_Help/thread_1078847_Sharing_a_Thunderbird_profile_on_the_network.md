---
title: "Sharing a Thunderbird profile on the network"
date: 2009-02-23
forum: General Help
---

### Post by DavidHB on 2009-02-23
I am Linux newbie, and have installed Ubuntu 8.10 (AMD x64), dual-booting with Windows XP Pro, on one of the three machines on my LAN; the others are running different flavours of Vista. The aim is to work the Ubuntu installation up to production machine standard, which is a statement as much about my capabilities as those of the system. So far, things have gone much more smoothly than on previous occasions I have tried to install Linux.

In the Windows environment, I use Thunderbird as the email client, with a single profile (physically located on one of the Vista PCs) shared between the 3 machines, though, obviously, only usable by one machine at a time. I should like to extend this arrangement to include the Ubuntu installation. I have tried searching in this forum and elsewhere, but have yet to find advice as to how to do this.

I can already access the network share where the profile is located via the 'Places' menu, and have installed Thunderbird on the Ubuntu system. Now (if previous experience with the Windows installations is anything to go by), all I need to do is edit the Ubuntu/Thunderbird profiles.ini file, so that Thunderbird accesses the pre-existing shared profile. This is where I am uncertain.

I have two questions, the answers to which I hope are obvious to non-newbies.
[LIST=1]
[*]How, exactly, do I reference the shared profile, that is how do I specify the path?
[*]Does the network share need to be explicitly mounted (e.g. by editing etc/fstab), or will the process of opening Thunderbird take care of this, as it does in Windows? If the share has to be explicitly mounted, how is it done?
[/LIST]
Thanks in advance for answers to these questions, and for any other advice you feel is relevant.

David

---

### Post by tad1073 on 2009-02-23
[http://ubuntuforums.org/showthread.php?t=1076549](http://ubuntuforums.org/showthread.php?t=1076549)

---

### Post by DavidHB on 2009-02-23
Thanks, tad1073, for that astonishingly prompt reply, and for the link, which I had seen. (Yes, I know I should have said so, but my post was already a bit long.)

I don't have a storage partition as such, but I assume that my network share can save the same purpose. The trouble is that the Profile Manager does not seem to provide me with any means of browsing to the network share. Am I missing something?

David

---

### Post by tad1073 on 2009-02-23
You could edit your fstab to auto mount your network drive. I don't really know how to do that personally but I am sure a search would turn something up.

[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=YnR&q=auto+mount+your+network+drive+linux&btnG=Search](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aunofficial&hs=YnR&q=auto+mount+your+network+drive+linux&btnG=Search)

---

### Post by DavidHB on 2009-02-24
> **tad1073 said:**
> You could edit your fstab to auto mount your network drive.As I said in my first post, I don't know whether this is needed. 

I am having difficulty in referencing the profile when the share is already mounted. Thunderbird is throwing up the "Thunderbird is already running ..." error message, which is a sure sign that it cannot see the profile.

David

---

### Post by DavidHB on 2009-02-24
In case it is relevant, here is the text of the profiles.ini file.

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=//wootton/documents/Mozilla/Thunderbird%20Profile/2q2m4lff.default
Default=1

Does the fact that this is giving an error message, even when the network share is mounted, suggest that the path may be correctly specified, but that there is a permissions issue? Any help would be appreciated.

David

---

### Post by tad1073 on 2009-02-24
I was having the same problem and when I deleted my profile and recreated it, it worked fine.

---

