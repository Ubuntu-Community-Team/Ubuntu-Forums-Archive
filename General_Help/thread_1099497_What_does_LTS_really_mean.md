---
title: "What does LTS really mean?"
date: 2009-03-18
forum: General Help
---

### Post by Tux+ on 2009-03-18
In Ubuntu land does LTS mean the release ONLY gets software patches and fixes no new features during it's lifetime of support?

I'm more interested in knowing whether Canonical will / have released new kernel versions rather than just patches to the originally released kernel version 2.5.24 I believe in 8.04.

---

### Post by skymera on 2009-03-18
Long Term Support releases are meant for rock solid stability.
So no, no new features are added to keep this distribution stable.

Upgrade to the latest Ubuntu for new features.

Or try a different distro that has bleeding edge packages :)

@ Yes, new kernel versions are released periodically. This is to fix bugs etc.

---

### Post by Tux+ on 2009-03-18
> **skymera said:**
> Long Term Support releases are meant for rock solid stability.
So no, no new features are added to keep this distribution stable.

Upgrade to the latest Ubuntu for new features.

Or try a different distro that has bleeding edge packages :)

@ Yes, new kernel versions are released periodically. This is to fix bugs etc.

Thanks skymera for the quick reply. Is there a roadmap for when the new kernel is planned for i.e in Launchpad somewhere?

---

### Post by skymera on 2009-03-18
I haven't seen one.

They get released "as-and-when" they're needed really. :)

Jaunty runs the latest kernel 2.6.28

---

### Post by Thelasko on 2009-03-18
You can enable the "backports" repository to get some newer software for Hardy, but Hardy will never have all of the latest and greatest applications.

---

### Post by mb_webguy on 2009-03-18
You can also enable Launchpad PPAs or other third-party repositories to get the latest versions of specific software.

---

### Post by Tux+ on 2009-03-18
Thanks for the suggestion. I already had backports enabled but not PPA.

---

### Post by mcduck on 2009-03-18
> **Tux+ said:**
> In Ubuntu land does LTS mean the release ONLY gets software patches and fixes no new features during it's lifetime of support?

I'm more interested in knowing whether Canonical will / have released new kernel versions rather than just patches to the originally released kernel version 2.5.24 I believe in 8.04.

*None* of the Ubuntu releases get new features after release. All package versions are locked during the end of the development and updates are only provided to fix serious problems and for security reasons.

LTS versions simply have longer support time than normal releases, and they also tend to be a bit more focused on stability than normal releases are.

---

### Post by sdennie on 2009-03-18
To expand upon Mcducks post, 8.04 will always use the 2.6.24 kernel.  ALWAYS.  It will be patched and modified such that you can barely call it 2.6.24 but, that will always be the base of the kernel.  The same holds true for the rest of the packages on the system.  They are what they are.  They will not be upgraded, they will only be patched.

However, an LTS release is really nice in that you can have a 100% stable system and then manually upgrade the 10-15 packages you actually care about.  Your machine probably has 2000-3000 packages on it.  You only really care about 10-15.  Figure out how to upgrade those packages via PPAs, getdeb.net, source, etc.  You will have a stable system with up to date applications.

---

