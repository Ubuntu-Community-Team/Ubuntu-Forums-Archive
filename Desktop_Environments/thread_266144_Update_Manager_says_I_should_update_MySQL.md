---
title: "Update Manager says I should update MySQL"
date: 2006-09-26
forum: Desktop Environments
---

### Post by anroy on 2006-09-26
My Update Manager shows two updates for MySQL.  They are:
[LIST]
[*]libmysqlclient15off
[*]mysql-common
[/LIST]
Here is the screenshot.
[[IMG]http://img97.imageshack.us/img97/6238/updateszm6.th.jpg[/IMG]](http://img97.imageshack.us/my.php?image=updateszm6.jpg)

However this does not make sense.  I installed MySQL myself from source.  I did not use the Add/Remove Applications feature, or Synaptic Package Manager.  How is it even aware that I have MySQL on my machine?

Also, these updates are indicated to be version 5.0.22.  The MySQL installation on my machine is version 5.0.24.  It may well be harmful to my MySQL installation if I, through carelessness or ignorance, applied these updates.

Is this a bug in the Update Manager?  Is there anything I can do about it?

I often get notice of various updates, and I do apply them.  I just do not put a checkmark beside these two.  But having to be careful like this is becoming a pain.

What is worse is the feeling that I cannot trust that Update Manager.  I have no way of knowing if the updates being offered will be harmful or not.  In the case of MySQL I just happened to be knowledgeable but I know absolutely nothing about the vast majority of the packages that normally show up in that update list.

---

### Post by amohanty on 2006-09-27
I wouldnt worry about those. The mysql-common is required if you installed libmysqlclient. And lots of apps depend on libmysqlclient, so I am guessing it gets installed by default. 

To check out the 'dependants' of libmysqlclient, fire up System->Administration->Synaptic
Then search of libmysqlclient
In Settings->Preferences->General check the checkbox that says 'Show properties in main window' (its the first one).
Then click on libmysqlclientoff
in the bottom window, select Dependencies and then use the drop down to look at dependants.

The update-manager _does_ _not_ know about your mysql install. Moreover if you installed the source version in a non-default location ie /usr/local/ (as you should all installed-from-source packages - for easier management) you will be fine, however if you installed in /usr, well the chances of an overwrite is real. You can just ignore these two packages then.

HTH
AM

---

### Post by anroy on 2006-10-17
> **amohanty said:**
> I wouldnt worry about those. The mysql-common is required if you installed libmysqlclient. And lots of apps depend on libmysqlclient, so I am guessing it gets installed by default. 

To check out the 'dependants' of libmysqlclient, fire up System->Administration->Synaptic
Then search of libmysqlclient
In Settings->Preferences->General check the checkbox that says 'Show properties in main window' (its the first one).
Then click on libmysqlclientoff
in the bottom window, select Dependencies and then use the drop down to look at dependants.

The update-manager _does_ _not_ know about your mysql install. Moreover if you installed the source version in a non-default location ie /usr/local/ (as you should all installed-from-source packages - for easier management) you will be fine, however if you installed in /usr, well the chances of an overwrite is real. You can just ignore these two packages then.

HTH
AM
Thanks amohanty.

I checked as you instructed, and there is a long list of dependants.  Is that a list only of dependants that are installed on my machine, or of all possible known dependants?

Yes, like you said anything I install by myself from source (which is just MySQL, Apache and PHP) I always put in /usr/local/.

So should I install those updates, then?  They are annoying and never go away.  However I really need to be sure they won't screw up anything.

I have no confidence in my knowledge of Ubuntu or Unix or Linux.  But I am highly confident at installing MySQL from source.  So I guess if something stops working I can install it again.  

Are there situations where things can get so screwed up that even my installing it again won't fix it?

---

