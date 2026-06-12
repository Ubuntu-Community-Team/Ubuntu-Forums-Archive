---
title: "Apache2 PHP - user home directories problem"
date: 2005-03-01
forum: Desktop Environments
---

### Post by natefish on 2005-03-01
I am using Hoary, Apache2 and PHP4, all installed via synaptic. 

The root or default folder works fine and serves up the phpinfo file  without any problems. 

However the user folder (ie localhost/~user/phpinfo.php ) doesn't  work in faact it just ask if I would like to download the file. I checcked the usrdir modules and everyone tllosks fine. Any ideas what could be causing this?

---

### Post by hantsy on 2005-03-02
The test file  is in the  "public_html" dir in your user home??? And it (and home directory) can be read and executed for anyone???

---

### Post by natefish on 2005-03-02
Yes, permissions shouldn't be an issue but even after changing nothing has improved. I tried to reinstall everything (complete remove apache files, php files, phpmodule, etc, etc), then go back through and reinstall. 

Now the phpinfo file in the root directory no longer works, system asks for download. I checked the install, the module are enabled in apache, php is installed, settings look correct but still no php. Restarted the server, all that good stuff, by all accounts it should work. 

I tried making the changes directly in the apache.conf file though you shouldn't need to do that if the modules and such are set up correctly. Unfortunately it didn't make a  difference. I wonder if installing from source would fix this problem, or from the debian sources. 

The system worked via apache1.3 but on the last update it was replaced with apache2 and everything went to hell. 

It looks like I am the only person having this problem so must be something I screwed up but I don't know how considering I just used synaptic.

---

### Post by natefish on 2005-03-02
Yes, permissions shouldn't be an issue but even after changing nothing has improved. I tried to reinstall everything (complete remove apache files, php files, phpmodule, etc, etc), then go back through and reinstall. 

Now the phpinfo file in the root directory no longer works, system asks for download. I checked the install, the module are enabled in apache, php is installed, settings look correct but still no php. Restarted the server, all that good stuff, by all accounts it should work. 

I tried making the changes directly in the apache.conf file though you shouldn't need to do that if the modules and such are set up correctly. Unfortunately it didn't make a  difference. I wonder if installing from source would fix this problem, or from the debian sources. 

The system worked via apache1.3 but on the last update it was replaced with apache2 and everything went to hell. 

It looks like I am the only person having this problem so must be something I screwed up but I don't know how considering I just used synaptic.

---

### Post by natefish on 2005-03-02
I wonder if it has anything to do with the virtual servers / sites enabled functionality. Not sure how tht works, but the I have a sites-enabled and sites-available files, the sites-enabled has a 000-default item, could this create some problems?

---

### Post by natefish on 2005-03-02
Tried uninstall / reinstall with debian packages, nothing changed still doesn't serve the php files. I am going to need to dive into things in more depth, maybe try and install from source tonight if no one has any ideas.

---

### Post by natefish on 2005-03-02
I installed phpmyadmin to see if that would improve things, I did at least get an error that makes some sense...

"The requested url cgi-bin/php4/phpmyadmin/index.php was not found."

It looks like my configuration is for the cgi version of php not the module...at least thats what the above points too. 

Guess I will need to look for the details on how to change that.

---

### Post by natefish on 2005-03-02
Well removed and reinstalled again, but made sure to only use the packages associated with apache and the php module, no CGI or php4 etc. 

Still nothing works, so there is something screwy going on. Looks like tonight is an install from sources, bummer.

---

### Post by natefish on 2005-03-03
Well I got it working...what made it work? 

Well I uninstalled everything, removed any folder left behind. Then selected PHP4 package to install which automatically selected everything else. Then installed it all, restarted the server, still no php. So I reinstallled the libapache2 php4 mod multiple times restarting the server on the third try it worked. 

Weird but it works, for some reason, the system still prompts for download, when navigating to the folder and there is only a index.php file...for example
localhost/folder/... as compared to localhost/folder/index.php which does work. 

I checked the apache2.conf and the DirectoryIndex includes index.php and others so this shoudn't be happening but it does. Oh well maybe it will just start working in the future.

---

