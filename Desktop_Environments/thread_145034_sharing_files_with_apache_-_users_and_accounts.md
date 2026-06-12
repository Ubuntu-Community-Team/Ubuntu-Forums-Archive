---
title: "sharing files with apache - users and accounts"
date: 2006-03-15
forum: Desktop Environments
---

### Post by stiankarlsen on 2006-03-15
Hey, I was wondering if there was some alternative to [this]("http://www.snapfiles.com/get/easyfilesharingserver.html"), in linux.

I need to be able to host files on my apache server, and it would be nice if there was some site/prog i could use that would give me access to create users with passwords and so forth.. Anything on that front for linux?

---

### Post by benvdh on 2006-03-22
Hey,

There a a few options to choose from. Both require PHP on your server though. The also requires a MySQL database.

First of all you could have a look at quixplorer which is a very simple webbased filemanager that allows user logins with different permissions and root folders. The only drawback is that it is no longer being maintained:
[URL="http://quixplorer.sf.net"]
http://quixplorer.sf.net[/URL]

The second option is to install joomla (a content management system) which has a component you could use for this. Here are some links:

Joomla: [http://www.joomla.org]("http://www.joomla.org")

Remository Ext (the component): [http://www.joomlart.com/addons/components_and_modules/remository_ext_3.04.html]("http://www.joomlart.com/addons/components_and_modules/remository_ext_3.04.html")

Download Remository from their downloads (first click download tab) section. Before that register on their site (registration is free)

Joomla documentation:

[http://help.joomla.org/]("http://help.joomla.org/")

Regards,

Ben

---

### Post by stiankarlsen on 2006-03-23
Thanks, QuiXplorer seems to work fine, just one problem.

When I share a link to some folder that is not placed above my home dir, I get this error when I try to open it.

arc/260a : The current directory may not be above the home directory.

This explains itself, but what I was wondering, is it possible to share files/folders not above the home dir? (I have to harddrives mounted, and I want to share them both)

---

### Post by benvdh on 2006-03-24
Hey, 

I believe it was possible to access files above the quixplorer home folder. You could change the home folder in the .htaccess file or .htuser file I believe. Haven't used this app for a while. And if you would like to share files that are outside your webroot you could try using symlinks. I'm not sure how quixplorer will respond to that since I haven't tried but maybe it could work. You can create a symlink like this:

1. Open a commandline
2. type the following command:

ln -s /media/hda2 /var/www/hda2_link

in this example /media/hda2 is the partition that should be available under your webroot and hda2_link is the name of the folder that is linked to the /media/hda2 folder.

Hope this works for you,

Regards,

Ben

ps. will be trying this myself shortly. I will post my findings here.

---

### Post by benvdh on 2006-03-24
> Hey, 

I believe it was possible to access files above the quixplorer home folder. You could change the home folder in the .htaccess file or .htuser file I believe. Haven't used this app for a while. And if you would like to share files that are outside your webroot you could try using symlinks. I'm not sure how quixplorer will respond to that since I haven't tried but maybe it could work. You can create a symlink like this:

1. Open a commandline
2. type the following command:

ln -s /media/hda2 /var/www/hda2_link

in this example /media/hda2 is the partition that should be available under your webroot and hda2_link is the name of the folder that is linked to the /media/hda2 folder.

Hope this works for you,

Regards,

Ben

UPDATE : Have just tried symlinking and quixplorer doesn't like it. So you'll have to set direct paths to those folders. If you set your admin home dir as / it should be possible to access your complete file system though.

Just did a little search on google and found the following project: PHPfileNavigator. It seems to have a lot more options then quixplorer and is still being maintained:

[http://pfn.sourceforge.net/index.php?opc=1&lg=ing](http://pfn.sourceforge.net/index.php?opc=1&lg=ing)

Apart from that it also looks great :P

---

### Post by stiankarlsen on 2006-03-25
Thanks a lot man, really appreciate you taking the time.

I'll be sure to try PHPfileNavigator as soon as I can, (getting home in a little under two days)

Thanks again, Stian.

---

