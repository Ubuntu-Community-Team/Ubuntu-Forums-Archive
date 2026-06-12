---
title: "Can i download the Ubuntu updates and install to another computer?"
date: 2009-01-18
forum: General Help
---

### Post by asaren on 2009-01-18
Hi

I want to update some important security updates for Ubuntu 8.10 in a no-internet-connection computer.

I know only way to update Ubuntu by Update Manager that need internet connection.

Where can i find the download update file like ones are showed in update manager? and save as files to move installing other computer.

Thank you

---

### Post by mssever on 2009-01-18
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Topsiho on 2009-01-18
I am not sure for I never used this. But I found the downloaded update files are stored in/var/cache/apt/archives, as .deb files, like this:

...
cvs_1%3a1.12.13-9_amd64.deb
dnsutils_1%3a9.4.2.dfsg.P2-2ubuntu0.1_amd64.deb
firefox-3.0_3.0.5+nobinonly-0ubuntu0.8.04.1_amd64.deb
firefox_3.0.5+nobinonly-0ubuntu0.8.04.1_all.deb
firefox-3.0-gnome-support_3.0.5+nobinonly-0ubuntu0.8.04.1_amd64.deb
firefox-gnome-support_3.0.5+nobinonly-0ubuntu0.8.04.1_all.deb
flashplugin-nonfree_9.0.152.0ubuntu1~hardy1_amd64.deb
g++-4.2_4.2.4-1ubuntu3_amd64.deb
...

You might copy the files that you find in this map that you downloaded from internet to your other computer while updating and do the update from there. I guess that trying to update, these files are found automatically.

If this is dangerous maybe someone who reads this might jump in :). But my guess is that apt-get will automatically use only those files that it needs. And moan about the files that it needs but doesn't find there, for no computer is the same <== there might be the snag.
But please be aware that you are my guinea pig :) and I hope you'll report back how it goes....

Topsiho

---

### Post by mssever on 2009-01-18
> **Topsiho said:**
> I am not sure for I never used this. But I found the downloaded update files are stored in/var/cache/apt/archives, as .deb files, like this:
That will also work. But you can't just dump them into /var/cache/apt/archives on the target machine, because apt won't be expecting them. You can, however, use gdebi or dpkg -i to install them manually (or double-click the icon if you're using Nautilus).

---

### Post by Topsiho on 2009-01-18
On second thought I think you would have to download all files first on your computer that is connected to internet, copy those to the other computer, and do the update from there.
And this every day, or week, or maybe month.
Which of course can be done but is not practical: 26000 or so files every time.

Or an intelligently selected subset of these files .... maybe this would make the thing more practical?

Using the link mssever mentioned.

Topsiho

---

### Post by mssever on 2009-01-18
You'd have to know which packages had been updated since last check. One way is if you have another Internet-connected Ubuntu machine. Another would be to look for a mailing list or something that posts such info. Presumably there exists at least such a list for security updates.

---

### Post by Topsiho on 2009-01-19
A solution is to have exactly the same packages on both computers.

Topsiho

---

### Post by Pidgin on 2009-01-19
I have noticed that Synaptic can generate download script. I don't know whether it helps.

---

