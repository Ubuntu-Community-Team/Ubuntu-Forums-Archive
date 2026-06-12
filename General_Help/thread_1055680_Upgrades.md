---
title: "Upgrades"
date: 2009-01-31
forum: General Help
---

### Post by RedSingularity on 2009-01-31
Where can i get third party update addresses?  I want ubuntu to automatically look for updates on things such as firefox and OpenOffice.  I know i can go into ||System>Administration>Software Sources|| and then click the Third party software tab.  But where can i find other links to add to this tab?

---

### Post by mb_webguy on 2009-01-31
[Launchpad]("https://launchpad.net/") PPAs are mini-repositories created and maintained by individuals or groups not necessarily directly affiliated with Ubuntu.  Once you add a PPA to your software sources, you can install software from that PPA just like you would from the official repositories.

Launchpad has recently added PGP keys to it's PPAs, so you'll need to add those keys in the Authentication tab of Software Sources.  Because this is a relatively new addition, there's no one-click way to add these keys yet.  On the PPA page, there will be a long alphanumeric link to the key.  Click on that, then right-click on the keyID link and save it to your computer.  On the Authentication tab of Software Sources, click the Add button and locate the file you just downloaded to add the key.

---

### Post by Slim Odds on 2009-01-31
I think that you are confused about the way that Ubuntu organizes it's repositories.

You will automatically get security updates and bug fix updates from the "standard" repositories. There is no need for "third party" repositories for these.

However, each release has an established baseline. So, for example, if you're using 8.04, you'll get updates to OpenOffice 2.4. But you won't get OpenOffice 3.0. For that you'd need 9.04.

---

