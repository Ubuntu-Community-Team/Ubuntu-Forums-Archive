---
title: "disable thunderbird session tab restore"
date: 2019-08-21
forum: Desktop Environments
---

### Post by holiday on 2019-08-21
Just started using Thunderbird and want to stop the application from opening all the tabs I had opened when I last quit. 

Web searches take me to info on how to do this for Firefox but I don't see any info for Thunderbird.

---

### Post by walts48 on 2019-08-22
Have you tried selecting the Mail tab, right click on it and use "Close Other Tabs" from the context menu before quitting Thunderbird?

---

### Post by holiday on 2019-08-22
> **walts48 said:**
> Have you tried selecting the Mail tab, right click on it and use "Close Other Tabs" from the context menu before quitting Thunderbird?

I would rather not have to do that. I never want to restore tabs from previous session. It is unnecessary busyness to have to explicitly close them. Has it always been this way or is the tab a new feature?  I

Perhaps there is some way of automatically closing all tabs on quit. Some plugin. An event handling API perhaps. 

Or perhaps there is another mail client. In trying to get away from the gmail web application,  I've tried geary, mailspring, sylpheed... 

Any others?

---

### Post by walts48 on 2019-08-23
Have you searched [https://addons.thunderbird.net/en-US/thunderbird/](https://addons.thunderbird.net/en-US/thunderbird/) for an extension?

If you can't find an extension, search [https://bugzilla.mozilla.org/home](https://bugzilla.mozilla.org/home) to see if a bug has been filed for what you are requesting. If not file one for the Thunderbird product and Toolbars and Tabs component.

EDIT: 

SeaMonkey's Mail and Newsgroups window closes all tabs on quitting. There is a warning popup which you can disable so you won't have the "unnecessary busyness" of clicking "Close All Tabs" each time you quit the application. SeaMonkey can be configured to only open the Mail and Newsgroups window upon starting.

If interested use this link for the 64-bit version. [http://www.seamonkey-project.org/releases/#contrib](http://www.seamonkey-project.org/releases/#contrib)

---

### Post by walts48 on 2019-08-24
Well, I prefer to do it the easy way and don't normally view emails in a tab, but when I do I use "Close Other Tabs" from my Calendar tab, because I don't want to have any unnecessary busyness of having to go to Events and Tasks to open the Calendar tab.

Out of curiosity and to be helpful I did a search on ATN and found a "Don'tRestoreTabs" extension that will work for the current 60.* versions.

[https://addons.thunderbird.net/en-US/thunderbird/addon/dontrestoretabs/](https://addons.thunderbird.net/en-US/thunderbird/addon/dontrestoretabs/)

I installed it and it works. Unfortunately now I have to do some unnecessary busyness of opening that Calendar tab, the Quick Filter bar and Chat tab if connected to Chat.

Enjoy! I'm off to remove it now.

---

