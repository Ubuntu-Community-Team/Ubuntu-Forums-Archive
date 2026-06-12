---
title: "Updating to KDE 3.5"
date: 2005-12-20
forum: General Help
---

### Post by canadianwriterman on 2005-12-20
Not sure I did the right thing, but I wanted to upgrade my Kubuntu Breezy to KDE 3.5. So, I went to the instructions at:

[http://kubuntu.org/announcements/kde-35.php](http://kubuntu.org/announcements/kde-35.php)

It wasn't really clear what the update process is.  I assumed that I should add the deb line to my sources.list and then do an Adept update. The page did say that there were i386 and amd64 packages, but I wasn't given the option to select one or the other... the update just started happening. There were 87 packages. I didn't see that any of them originated from the URL in the repository URL that I put into my sources.list. Also, the updates stopped halfway through because a number of packages that were being downloaded were marked as "broken."

Did I do something wrong?

---

### Post by grinias on 2005-12-20
You did the right thing. I did the same using synaptic (and not adept) without problems. Maybe you should try

sudo apt-get update
sudo apt-get -f upgrade

in a konsole.

---

### Post by Adrian on 2005-12-20
[QUOTE=canadianwriterman]Not sure I did the right thing, but I wanted to upgrade my Kubuntu Breezy to KDE 3.5. So, I went to the instructions at:

[http://kubuntu.org/announcements/kde-35.php](http://kubuntu.org/announcements/kde-35.php)

It wasn't really clear what the update process is.  I assumed that I should add the deb line to my sources.list and then do an Adept update. The page did say that there were i386 and amd64 packages, but I wasn't given the option to select one or the other... the update just started happening. There were 87 packages. I didn't see that any of them originated from the URL in the repository URL that I put into my sources.list. Also, the updates stopped halfway through because a number of packages that were being downloaded were marked as "broken."

Did I do something wrong?[/QUOTE]

Actually I just did the same upgrade, and I also had problems with broken packages. This is what I did.

* Downloaded and installed Riddell's key
* Edited sourses.list
* apt-get update
* apt-get dist-upgrade
Now it made me aware of the fact that I had broken packages. So I loaded Synaptic, which told me that I had 11 broken packages. I selected "Fix broken packages" from the menu. Then I did a
* apt-get upgrade
and everything seems to be OK.

So, maybe Synaptic can take care of things for you?

---

