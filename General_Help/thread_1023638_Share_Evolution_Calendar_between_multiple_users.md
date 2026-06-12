---
title: "Share Evolution Calendar between multiple users?"
date: 2008-12-28
forum: General Help
---

### Post by jondecker76 on 2008-12-28
I'm using Ubuntu 0810. My wife and I both use separate logons, but would really like to be able to syncronize our Evolution Calendar (and contacts for that matter).

I already have a shared folder set up where the users group has full read/write access to.

Is there any way to do this?

thanks,
Jon

---

### Post by dcstar on 2008-12-28
> **jondecker76 said:**
> I'm using Ubuntu 0810. My wife and I both use separate logons, but would really like to be able to syncronize our Evolution Calendar (and contacts for that matter).

I already have a shared folder set up where the users group has full read/write access to.

Is there any way to do this?

thanks,
Jon

You can probably make a link of the Calendar files in your .evolution directory, and then move the links to the other user's .evolution directory renaming the links and replacing those same calendar files.

That way Evolution will reference those same files for both users.

Beware that you then cannot run Evolution and therefore access the same files from simultaneous logins (which is possible to do).

---

### Post by jondecker76 on 2008-12-28
I'll give that a try... I move the calendar file to our shared folder that we both have full read/write access to, and then make symbolic links to that from within .evolution folders of both of our home folders.

Thanks for the suggestion!

---

