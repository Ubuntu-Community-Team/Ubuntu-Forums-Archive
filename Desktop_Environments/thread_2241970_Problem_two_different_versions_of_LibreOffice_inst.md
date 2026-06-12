---
title: "Problem: two different versions of LibreOffice installed on same computer"
date: 2014-08-29
forum: Desktop Environments
---

### Post by williepabon on 2014-08-29
Hi!
I installed the latest (bleeding edge) version of LibreOffice from the LibreOffice repository (ppa:libreoffice/ppa) but forgot to remove the version that is installed by default with the OS(12.04). Now, I have different kinds of errors and conflicts between the packages (didn't include the details, sorry). It's messed up. Is there a way to remove everything and start all over? I mean, remove LibreOffice and then, re-install it using the Ubuntu maintained repository. Please, advise how to do this. Thanks.

---

### Post by kansasnoob on 2014-08-29
Is this the PPA:

[https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa)

If so the process for reverting is right there at the bottom of the instructions.

> To return to the LibreOffice version from the main archive, use ppa-purge. see: [http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html](http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html) for details

---

### Post by deadflowr on 2014-08-29
I think something else is the problem.
When using the ppa, you don't have to uninstall the original version.
It will simply install new packages, upgrade existing ones, and remove those packages which are no longer needed.
(Like any other update)
What commands did you run when you upgraded the packages?
(or tried to run to upgrade the packages)

---

### Post by williepabon on 2014-08-30
[B]@kansasnoob:
[/B]
When I do:
```
sudo add-apt-repository ppa:libreoffice/ppa
``` , I guess the additional repository added to the Software Sources is: [http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu)
There's another one that says instead libreoffice-4-0. So, it's not the one you are referring to.

[B]@deadflwr:
[/B]
Thanks for answering. My problems started when I did:
```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get dist-upgrade
```

While the final command was running, I saw in the terminal errors and conflicts, and when it finished, I got on the screen top panel a red negative sign that when clicked says that an error occurred. The message essentially says that the installed packages have unmet dependencies. If there's a way to resolve this without doing a clean installation of LibreOffice, it will be really appreciated. If not, please advise how to perform the clean install.
wp

---

### Post by deadflowr on 2014-08-30
Have you done anything yet?

If you have not tried to remove anything yet, then try the ppa-purge method first.
Kansasnoob posted a good link in the quote box on how to use it.
[http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html](http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html)
It should remove all the ppa packages and revert the old packages to it's original state, before the ppa snafu.

---

### Post by williepabon on 2014-08-30
> **deadflowr said:**
> Have you done anything yet?If you have not tried to remove anything yet, then try the ppa-purge method first.Kansasnoob posted a good link in the quote box on how to use it.[http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html](http://www.webupd8.org/2009/12/remove-ppa-repositories-via-command.html)It should remove all the ppa packages and revert the old packages to it's original state, before the ppa snafu.Thanks for answering. Ran the command you suggested above and everything went OK except at the end. This is a fraction of the code:```
Disabling libreoffice PPA from /etc/apt/sources.list.d/libreoffice-ppa-precise.listRunning apt-get updateReading package lists... DoneBuilding dependency tree       Reading state information... DoneE: Release 'precise' for 'libboost-date-time1.54.0' was not foundE: Release 'precise' for 'libcmis-0.4-4' was not foundE: Release 'precise' for 'libglew1.10' was not foundE: Release 'precise' for 'libgraphite2-3' was not foundE: Release 'precise' for 'libreoffice-style-sifr' was not foundE: Release 'precise' for 'librevenge-0.0-0' was not found/usr/bin/ppa-purge: 142: /usr/bin/ppa-purge: aptitude: not foundWarning:  Something went wrong, packages may not have been revertedwilliepabon@william-VirtualBox:~$
```Well, at least the negative sign on the top bar disappeared. So I guess, now there are no dependency problems. I'm going to reboot to double check. Thanks.

---

### Post by williepabon on 2014-08-31
Hi!:
Just to inform that running the ppa-purge utility seems to have solved my problem. Thanks for your help.

---

