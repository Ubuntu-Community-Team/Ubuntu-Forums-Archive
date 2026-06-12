---
title: "Update manager no longer shows versions of currently installed packages"
date: 2008-05-31
forum: Desktop Environments
---

### Post by sexcopter on 2008-05-31
Hi there,
This isn't a really big issue, but I recall when I used Gutsy and updates came through update-manager, it would list the updates available, along with the currently installed version and the new version available. It's nice to know, and seems to have disappeared in Hardy. I can't see any relevant setting in gconf-editor for it.

I'm a missing something? Does anyone miss this feature?


Thanks,
James.

---

### Post by 16777216 on 2008-05-31
I miss it too.

---

### Post by jimv on 2008-05-31
THe update manager only shows up when updates are available.  Check to make sure that it's enabled by going to System > Preferences > Sessions and make sure that Update Notifier is checked.  If you don't see it, you can install it with

sudo apt-get install update-manager

---

### Post by Xiong Chiamiov on 2008-05-31
> **jimv said:**
> THe update manager only shows up when updates are available.  Check to make sure that it's enabled by going to System > Preferences > Sessions and make sure that Update Notifier is checked.  If you don't see it, you can install it with

sudo apt-get install update-manager
That's not what he was asking about.  He misses the fact that when the update manager launches, it doesn't show the installed and candidate versions.

---

### Post by jimv on 2008-05-31
Mah mistake.  I read too fast.

---

### Post by Cherry Cotton on 2008-06-10
I've been bugged by this, too. It's especially a problem if the package has no changelog, or if it has an outdated changelog. I wish there were a Gconf option for it, or something...

Any ideas?

---

### Post by Bubba64 on 2008-06-10
I don't know if this is any help but synaptic has a history that shows installs including ones from update manager.

---

### Post by sexcopter on 2008-06-10
> **Bubba64 said:**
> I don't know if this is any help but synaptic has a history that shows installs including ones from update manager.

That's exactly the information they have removed. If I'm desperate to know about version numbers, I can look there, but it just seems like a real step backwards to have removed this information from update-manager.

I just had a browse of the changelog for update-manager, and noticed that it was removed in version 1:0.87, as seen [here]("http://changelogs.ubuntu.com/changelogs/pool/main/u/update-manager/update-manager_0.87/changelog").
I'm at work now, so can't check out what the changelog comment is talking about ("details tab"?) I'll have a look when I get home.

So, who/how do we voice our views on this matter such that maintainers hear us? Launchpad? Bugzilla?

Cheers,
James.

---

### Post by Cherry Cotton on 2008-06-11
It's possible that the "details tab" thing is referring to the changelog... but of course, that works only if the package has a changelog, and then it still does not say what version you are upgrading _from_ (plus, the changelog can be outdated or inaccurate). Or, maybe they meant to put a details tab in and forgot? Maybe the update manager has a details tab on other distros? I don't know.

---

### Post by sexcopter on 2008-06-11
> **Cherry Cotton said:**
> It's possible that the "details tab" thing is referring to the changelog... 

I think you're right, I don't see anything else it could be.

> but of course, that works only if the package has a changelog, and then it still does not say what version you are upgrading _from_ (plus, the changelog can be outdated or inaccurate). Or, maybe they meant to put a details tab in and forgot? Maybe the update manager has a details tab on other distros? I don't know.

I think we're thinking along the same lines. It bugs me that nowhere does it mention the currently installed version for comparison with the newly available version... In particular, it'd be nice to know what is actually being fixed/changed when I hit "Install Updates".

James.

---

### Post by Cherry Cotton on 2008-06-12
> **sexcopter said:**
> I think we're thinking along the same lines. It bugs me that nowhere does it mention the currently installed version for comparison with the newly available version... In particular, it'd be nice to know what is actually being fixed/changed when I hit "Install Updates".

I think it would also be nice to see what repository an update is coming from... I mean, I vet third-party repositories before adding them, but I think I'd like to apply a little extra scrutiny if, say, a repository that I like for its cool wallpapers suddenly wants to update libc6.

Yeah, we need to find the bugtracker for this program....

---

