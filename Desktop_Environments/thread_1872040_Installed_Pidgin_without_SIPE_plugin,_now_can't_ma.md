---
title: "Installed Pidgin without SIPE plugin, now can't make plugin work"
date: 2011-10-29
forum: Desktop Environments
---

### Post by Cidman on 2011-10-29
I am in GNOME on 10.04.03 LTS.  I had made this work previously before I wiped and reinstalled the system.  I am needing to connect to my company's Lync server using Pidgin because it now has a SIPE plugin to connect to a Lync server and be able to text chat (no other functionality).  On the previous installation I did:

sudo apt-get install pidgin pidgin-sipe 

(per this article: [http://itswapshop.com/content/add-lyncoffice-communicator-account-pidginubuntu](http://itswapshop.com/content/add-lyncoffice-communicator-account-pidginubuntu)).

That worked right away straight out of the box.

On this new installation I did:

sudo apt-get install pidgin

and then brought it up and tried my account without thinking of choosing Office Communicator, which wasn't there anyway and failed because I had forgot the SIPE plugin install.

After that, I could NEVER get the option Office Communicator under account management.  I have all the other options like AIM, AOL, SIMPLE, etc.

I tried uninstalling and reinstalling Pidgin and the plugin SIPE both from Add/Remove Software and the command line, with a reboot.....no dice.  I cannot get the option of Office Communicator as stated in the above article.  I was thinking I might need to physically delete directories created by the first install, but have no clue what directories to check.

Has anyone ever dealt with something like this in Ubuntu?  Thanks!

Cidman

---

### Post by ingramproductions on 2013-01-24
I know this is old, but in case anyone comes across this, the pidgin-sipe package from the repositories is outdated. I recommend installing the the sipe plugin from source. It's easy to do and they provide instructions here on how to do it:
[http://sipe.sourceforge.net/install/]("http://sipe.sourceforge.net/install/")
Installing from source may fix your problem. But I'm not sure why it didn't show up in the list of protocols, as your original question stated.

---

