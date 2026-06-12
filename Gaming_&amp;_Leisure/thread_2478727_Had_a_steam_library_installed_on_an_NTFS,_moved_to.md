---
title: "Had a steam library installed on an NTFS, moved to ext4, still not working right."
date: 2022-09-03
forum: Gaming &amp; Leisure
---

### Post by rc-brooks on 2022-09-03
I haven't been able to run any games with Proton. It begins to start but then fails. I believe this has to do with it originally having been installed on an NTFS partition. SOME games will run if I use 5.0 proton, but most will not.

Here is the log [https://github.com/farmall1125/farmall1125/blob/main/pressure-vessel.log](https://github.com/farmall1125/farmall1125/blob/main/pressure-vessel.log)

It seems to be a permissions issue. I have uninstalled steam, purged and manually removed any files I can find, I had a separate library on an ntfs folder originally and believe something is still left over somewhere. Does anyone have an idea? Everything is on an ext4 folder now. Any help is greatly appreciated.

---

### Post by TheFu on 2022-09-03
NTFS doesn't support Unix permissions.
Also, NTFS files aren't case-sensitive, so if any of the filenames aren't exactly correct for what the program expects in upper/lower case, those will fail to be seen.

I don't game. Those things just jumped out to me as likely issues.

In short, don't use non-native file systems like NTFS or any of the FAT-crap, unless the storage will be physically connected to a non-Unix OS.

Fixing permissions on thousands of files manually just doesn't make sense.  It will be whack-a-mole for days, perhaps weeks.  You could perform a new install, capture all the filenames and permissions, then script a method to create all of those back in your copied-from-NTFS area.  I don't think that would be a trivial script, but I could be wrong.  Perhaps if it was sorted, then the names any permissions would line up so all the differences could be easily seen?  IDK.

---

### Post by rc-brooks on 2022-09-03
Everything was deleted. I uninstalled steam, all the games, purged, cleaned, searched, removed anything with steam. I see other people having these issues. Most go unresolved. Some using chroot to resolve. But yes, after I learned about the issues with the NTFS drives, I uninstalled everything. Done it three times now. I can't see anything that seems to be sticking around. Definitely has helped me get a bit more familiar with ubuntu to be certain.

---

### Post by TheFu on 2022-09-03
Not that it helps, but don't get too hung up on Ubuntu.  Linux is Linux is Linux. The different distros are mostly about the packages included by default and the default GUI.  The GUI in all Unix-like systems isn't anything special. It is just another program.

Always start searching for answers using "ubuntu {release} {error line}", where
the "release" is 20.04 or 22.04 or whatever supported version you run.  Always run LTS and supported releases.
the "error line" is what gets displayed on a terminal or in the system logs.

If nothing good shows up, remove ubuntu, then the {release}.  Often, the Arch forums/wiki will have more hands on commands. As long as they aren't saying to use the Arch package manager, the instructions 90% apply to other releases.

Normally, you'll want to only get instructions from websites that have "ubuntu" somewhere in the domainname. I haven't seen any of those providing bad or dangerous advice.  Beware of old instructions.  If an article doesn't have a date on it or doesn't specifically list which releases the instructions apply, be very careful.  They are usually click-bait.  
Also, never copy/paste commands directly from a website into a terminal.  It is easy to hide characters in HTML, but still have them included in copied text.  Copy the text and paste it into an empty editor first.  Look over each command and look up each option in the manpages installed on your system BEFORE running.  It is possible to setup a reverse remote shell by tricking people into the copy/paste method. That remote shell can pull nasty payloads and provide someone with a webpage anywhere access into your system.

You probably know all this.  Might be news for lurkers.

---

