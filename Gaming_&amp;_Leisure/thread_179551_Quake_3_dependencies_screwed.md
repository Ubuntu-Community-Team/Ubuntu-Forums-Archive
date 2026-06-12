---
title: "Quake 3 dependencies screwed"
date: 2006-05-20
forum: Gaming &amp; Leisure
---

### Post by LCID Fire on 2006-05-20
The dependencies of the Quake 3 package are screwed in dapper. A library was renamed and the maintainer did not yet reflect this change.
Namely
libopenal0
was renamed to libopenal0a
Since the quake3 package seems to origin from debian unstable I don't think the change will be reflected in the near future.
So my question - how can I tell synaptic to keep libopenal0 so quake3 isn't removed (due to the missing dependency)? I tried locking the version - but it apprearently doesn't lock that hard ;)

---

### Post by Perfect Storm on 2006-05-20
Try making a symblink, that should do the trick.

---

### Post by LCID Fire on 2006-05-25
A symblink? What, to where, how?
Could you describe a little more. Is there a way to tell synaptic to not remove a certain package?

---

### Post by LCID Fire on 2006-05-28
Ok, I fixed it using dselect (which doesn't force you to remove non existant packages).

---

