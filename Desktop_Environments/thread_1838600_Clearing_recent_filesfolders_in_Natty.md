---
title: "Clearing recent files/folders in Natty?"
date: 2011-09-04
forum: Desktop Environments
---

### Post by cybrsaylr on 2011-09-04
How do you delete the recent files and folders used?

When I click on 'Files & Folders' on the left column launchpad bottom, Search Files & Folders pops up and 'Recent' is the top first line that shows up showing everything recent used. Now there are over 30 recent files/folders listed that were recently used. I can't figure out how to delete them. Can someone tell me how they can be deleted and removed?

---

### Post by raja.genupula on 2011-09-04
[https://help.ubuntu.com/community/QuickTips](https://help.ubuntu.com/community/QuickTips)

---

### Post by stinkeye on 2011-09-04
See here to manage Zeitgeist logging.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=10893302&postcount=3[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=10893302&postcount=3")

---

### Post by cybrsaylr on 2011-09-04
> **raja.genupula said:**
> [https://help.ubuntu.com/community/QuickTips](https://help.ubuntu.com/community/QuickTips)

This does not exist in my 64 bit Natty version:

> Disable

First, go to Places -> Recent Documents -> Clear list. 

Here's a screenashot:


When I click on Files & Folders where the arrow is: Recent files & folders pop up with no way I can find to delete them. The when clicking on 'All Files' > Images: all recent image files show for today, yesterday, last week, last 6 months! I want to know how to delete all those files, clearing that list. 


Haven't tried disabling this feature in Terminal yet until I find out how to delete everything first.

---

### Post by stinkeye on 2011-09-04
See my previous post.
It's a Zeitgeist feature which was included in Natty.
You can turn off the logging if you like.

---

### Post by cybrsaylr on 2011-09-04
> **stinkeye said:**
> See my previous post.
It's a Zeitgeist feature which was included in Natty.

Wow!

Was hoping there was an easiler way to do this already inside Natty.

Reading through your link makes it look kinda tricky.....

---

### Post by stinkeye on 2011-09-04
> **cybrsaylr said:**
> Wow!

Was hoping there was an easiler way to do this already inside Natty.

Reading through your link makes it look kinda tricky.....
Nah easy.
Just follow the steps to add the Zeitgeist PPA.
Update your packages.
Install Activity Log Manager.

---

### Post by cybrsaylr on 2011-09-04
> **stinkeye said:**
> Nah easy.
Just follow the steps to add the Zeitgeist PPA.
Update your packages.
Install Activity Log Manager.

OK. Figured it out.......I think.
Did all the above.

When clicking on 'Activity Log Manager', after finding it in Natty, nothing happens. It won't open.

Synaptic show this version is installed:
activity-log-manager
blacklist configuration user interface for Zeitgeist
0.8.0-0ubuntu1~ppa2~natty

Now what?

---

### Post by cybrsaylr on 2011-09-04
Tried removing and reinstalling Activity Log Manager a couple times and still it will not open or respond when clicking on it.

---

### Post by cybrsaylr on 2011-09-04
GOT IT!

Found what I messed up on.

Forgot to do this:
> Once added upgrade Zeitgeist via the Update Manager, log out and back in to restart Zeitgeist. The proceed to install ‘Activity-log-manager’ via the Software Centre.

Just updated Zeitgeist via the Update Manager and it opens right up. Now Just have to play around with it to learn it.



PS: Zeitgeist Activity Log Manager works pretty good removing recent activity but only goes back 1 week. Natty shows files & folders going back 6 months. Is there a way to remove these older files & folders also?

---

### Post by stinkeye on 2011-09-04
> **cybrsaylr said:**
> PS: Zeitgeist Activity Log Manager works pretty good removing recent activity but only goes back 1 week. Natty shows files & folders going back 6 months. Is there a way to remove these older files & folders also?
Just below that you can choose a date **from** and **to**.

---

### Post by cybrsaylr on 2011-09-04
> **stinkeye said:**
> Just below that you can choose a date **from** and **to**.

Tried that and it worked OK going back 1 month from today. Trying to go back further it stalled and stopped responding.

However installing and using Activity Journal 0.6.0 (A viewport into the past powered by Zeitgeist) it allowed me to go back as far as needed to delete any files/folder desired.

Zeitgeist Activity Journal 0.6.0, gives you a nice view of everything done in the past.



Thanks for all the help stinkeye...):P

---

