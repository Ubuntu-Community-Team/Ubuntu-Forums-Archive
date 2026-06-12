---
title: "Turn off executable text file dialog?"
date: 2006-07-13
forum: Desktop Environments
---

### Post by vayu on 2006-07-13
Whenever I double click on a text file I get a dialog that asks if I want to display it or run it.  Is there a way I can get this to default to display without the dialog coming up and then either lose the run capability or even better make a right click option that lets me run it?

---

### Post by etank on 2006-07-13
It is probably doing that because the file is executable. Go to Places->Home Folder. Click on Edit->Preferences. Select the Behavior tab and there you can make the change that you want.

---

### Post by vayu on 2006-07-14
> **etank said:**
> It is probably doing that because the file is executable. Go to Places->Home Folder. Click on Edit->Preferences. Select the Behavior tab and there you can make the change that you want.

Thank you!

---

### Post by OzzyFrank on 2008-03-21
But what about .txt files that aren't executable? I'm getting this for every text file not on my Ubuntu partition (or Home folder anyway), and even for those I've copied across to my user folder. Since I've seen a lot of "then it MUST be an executable file", I'll stress that these are standard text files.

I'd rather not turn off the notification because then EVERY text file after that would be treated as a standard text file. So I suppose the question is **how to disable this only for .txt files**. I've seen a lot of talk that Ubuntu scans the innards of files so knows what they actually are, but in my experience, once I turn off that notification for .txt files, then it is applied to .sh scripts (which I then have to right-click and make executable, which is a drag). Cheers

---

