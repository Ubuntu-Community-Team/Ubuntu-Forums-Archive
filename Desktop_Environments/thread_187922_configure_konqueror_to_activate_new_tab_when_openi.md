---
title: "configure konqueror to activate new tab when opening another folder?"
date: 2006-06-03
forum: Desktop Environments
---

### Post by jetpeach on 2006-06-03
Here's my goal - when I have konqueror open, but minimized, when I click a folder on the desktop, a new tab in konqueror shows the folder and konqueror is brought to the foreground.

Sounds simple, eh?

I love KDE more than Gnome but I've found configuring this seemingly simply option impossible.  First, the easy part that works fine is configuring Konq to load new windows in tabs: in Konq->Settings->Configure Konqueror->Web Behavior Tab->under tabbed browsing clicked "Open links in new tab instead of in new window".  Nope, that didn't do it, a new window is still loading.  So Then I go to advanced options directly under these options, checked "Open as tab in existing Konqueror when URL is called externally."  I also made sure in these advanced options that "Open new tabs in the background" was unchecked.  That fixed so new opened folders load in a new tab, but they're loading in the background.  And here's the tough part - is it even possible to configure this somewhere in the Konq settings to force new tabs to be activated?  In particular, those when opening new windows?

I've tried disabling all focus prevention, but this doesn't seem to be the problem - I believe the window isn't even asking for focus right now when it loads the tab.

Anyway, I began looking at the command KDE uses to load the folders, it's currently "kfmclient openURL %u inode/directory".  It looks like there used to be a foreground tab for some other similar kfmclient type commands, but I couldn't find any option in the man pages for kfmclient currently.

Maybe all this is silly and I'm just ](*,)  but the desired behavior described seems like something that many people would like - I.E. it just makes sense that, if you like tabs, when you click a folder on the desktop it should load in a new tab and the window it loaded in should be restored/made visible.

Thanks for any help ya'll can give!

---

### Post by ihavenoideax2 on 2006-06-27
Hi, i think this is my first post. Ive been using this forum for kubuntu since ive started using it about 2 years ago. Well i would like to setup the same thing. When i was using Breezy it opened in a new tab and i really liked that after awhile. So if theres anyway to set that up on Dapper. Thanks

---

### Post by jetpeach on 2006-06-27
woohoo! i'm not alone anymore!  i still don't have a solution, maybe now that this is bumpbed up we'll see somebody chime in...

---

