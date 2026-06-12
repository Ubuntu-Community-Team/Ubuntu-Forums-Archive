---
title: "problem with synaptic"
date: 2005-03-27
forum: Desktop Environments
---

### Post by bailout on 2005-03-27
Just did a fresh install of ubuntu. Ran Synaptic to what upgrades were needed, first updated sources then select all updates. Result was about 250M of download needed. Didn't want to do all that at the time so I cancelled. There was some message that I needed read fully. When I went back later I repeated same, update source then select all upgrades but now it says my system is up to date and no updates needed.

Obviously synaptic thinks that the updates identified 1st time have been done and has marked all my packages as most recent versions when they are not. Is there any way I can force it to rescan my installed packages and id them correctly as old so I can then update them?

---

### Post by cdhotfire on 2005-03-27
[QUOTE=bailout]Just did a fresh install of ubuntu. Ran Synaptic to what upgrades were needed, first updated sources then select all updates. Result was about 250M of download needed. Didn't want to do all that at the time so I cancelled. There was some message that I needed read fully. When I went back later I repeated same, update source then select all upgrades but now it says my system is up to date and no updates needed.

Obviously synaptic thinks that the updates identified 1st time have been done and has marked all my packages as most recent versions when they are not. Is there any way I can force it to rescan my installed packages and id them correctly as old so I can then update them?[/QUOTE]

reload, then select Mark All Upgrades and choose Smart Upgrade.

---

### Post by bailout on 2005-03-27
[QUOTE=cdhotfire]reload, then select Mark All Upgrades and choose Smart Upgrade.[/QUOTE]

Tried this, doesn't work-that is the problem. The first time I did the first two steps but not apply upfrades and then exited. It seems that synaptic has marked the upgrades as having been done although I didn't apply. Now when I try again, reload/mark all, it says no upgrade needed and the list shows all my package versions matching the updated list (they obviously don't in reality as I didn't apply the original marked upgrades).

What I need is some way of forcing synaptic to rescan and correctly id the installed packages as being previous versions.

---

### Post by Glanz on 2005-03-27
I would check to see if you have those applications pinned...(under "locked versions") though I don't believe that is the problem if Synaptic truly marks non-upgraded packages as having been upped. The second thing I would verify is the "history" , also in the "file" drop-down menu to see what's up. Also check under settings> preferences> distribution  to see if "always choose the latest version" is checked. Then I would simply close synaptic, do an apt-get update in a terminal, followed by an "apt-get install synaptic" also in the terminal to make sure you have the latest version of Synaptic...

Good luck!

---

