---
title: "Wrath Help?"
date: 2010-08-16
forum: Gaming &amp; Leisure
---

### Post by Target Ninja on 2010-08-16
Hi! Sorry to bother you guys, I'm Target Ninja and I was hoping you guys could help a beginner like me with a tiny problem I have with Blizzard's World of Warcraft: Wrath of the Lich King. My roommate who has better knowledge than me(<-Complete n00b) with linux seems to be dumbfounded. The current message that I get after I fully download the program is: "Launcher requires write permission to the World of Warcraft Directory to successfully patch the game. Please enable write access to the directory using an administrator account."

Can anyone help me?

---

### Post by ed-koala on 2010-08-16
There have been patches to the Blizzard launcher in the past that have broken WoW.  One of those was a patch that made all of the permissions change in your WoW folder, making you unable to run the game.  This seems to be where you are at the moment.

To fix, do 2 things.  First, go to /.wine/drive_c/Program Files (you'll have to show hidden files to find .wine), right click on the World of Warcraft folder, go to the permissions tab, and change the owner to yourself and change permissions to create and delete files ... also click the Apply Permissions to Enclosed Files button.

Next, upgrade to wine 1.2 or later, and upgrade WoW.  This problem goes away after updating.  You may have to do this multiple times during the update process to get to the fixed version, but I no longer have the problem with up to date wine and WoW.

Hope this fixes things!  It should, I no longer have the issue as I once did.

---

