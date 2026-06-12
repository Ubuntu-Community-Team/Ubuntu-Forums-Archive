---
title: "Latitude 2100 package header &amp; wireless problem ..."
date: 2010-11-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Dave Cooper on 2010-11-02
My Dell Latitude 2100 Ubuntu 9.0.4. netbook connected once to the Internet via my wireless router. I made that connexion at the same time as I configured my Acer Aspire One Windows XP Home netbook to connect to the Internet via the same wireless router. Both netbooks configured using the same WEP key.

Now only the Windows device connects. The Dell tries to connect but continuously presents the Wireless Network Authentication Required dialog which prompts me to click Cancel or Connect. Clicking Connect does not result in a connexion to the Internet and eventually the dialog is presented again.

An error message displays when I click on the red alert icon that displays next to the battery icon. This is what the error message says:

[FONT=Courier New]An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error: Opening the cache (E: Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages, E: The package lists or status file could not be parsed or opened.)' This usually means that your installed packaged have unmet dependencies.[/FONT]

Reports of similar error messages on the Web suggest actions like this:

[FONT=Courier New]sudo rm /var/lib/apt/lists/* -vf[/FONT]

Would this really be a fix? Or less drastically, can I just remove the package list file that is specifically mentioned in the above error message ([FONT=Courier New][FONT=Verdana]*/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_jaunty-updates_restricted_binary-i386_Packages*[/FONT])[/FONT] rather than **all **the contents of this *./lists* directory?

Any help, suggestions and advice would be greatly appreciated.

Thanks ...

Dave

---

### Post by mörgæs on 2010-11-03
9.04 is unsupported and hence a security threat. Rather than trying to fix it I would go for a clean install of 10.04 or 10.10.

[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

---

