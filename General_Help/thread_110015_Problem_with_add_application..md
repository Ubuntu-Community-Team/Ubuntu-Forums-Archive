---
title: "Problem with add application."
date: 2005-12-29
forum: General Help
---

### Post by raha on 2005-12-29
Hello

I am kind of new with Ubuntu and generaly Linux.
I think Ubuntu is really cool, specially on a widescreen Monitor :)

Problem: When I stat add application from Applications menu, some of the programs are bold and some other ones are lighter. When I click on the lighter one the text box next to it says that this program is currently not installable it sould be available in universe section repository. how can I solve this problem ?
I should mention that I did go to settings and then Repositories, but I didnt know what I should do :(
Is it something wrong with server or is it me who cant fix it ?

Thank you

---

### Post by Zelut on 2005-12-29
what the message is telling you is that the program is available but not from the default database where the programs are stored.  Its from one of the additional or optional databases that need to be added to your list.

As it mentioned you need to activate the additional databases (repositories) in order to install that program.  Did it not give you a simple 'yes/no' option for including those?  If not try this:

System > Administration > Synaptic Package Manager
Settings > Repositories > Add: check - universe & multiverse.

After you do that try the Add Applications again.

---

### Post by raha on 2005-12-30
Thank you dude.
I tried it but this message came up, I think there is something wrong with server. I am not sure:
------------------------------------------------------------
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://gb.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)
----------------------------------------------------
What do you think now ?

---

