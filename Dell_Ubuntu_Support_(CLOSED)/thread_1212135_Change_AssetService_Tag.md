---
title: "Change Asset/Service Tag"
date: 2009-07-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by 4-PackDad on 2009-07-13
Hey;

I inherited an old Dell...

It's 4 years old, but faster than my 12 yr old clone/mut.

How do I change the Asset/Property/Service tag's

Found these commands on another site,
but
they do not work.:?

% sudo nvram asset_tag=YOUR_ASSET_TAG 


    $ ./propertyTag
    Existing Property Tag:
    $ ./propertyTagS -s "New property ownership tag."
    Existing Property Ownership Tag:
    Changing Property Ownership Tag: New property ownership tag.
    Change Successful. The changes may not take effect until reboot, depending on
    system type.


    $ ./serviceTag
    Existing Service Tag:
    $ ./serviceTagS -s foobar1
    Existing Service Tag:
    Changing Service Tag: foobar1
    Change Successful. The changes may not take effect until reboot, depending on
    system type.


    $ ./assetTag
    Existing Asset Tag:
    $ ./assetTagS -s foobar
    Existing Asset Tag:
    Changing Asset Tag: foobar
    Change Successful. The changes may not take effect until reboot, depending on
    system type.

---

