---
title: "Issues with updating to KDE 3.5.2"
date: 2006-03-31
forum: Desktop Environments
---

### Post by irichardson03 on 2006-03-31
I've been looking for a post with someone having the same issue and maybe a resolution, but I was unable to find one.

So here's the scoop:

I followed the instructions on [http://kubuntu.org/announcements/kde-352.php](http://kubuntu.org/announcements/kde-352.php) to hopefully update to 3.5.2, but adept and apt-get is holding back those package upgrades.  What is the reason for this?

Thanks,
Ian

---

### Post by gingermark on 2006-04-05
I think this might happen if there are some dependency issues (not 100% sure though).

Did you try an apt-get upgrade or an apt-get dist-upgrade?

You might want to post the contents of /etc/apt/sources.list to get more help.

---

### Post by RavenOfOdin on 2006-04-05
[QUOTE=irichardson03]I've been looking for a post with someone having the same issue and maybe a resolution, but I was unable to find one.

So here's the scoop:

I followed the instructions on [http://kubuntu.org/announcements/kde-352.php](http://kubuntu.org/announcements/kde-352.php) to hopefully update to 3.5.2, but adept and apt-get is holding back those package upgrades.  What is the reason for this?

Thanks,
Ian[/QUOTE]

I had trouble downloading it too. I put the mirror from kubuntu.org into my /etc/apt/sources.list file and it returns the message "No such file or directory" when I try a dist-upgrade.

Oh well, I'll try again later.

---

