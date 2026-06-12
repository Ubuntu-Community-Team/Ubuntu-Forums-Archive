---
title: "Creating symlink for Adobe AIR - for TweetDeck"
date: 2009-05-04
forum: General Help
---

### Post by Fleshtone on 2009-05-04
I've been trying to install TweetDeck.  Their website has a Flash link to download the installer.  When clicked, there appears a phrase like "download starting...", but nothing happens.

I'm using Firefox w/ flashplayer.  I even installed AIR separately hoping that would work.

I was told to "manually symlink the installer: from /opt/Adobe AIR/Versions/1.0/Adobe AIR Application Installer to /usr/bin"

After looking into the syntax of symlink and trying work out how to deal with Adobe's bulky space-ridden directory and file names (it's like they're screwing with linux users), it occurs to me that this action seems unrelated to the problem of getting the download button on the website to work.  I got that feeling I get when I'm about to accidentally brick my machine, so I stopped.

Is a symlink a solution to this?  If so, how would it be done?

---

### Post by dwayne.hale on 2009-06-17
your right it is a problem with the website and flash in general. Flash has never ran in linux on par with the way it runs in Windows or OSX. Try the link again but wait awhile when I downloaded it took me about 10 minutes before their server made the call back with the download. As for the symlinks thats usually for people who have already installed tweetdeck but are getting undesirable results.

---

### Post by Fleshtone on 2009-06-17
As is usual with my novice approach to fixing Ubuntu problems, I tried so many different things that I'm not sure exactly which thing actually fixed the problem.  I've probably made a messy web of symlinks and duplicate folders that would make people cringe, the same way I cringe when I see some people's (my mom's for example) Windows machines.

Thanks for the affirmation that the Tweetdeck site was being funky, which is more than I could get from Tweetdeck themselves on twitter.

As for the one (or more) unnecessary symlinks I've created, could I just delete them, or is there more to it than that if I wanted to clean up?

---

