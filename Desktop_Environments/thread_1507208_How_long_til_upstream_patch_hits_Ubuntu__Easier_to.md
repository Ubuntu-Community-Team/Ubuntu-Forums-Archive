---
title: "How long til upstream patch hits Ubuntu?  Easier to patch?"
date: 2010-06-11
forum: Desktop Environments
---

### Post by Huufarted on 2010-06-11
Referencing bug: [https://bugzilla.gnome.org/show_bug.cgi?id=599181](https://bugzilla.gnome.org/show_bug.cgi?id=599181)

The above has seemingly been patched and is valued at highly critical.  It's an incredibly annoying bug that I've submitted in the past and it's just now found a patch.

I have 2 options.  One, I wait for the upstream patch to filter to Ubuntu.  Does anybody know how I can figure out how long this takes on average?

The second option is to package the Ubuntu repo source with this particular patch, then recompile.  My dilemma in THIS area is that I have no idea how.  It's very easy to get the source:  [https://launchpad.net/ubuntu/+source/metacity/1:2.30.1-0ubuntu1](https://launchpad.net/ubuntu/+source/metacity/1:2.30.1-0ubuntu1)

I'm just unfamiliar with how to patch Ubuntu packages.  It looks like you take the original source (also provided) and apply the ubuntu specific patches, then turn around and apply this bug patch (which shouldn't interfere).

I don't know how to patch it and once done, it's not a standard ./configure && make && make install

Any ideas?

---

