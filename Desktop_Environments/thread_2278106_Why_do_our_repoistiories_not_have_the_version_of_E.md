---
title: "Why do our repoistiories not have the version of Evolution that has bugs removed?"
date: 2015-05-14
forum: Desktop Environments
---

### Post by cigtoxdoc on 2015-05-14
I received the following post from [email]evolution-list@gnome.org[/email]. "and it had been surely fixed [1] in the stable version of evolution,
like the current 3.16.2."  Why is not Evolution 3.16.2 in the repositories for 14.04.2?  Please note that some of us use Ubuntu for our businesses.  It needs to "play nice" with e-mail (mostly from clients in the corporate world that use MS Outlook) we receive from our clients.  Even the version of Evolution (3.12.11) that comes with 15.04 is obsolete.

John

---

### Post by wildmanne39 on 2015-05-14
Because with every ubuntu in the development stage there is a cut of for getting in new updates and evolution must have missed the cut off.
You can add more repositories or ppa's to install the new evolution if one is available but be care that it is a trusted source.
[http://ubuntuguide.org/wiki/Ubuntu_Trusty_Packages_and_Repositories](http://ubuntuguide.org/wiki/Ubuntu_Trusty_Packages_and_Repositories)

I did not find evolutiion 3.16 with a search only 3.13.

---

### Post by buzzingrobot on 2015-05-14
> **Wild Man said:**
> Because with every ubuntu in the development stage there is a cut of for getting in new updates...

Ditto for every distribution released on a schedule.  

Evolution updates frequently. It's a complex application and a major component of Gnome.  Distributions that do not use Gnome, like Unity, rely on portions of it for calendaring and other functions.  Because it is not built as a standalone app , as Mozilla builds Firefox and Thunderbird, new versions can't be released as simple drop-in replacements.

---

### Post by dino99 on 2015-05-14
3.16.2 will probably land soon into wily archive, as gnome devs have released it a couple days back

---

### Post by Tadaen_Sylvermane on 2015-05-14
This is one of the primary reasons I'm using Kubuntu with Kontact instead of any Gnome based for my laptop. I much prefer Evolution. It seems strange to me that while versions do get frozen, that they would freeze an obviously buggy piece of software instead of updating it. Kind of puts a bad taste in my mouth for anything *buntu to be honest. Especially when they bill themselves as an enterprise level os, leaving a buggy mess as part of stable is mind boggling.

---

### Post by buzzingrobot on 2015-05-14
> **Tadaen_Sylvermane said:**
> This is one of the primary reasons I'm using Kubuntu with Kontact instead of any Gnome based for my laptop. I much prefer Evolution. It seems strange to me that while versions do get frozen, that they would freeze an obviously buggy piece of software instead of updating it. Kind of puts a bad taste in my mouth for anything *buntu to be honest. Especially when they bill themselves as an enterprise level os, leaving a buggy mess as part of stable is mind boggling.

It's not a matter of stubbornness or indifference.

No distribution that follows a fixed release schedule can do that kind of one-off updating, especially of complex tools like Evolution.

Changes in a new application release can include changes in support code relied on by other applications and other components. Before releasing that upgrade, then, someone must test how all the changes it makes impact other components. Those changes can drive other changes in other components, and so on and on...

Simply bumping up the version number of components can cause problems for package installers and dependency resolution.

Following through with that approach soon makes keeping to a fixed schedule impossible.

Rolling releases like Arch don't follow a fixed schedule, but many would argue they may often trade newness for reliability.

A few apps, like Firefox, are deliberately built and released as self-contained tools, contrary to Linux standards, and that allows distributions to quickly package and release each new version.

---

### Post by cigtoxdoc on 2015-05-14
Thank you for your replies.  The workaround is to upgrade to 15.04 and go to Fabien Tassin's webpage in launchpad and get version 3.16.0-fta1 for vivid.

john

---

