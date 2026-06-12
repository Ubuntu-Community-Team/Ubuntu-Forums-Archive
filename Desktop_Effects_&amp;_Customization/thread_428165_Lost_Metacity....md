---
title: "Lost Metacity..."
date: 2007-04-30
forum: Desktop Effects &amp; Customization
---

### Post by Muppeteer on 2007-04-30
When i booted into Feisty today, i got a system message saying that there was a problem with the gnome daemon and that it would try to be restarted next time i log in. I looked in Beryl and surely i didn't have any option for compiz or metacity under the window managers...So i restarted and the same thing is happening...

Anybody know what could be causing this? The last thing i installed was Transmission (Torrent), i'm not sure that could be anything to do with it but i did install an update for kiba dock...

Oh and i just noticed i've lost emerald theme manager and Beryl settings...I'm using Beryl 2.1...Would it be best to just reinstall Beryl? Would this be safe without a window manager to fall back on? :confused:

---

### Post by blackened on 2007-04-30
Personally I would reinstall Metacity first as it tends to be much more stable than Beryl. I haven't had much luck, as far as stability, with Feisty (even without Beryl).

---

### Post by Muppeteer on 2007-04-30
Would i just do that through synaptic?

I've been quite lucky i think, everything has been working pretty well...Until today that is :)

---

### Post by blackened on 2007-04-30
Yeah, synaptic or apt.

---

### Post by Muppeteer on 2007-04-30
Ok i've tried reinstalling metacity and removing Beryl and reinstalling it but i still don't get any other window managers or the emerald/beryl settings....

Any other suggestions? :(

---

### Post by gashcr on 2007-04-30
Have you tried the command: metacity --replace once you have it installed??

---

### Post by Muppeteer on 2007-04-30
Yeah that worked...Seems to be just Beryl being the problem, surprise surprise...

Anybody got any idea what it could be?

---

### Post by Muppeteer on 2007-04-30
Ok this is driving me crazy now...

I restarted only to find i didn't have the ubuntu sign on the main menu (applications) and i couldn't select any dropdowns in firefox, nothing was rendering...

I tried removing kiba dock and Beryl, and all references to beryl. Everytime i reinstall Beryl i still only get Beryl as a choice for a window manager and no options for beryl. I haven't even updated beryl lately, why would it be acting so strange?

Ok after reading other posts, there seems to have been an upgrade to 0.3. Mine was at 0.3 and i tried downrgrading to 0.2.1 and 0.2.0 with the same results. I've removed everything to do with beryl! I don't get this...I think emerald must be screwed up or something...I tried removing the beryl repositories from my sources.list and install fresh from the ubuntu repos and it still installed 0.3.0...

Anybody know a solution for this?

---

### Post by Muppeteer on 2007-05-01
Bump :(

---

### Post by blackened on 2007-05-01
Honestly I don't have a solution, only sympathy. I had so many problems with Beryl under Feisty (well, Feisty in general) that I wound up doing a clean install back to Edgy. It's been nothing but rock solid ever since.

Not that I'm suggesting that as a solution, but you clearly have more patience than I.

---

### Post by Muppeteer on 2007-05-01
Thanks...I'm considering downgrading but it's such a pain in the a**...I tried asking on the Beryl forums too and didn't get any replies. I guess it's pretty rare if the people who make it can't even diagnose it :( 

So much for the 'helpful' linux community (not including you Blackened :)

---

### Post by rolf-c on 2007-05-01
This is the second thread today I've seen mention beryl 3.0 or 0.3, neither of which I can find reference to at [http://www.beryl-project.org/](http://www.beryl-project.org/).  Where did you find that release?

---

### Post by Muppeteer on 2007-05-01
It's in the Beryl repos and the feisty repos too apparently...

---

### Post by blackened on 2007-05-02
I wouldn't really put blame on the community in general. Moreso on the way forum-based support works. If the people "in the know" don't see your message, then, chances are, it won't get answered. Now that's not really their fault, but the fault of the forum structure. Especially in the case of very large, high-traffic forums like this one and that of Beryl. An unavoidable evil I'm afraid. The only way to solve this would be to use some sort of user tracking: record which users answer questions of certain topics. That way when they search for questions to answer, then they would be directed toward their areas of strength.

Those are my thoughts at least.

---

### Post by kabads on 2007-05-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/106350](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/106350) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The bug has been reported to the metacity maintainers and should be upstream soon. 

[http://bugzilla.gnome.org/show_bug.cgi?id=433253](http://bugzilla.gnome.org/show_bug.cgi?id=433253)

---

### Post by Muppeteer on 2007-05-02
Cool thanks, they've released an update for that...

I still have the Beryl problem though. Still missing the options on right clicking beryl manager and still getting high cpu usage. I noticed also, when Beryl is sucking up my usage so is GDM...

Well i removed 3.0 and i'm trying the version from the ubuntu repos, but in synaptic it shows beryl and beryl core as dsfg git also libberylsettings and decoration...all the other packages are showing as Ubuntu. Could this be a problem? if so, how do i fix it? This is straight from the ubuntu repos..

---

