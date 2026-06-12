---
title: "Error Occured"
date: 2007-12-13
forum: Desktop Environments
---

### Post by Gmonster on 2007-12-13
Hi,

Hi Please help!  I'm unable to install any new software and I'm also unable to use the Update Manager.  I've written as much detail as possible and posted screen shots of the error message here:

[http://docs.google.com/Doc?id=dfn2xdf3_6hjbdg3gt](http://docs.google.com/Doc?id=dfn2xdf3_6hjbdg3gt)

I couldn't figure-out how to include the jpeg screen shots in the post, so I uploaded them to the web at that address.  I've also wrote exactly what I did just BEFORE the error message started.

Please advise, as I'm stuck...

Thanks!

---

### Post by ajgreeny on 2007-12-13
I suspect the problem is because you didn't install the package for 7.10 with synaptic.  If you look closely you will see that the page you linked to is for 7.04 so the version of googleearth may well be different, and also your **/etc/apt/sources.list** file may be causing problems.  I am assuming that you copied the medibuntu commands shown in the link and ran them, which would work, but they will have added the wrong repos to your **sources.list** file, or to the **/etc/apt/sources.list.d/medibuntu.list **file.

Have a look at the last file mentioned and I think it should say something like this
## Medibuntu - Ubuntu 7.10 "feisty fox"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free

You should therefore edit or delete these entries as root, having backed up first, so ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
sudo cp /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.bak
```Then ```
sudo gedit /etc/apt/sources.list
```and edit out any lines refering to feisty fox.  Now do the same for the /etc/apt/sources.list.d/medibuntu.list file to edit out the feisty fox lines.

Now go to [www.medibuntu.org]("http://www.medibuntu.org") and make sure you enable the repos for gutsy gibbon this time not feisty fox.  You now will need to remove completely the googleearth that is causing the problem so in terminal try ```
sudo apt-get --purge remove googleearth googleearth-data
```  That should get rid of them.
Now try again to install googleearth with the new repos enabled not the old feisty fox ones and you may have more luck.

---

### Post by Gmonster on 2007-12-13
Hi, thanks for the response.  I followed your directions and still get the same error.  It's preventing me from access the Update Manager and the Synaptic Package Manager, which means I can't keep up with the upgrades.  Google Earth is also still there, with the same issue.  (Details can be found at: [http://docs.google.com/View?docid=dfn2xdf3_6hjbdg3gt](http://docs.google.com/View?docid=dfn2xdf3_6hjbdg3gt)

Not sure what to do from here.

The error says:

"AN ERROR OCCURED, the following details are provided: E: dpkg was interrupted, you must mannually correct the problem.  E:_cache->open()failed, please report."

How do I correct this problem?

---

