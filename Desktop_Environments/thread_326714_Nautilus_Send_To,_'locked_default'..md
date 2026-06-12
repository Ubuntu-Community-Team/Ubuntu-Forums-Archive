---
title: "Nautilus Send To, 'locked default'."
date: 2006-12-28
forum: Desktop Environments
---

### Post by merlyn on 2006-12-28
Hi all,

I've recently begun experimenting with alternative apps to those installed by default, Ubuntu 6.10, and today I'm looking at email applications.

The reason that I'm doing this? It's not that I dislike the default apps, (in this case evolution), it's just that I like to have a look around, and see what's out there.

Also to consider situations where person x migrates from Windows to Linux and asks about 'equivalent' programs. In this case lets say that person x used Thunderbird in Windows and would like to continue using it in Ubuntu.

Getting on to my actual quandry.

I've just changed my mail client, migrated all my mail, & contacts, altered the preferred applications setting to suit, even the 'you beut' mail key works on my fandangle keyboard.

Now just to set up the send to . . . .

Wait a minute, I can't seem to change this!?! 

Perhaps if I remove the default application, I'll be able to change it then . . .[fires up synaptic and go to remove evolution. . . hmm nautilus-sendto is dependant on evolution]. . . bugger.

Thus my questions are,[INDENT][LIST=1]
[*]Can the default 'send to' mail client for nautilus be changed? (the only [thread]("http://www.ubuntuforums.org/showthread.php?t=23156&highlight=nautilus+%2B+send+to") I could find regarding this yielded no conclusive answer).
[*]Is this behaviour specific to Gnome in Ubuntu or Gnome in general.
[*]Should not a user be able to change their mail client and be able to access such functions?[/LIST][/INDENT]Cheers.

**Edit: **A follow up after investigating further.

I have searched both this forum, and the Gnome support forums regarding this and found the following information amongst what usually amounted to dead ends.

Gnome support forums thread: [this]("http://gnomesupport.org/forums/viewtopic.php?t=10225&highlight=nautilus+send") thread initiated over a year ago has some useful links including the [reported bug]("http://bugzilla.gnome.org/show_bug.cgi?id=318052") in Gnome bugzilla.

A fellow by the name of Igor Feghali has produce a package which will install a plugin library which has worked on Slackware 10.2 and Ubuntu 6.06. The package (tarball & deb), and instructions for compiling from source can be found [here]("http://www.interveritas.net/thunderbird/"). Unfortunately I lack the skills need to rewrite the make file needed to compile the current nautilus-sendto from source with Igor's library.

Igor has mentioned the fix on the Gnome bugzilla site, to the unitiated such as myself it seems as if this hasn't been actioned to date.

There is a really useful thread [here]("http://www.ubuntuforums.org/showthread.php?t=91377") on the Ubuntu forums that mentions a utility know as nautilus actions, which enables additional functions and scripts to be incorporated into Nautilus, including a means to enable a 'send to feature' for Thunderbird, and most likely any other 'unsupported' email application.

Nautlilus-actions 1.2 is in the Ubuntu repos (universe), or the latest can be got from the repos mentioned on [this]("http://asher256-repository.tuxfamily.org/index.php?page=packages&lang=en") site.

Cheers once again.

---

