---
title: "Github - Tortoise =&gt; GIT with UI"
date: 2010-11-30
forum: Desktop Environments
---

### Post by jacksmith on 2010-11-30
Hi, 
I try to connect to github with ubuntu and it's difficult.
With command line, clone is allright.

Yet, I would like to get a UI to make some transfert and so on.

I'm looking for something very simple like "tortoise SVN" on Windows.

I've try qgit but I've not been really able to use it.
I've read on the net some comments on KDESVN [http://kdesvn.alwins-world.de/](http://kdesvn.alwins-world.de/) .
Yet, I use gnome and when using KDESVN, my computer (ubuntu) answer "unable to open a session ra_local"...

Does somebody know how to use github with a UI ?

Thanks in advance for your answers.

Jack

---

### Post by jacksmith on 2010-12-01
So, it seems not easy to find a software like tortoise git for ubuntu or linux.
The main adresses I've find which should be usefull are : 

I've read a lot of informations around (list here for the main informations)
[http://doc.ubuntu-fr.org/subversion](http://doc.ubuntu-fr.org/subversion)
[http://doc.ubuntu-fr.org/rapidsvn](http://doc.ubuntu-fr.org/rapidsvn)
[http://www.rapidsvn.org/index.php/Documentation](http://www.rapidsvn.org/index.php/Documentation)
[http://scenari-platform.org/trac/scenari/wiki/subversion](http://scenari-platform.org/trac/scenari/wiki/subversion)
[http://www.krishnashasankar.com/2008/11/tortoise-svn-in-linux-ubuntu-alternatives-here/](http://www.krishnashasankar.com/2008/11/tortoise-svn-in-linux-ubuntu-alternatives-here/)
[http://code.google.com/p/pagavcs/](http://code.google.com/p/pagavcs/)
[http://forum.ubuntu-fr.org/viewtopic.php?id=144033&p=2](http://forum.ubuntu-fr.org/viewtopic.php?id=144033&p=2)
[http://www.jasonfield.com/freebies/](http://www.jasonfield.com/freebies/)
[http://marius.scurtescu.com/2005/08/24/nautilus_scripts_for_subversion](http://marius.scurtescu.com/2005/08/24/nautilus_scripts_for_subversion)
[http://rabbitvcs.org/](http://rabbitvcs.org/)
[http://wiki.rabbitvcs.org/wiki/install/ubuntu#karmic-and-lucid](http://wiki.rabbitvcs.org/wiki/install/ubuntu#karmic-and-lucid)
[http://htmlcoderhelper.com/is-there-a-linux-ubuntu-svn-client-that-doesnt-suck/](http://htmlcoderhelper.com/is-there-a-linux-ubuntu-svn-client-that-doesnt-suck/)
[http://www.harecoded.com/nautilus-subversion-integration-tool-execute-svn-commands-with-gnome-scripts-96355](http://www.harecoded.com/nautilus-subversion-integration-tool-execute-svn-commands-with-gnome-scripts-96355)
[http://www.clickoffline.com/2008/12/ubuntu-alternatives-for-tortoise-svn-in-linux/](http://www.clickoffline.com/2008/12/ubuntu-alternatives-for-tortoise-svn-in-linux/)
[http://doc.ubuntu-fr.org/eclipse](http://doc.ubuntu-fr.org/eclipse)

And of course, for newbies like me on github, don't forget to differenciate svn and git repositories. 

Then I've try to install
sudo add-apt-repository ppa:rabbitvcs/ppa
sudo apt-get install rapidsvn
sudo apt-get install nautilus-script-collection-svn

But nothing seems really very easy to use... and particularly on git repository.

So, the only way I've find is to install tortoise on windows virtual machine.
That will be the first program I'll use under windows since I completely use linux for 2 years :-((((((((((((((((

I understand it's not THE solution but it's A solution... A "pity" solution...

Yet, on installing tortoisegit under windows XP in my virtual machine, I had some other problems (that I've finally solve after a long time of research...): 

Download TortoiseGit-1.5.8.0-32bit.msi from [http://code.google.com/p/tortoisegit/downloads/list](http://code.google.com/p/tortoisegit/downloads/list)

After that, I've download msysGit-netinstall-1.7.3.1-preview20101002.exe from [http://msysgit.googlecode.com/files/msysGit-netinstall-1.7.3.1-preview20101002.exe](http://msysgit.googlecode.com/files/msysGit-netinstall-1.7.3.1-preview20101002.exe)
=> But if you do that, you'll have some problems 
- it'll tel you that a dll is missing C:\msysgit\mingw\bin\libiconv2.dll
- and after, "ToirtoiseGit Git have not installed"

=> The solution I've find is to download [http://msysgit.googlecode.com/files/Git-1.7.0.2-preview20100309.exe](http://msysgit.googlecode.com/files/Git-1.7.0.2-preview20100309.exe)
Following a thread which explain the problem : [http://groups.google.com/group/tortoisegit-users/browse_thread/thread/ff1d81f59cd5fe90](http://groups.google.com/group/tortoisegit-users/browse_thread/thread/ff1d81f59cd5fe90)
... Good luck !

---

