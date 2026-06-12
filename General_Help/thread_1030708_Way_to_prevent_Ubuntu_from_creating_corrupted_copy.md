---
title: "Way to prevent Ubuntu from creating corrupted copy of a file?"
date: 2009-01-04
forum: General Help
---

### Post by vanadium on 2009-01-04
I was copying files from a cd-rom and (as usual) some of the files would not anymore be readable. Linux unfortunately seems to have the habit of creating the file in the destination anyway, even if not all content has been copied over. My only option was to review the log of the copy command and manually remove the erroneous copies from the destination.

Is there a way/setting ... we can have a file automatically be deleted in the destination if the copy was not successful (that's the behaviour in MS Windows if I remember right)?

By the way, this behaviour is also there when you copy a file over, then decide you do not want to continue the copy after all (e.g. pressing "cancel" in the nautilus copy progress dialog). The copy operation is terminated, but a file containing all content copied thus far is created nevertheless.

---

