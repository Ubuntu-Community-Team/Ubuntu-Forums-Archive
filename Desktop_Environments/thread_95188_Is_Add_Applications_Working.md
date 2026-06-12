---
title: "Is Add Applications Working?"
date: 2005-11-25
forum: Desktop Environments
---

### Post by Georgie-o on 2005-11-25
I live the U.S. and was wondering if the ADD APPLICATIONS Program Respositories is working?  For the past 2 days no programs on the basic installation menu appear to be available.   Is this a universal problem?****

---

### Post by aysiu on 2005-11-25
You need to say what exactly is going wrong.
Have you tried updating from the terminal? If so, what errors appeared (don't describe the errors--post them exactly as they appear)?

Open up a terminal (Applications > Accessories > Terminal) and type this command in ```
sudo apt-get update
``` What happens? Copy and paste it into a post--all of it.

---

### Post by Georgie-o on 2005-11-25
Here it is:

Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Fetched 3B in 0s (3B/s)
Reading package lists... Done



Any thoughts?

---

### Post by aysiu on 2005-11-25
[QUOTE=Georgie-o]
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Any thoughts?[/QUOTE] Yeah, it sounds as if another process is using it. Do you have the update manager, Add Applications, Synaptic Package Manager, or Adept open right now? If so, close it, and try the command again.

---

### Post by Georgie-o on 2005-11-25
sorry, figured that out after the post.  Stopped it and edited the original post.

---

### Post by aysiu on 2005-11-25
In answer to your original question, the repositories seem to be working just fine.

---

### Post by Georgie-o on 2005-11-26
Most of the Applications in the GUI of "Add Applications" are 'greyed' out and say that they are unavailable for download and that I would have to go to the universe.  Why would that be?

Thanks for the assistance.

---

### Post by aysiu on 2005-11-26
[QUOTE=Georgie-o]Most of the Applications in the GUI of "Add Applications" are 'greyed' out and say that they are unavailable for download and that I would have to go to the universe.  Why would that be?

Thanks for the assistance.[/QUOTE] It means that you don't have Universe enabled. There are a basic set of Ubuntu repositories enabled. In order to install certain applications, you have enable more repositories. For more info on the whole installation she-bang, read:

[http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

For an easy way to get all available Ubuntu repositories, see the first link in my sig.

---

