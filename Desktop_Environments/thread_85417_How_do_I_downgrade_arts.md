---
title: "How do I downgrade arts?"
date: 2005-11-02
forum: Desktop Environments
---

### Post by berndtj on 2005-11-02
Hi,

I just installed KDE3.5beta2. Arts is now crashing at login, and apparently the fix is to downgrade to KDE3.5beta1.  Problem is I never upgraded to beta1, just straight to beta2.  How do I get the downgraded arts/libarts packages.  Adept, is not helping.

Yes, I am new to Linux.

Berndt

---

### Post by beefsprocket on 2005-11-02
You'll want to look at the wiki: I had the same problem.
[https://wiki.ubuntu.com/KubuntuKDE35BetaKnownProblems](https://wiki.ubuntu.com/KubuntuKDE35BetaKnownProblems)

---

### Post by Lambert on 2005-11-02
I'm not sitting at my kubuntu box right now so this is off memory.

Open up synaptic and go to the package you want to downgrade and highlight that line. At the top menu click on package, some where at the bottom of the list there's an option underneath lock package. Click on that and if there is a downstram package you can choose to downgrade. Go back and choose the lock package option so it doesn't upgrade.

I changed my repository list to the beta1 and downgraded both packages listed on the wiki to .91 version and my sound is working again.

---

### Post by berndtj on 2005-11-02
> Note that for users who upgraded directly to KDE3.5 Beta2 from a clean Breezy 3.4.3 installation, you'll have to install the beta1 arts and libarts packages to have working sound. Add the beta 1 repository, downgrade arts, libarts, then lock arts, and libarts (2 packages in the lib section I think) to the .91 version instead of .92. You can also just keep the default arts packages from the base installation.

I found the wiki earlier.  I'm just not sure how to do the above.

Thanks,

Berndt

---

### Post by beefsprocket on 2005-11-02
Hmmm, I'm the one who posted that bit. Perhaps once you get this resolved I'll edit it to make it clearer.

Using synaptic (or adept?) change the kde repository that you added to read:
[http://kubuntu.org/packages/kde35beta1/]("http://kubuntu.org/packages/kde35beta1/") (instead of kde35beta1)

Using nano edit the line to read:
deb [http://kubuntu.org/packages/kde35beta2/]("http://kubuntu.org/packages/kde35beta2/") breezy main (instead of kde35beta1)

Then you can follow the instructions given?

Once you've sucessfully got sound working again, you can change the line back to kde35beta2. Just make sure that you've locked the arts packages!

---

### Post by berndtj on 2005-11-02
Thanks,

l'll give it a shot when I get back.  Your first explanation was good, I think I was replying as you were writing.  Anyway, I think I should be able to get this going.

Berndt

---

