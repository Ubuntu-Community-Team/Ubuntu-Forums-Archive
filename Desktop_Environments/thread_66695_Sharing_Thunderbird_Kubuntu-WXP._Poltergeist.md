---
title: "Sharing Thunderbird Kubuntu-WXP. Poltergeist?"
date: 2005-09-18
forum: Desktop Environments
---

### Post by ryke on 2005-09-18
Hi,

I need to share e-mail in Kubuntu and WXP, and it seems that solution is to use TB.
I've made the following (thanx to Aaron Burda):
On windows copy the following directory to a shared FAT32 partition
C:\documents and settings\<user name>\application data\thunderbird\profiles\<jxljq4q7.default>    <- the last directory will vary but will be something similar
then in both windows and linux you need to edit your profiles.ini file for thunderbird.  For linux this is in your home directory in a hidden directory called .mozilla-thunderbird, for windows it is in your users application data\thunderbird folder.  In the file set the IsRelative variable to 0 and then for Path= set it to the path to your files
for me under linux it is Path=/dos/thunderbird/aburda/jxlq4q7.default
windows Path=G:\thunderbirds\aburda\jxl....

It works ok, but  I have a problem:
- In Linux. I receive some mails, I erase some of them and file another in different folders that the "inbox" one.
- Go to Windows. I open tb and some the erased and moved mails are in their corresponding but remain in the inbox folder too (so, I have 2 copies of the same mail)
- Come back to Linux. the same that in Windows

So, it's very nasty to move and erase the same mails several times.

Moreover, this thing not always happens... maybe for a couple of days everything is ok, but i.e. third day I have the problem again.

I think that problem just involves Windows, not Linux.
For example... TB in Linux: I have 5 e-mails in the inbox folder, all of them marked as read.
I make a new and clear (deleting manually all folders relating to TB) installation of TB in Windows. Afterthat I copy the Linux's user folder to Windows, modifying the Windows' profiles.ini. When I open TB in Windows, in inbox folder there are more of 5 e-mails, and some of them marked as unread. It's very strange. It seems that Windows doesn't recognize, partially, the last moved e-mails made under Linux (because mails appear in the new folders, but are not deleted of the inbox folder).

Any idea about how to do? Thanx in advance ;-)

---

