---
title: "All entries not showing up in repos"
date: 2009-05-27
forum: General Help
---

### Post by 10Digits on 2009-05-27
Hi, there everybody,

Could you please help out??? Entries like nodoka,industrial,aurora are missing from my repos.I am using Ubuntu studio 8.10.Is it because of my partitions??Because I think I have created logical partitions.Is this causing the problems???

Also, after connecting to the internet ( connecting was a breeze!!!) I have updated my repos via synaptic and checked then but still no entries are to be found.....:( When I try to install software like Gnome-Do..I find to my surprise that it is of an older version and I have add launchpad to my software sources to get the latest version.....

Am I missing something???

Thanks well in advance!!!!!!!!!!!

---

### Post by drs305 on 2009-05-27
The logical partitions do not matter, so don't worry about that.

I don't use Studio but I did a search and two of the three packages you mentioned are in the *universe* repository if you are looking for theme engines. Do you have *universe* enabled? Nodoka is listed as g2k-engines-nodoka. If you aren't sure of the name you can enter a partial name (such as "nodoka") in the top "Quick Search" window in synaptic

Open Software Sources or Synaptic. Settings, Repositories, Ubuntu Software tab. Enable the *universe* repo if it isn't already enabled, then "Reload" from the main Synaptic menu.

The package versions are frozen once the distro is finalized so you often won't find the latest releases in the official repositories. Ubuntu is not what is called a "rolling release", meaning that updated versions of an app are not normally added to the repositories. This is done for stability purposes.

---

### Post by 10Digits on 2009-05-27
Phew, that's a relief so the logical partitions are not a problem.

Hmm.Well it seems that the universe repo along with all the others like multiverse, restricted are enabled by default , coz this is a fresh install and it is only 20 mins since i have posted after installing on my laptop.
Okay, I have gone software sources thru my synaptic....

I have even let it choose my server according to it.....

unticked all of them except multiverse and reloaded .....each time marking only one option and finding TONS of downloads.......

But I kept my patience AND IT WORKED............nodoka,industrial is AVAILABLE......

THANK YOU >>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>:)


PS: sorry for the long post but I was doing all this while I was writing this reply so, please keep with me.

---

