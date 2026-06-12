---
title: "Fresh install 103 un-needed files."
date: 2009-04-18
forum: General Help
---

### Post by Kzap333 on 2009-04-18
Ok so I had a fresh install of the latest Ubuntu today and just from installing and uninstalling a few dock a widget programs (from the repositories and other sources) the new Computer Janitor software is telling me I have I have 103 deb files to clean up, I'm leaving off pushing the ok button till I know if this is normal?
I have already unticked the flash player as it wanted to uninstall that just because I didn't get it from the Ubuntu repositories.
Should I let it remove all 103 Deb files?

---

### Post by cariboo on 2009-04-18
It really depends on what the files actually are, if the files have a check mark, they are marked for deletion. I would suggest you open an Applications-->Accessories-->Terminal and type:

```
sudo apt-get clean
```

and then:

```
sudo apt-get autoremove
```

Then check Computer Janitor again. Remember Jaunty is still in Beta, so things may not work as ex[ected. THe RC is for the final bit of bug squashing befire release.

Jim

---

### Post by Kzap333 on 2009-04-18
> **cariboo907 said:**
> 
Then check Computer Janitor again. Remember Jaunty is still in Beta, so things may not work as ex[ected. THe RC is for the final bit of bug squashing befire release.

Jim
Thanks, I found the old beta a bit too buggy and though I would give the RC a go.
When I do that command it says something like "103 packages to be removed 66 not upgraded"
So I assume it's doing the same thing as Computer Janitor (except with Computer Janitor I had to tell it not to uninstall flash).
Thanks again.

---

### Post by Kzap333 on 2009-04-19
Computer Janitor broke nautilus, yay.
Don't ask me how but it's the only thing I was using now the file browser won't open the desktop background is displaying but nautilus won't open.

---

