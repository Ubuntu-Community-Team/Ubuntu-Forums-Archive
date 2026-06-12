---
title: "Wierd Log Off/Shutdown Button Issue"
date: 2007-12-26
forum: Dell  Ubuntu Support
---

### Post by MrSootentai on 2007-12-26
For some reason my 'Quit' button has now become more of a 'Just Log Out' button.
Can anybody help? I even made sure that under login window settings that show actions menu is enabled.

---

### Post by chewearn on 2007-12-27
Check this:

Gnome Top Panel Menu > System > Preferences > Power Management > General Tab
Actions
When the power button is pressed


EDIT:
Opps, I read you post wrongly, sorry.

---

### Post by wormser on 2007-12-27
I found the answer [here]("http://ubuntuforums.org/showpost.php?p=3935124&postcount=21")!  The solution:

> System-> Administration-> Login window-> Local(tab)

Checked the show actions check box. And it works.

I believe this is the problem you are talking about.

---

### Post by MrSootentai on 2007-12-27
Thank you for the replies!
I just found out it was a setting under UbuntuTweak that I unchecked.
Now my Suspend and Hibernate options show up, but my only my suspend works properly.

---

