---
title: "Preformed upgrade with manager - now OO is GONE and I cannot reinstall"
date: 2010-05-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by irenaios on 2010-05-06
I am using Ubuntu Hardy via the Dell Mini.

Quite awhile ago I upgraded my OO to the newest lpia version I could find...I cannot recall, but I did it "manually" by adding the launchpad repository etc.

Yesterday I noticed that my update manager was flashing at me and telling me I had updates and so I let it update. Seems to me I got some sort of error message during the updating, but I was multi-tasking and stupidly just clicked OK....Afterwards I noticed that my Open Office would not work...in fact it was almost as if it was uninstalled. It was nowhere to be found.

So, I thought maybe my update got messed up and I ran it again with update manager - no changes.

Okay...reinstall OO. I first tired "Add/Remove" and I got an error as soon as I clicked on the box next to the suite: "This application conflicts with other installed software...conflicting software must be removed...switch to Synaptic"

Okay...fine

When I check for install the "openoffice.org suite" I get this:

"Could not mark all packages for installation or upgrade. The following packages have unresolvable dependencies. Make sure all required repositories are added and enabled in the preferences"

And then

"openoffice.org:

Depends: openoffice.org-base but it is not going to be installed
Depends: openoffice.org-calc but it is not going to be installed
Depends: openoffice.org-core but it is not going to be installed

etc"

I then tried to check each of these individually and I just continue to get more of the same type of errors with different dependency errors.

Seems that no matter what I do I cannot get Open Office back :(

I posted this in a different forum category and realized it really was the wrong one...did get some help, but problem remains.

Jame

---

### Post by irenaios on 2010-05-06
Following the Instructions offered to Tony Land here:
[http://www.rebelzero.com/ubuntu/ppa-for-openofficeorg-301-for-hardyintrepid/94](http://www.rebelzero.com/ubuntu/ppa-for-openofficeorg-301-for-hardyintrepid/94)

I was able to revert back to 2.4 (I think I was using 3.0)

Whew.

Still don't know what happened, but it sounds like the same thing that happened to Tony.

---

