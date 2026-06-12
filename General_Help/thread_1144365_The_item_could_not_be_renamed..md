---
title: "The item could not be renamed."
date: 2009-04-30
forum: General Help
---

### Post by WattoDaToydarian on 2009-04-30
I just discovered a bug in Nautilus where if you try to rename a file by changing the first letter from lowercase to uppercase it will fail saying:
> The item could not be renamed.
There is no "test" in this folder. Perhaps it was just moved or deleted?
And then it just deletes the file...

I have attached a screen shot of the error.

This happened to me a few times today one of which I had just finished downloading a large file and I wanted to change it's name, when I did it errored, disappeared, and I had to re-download the entire thing again...:(

Does anyone know of a fix or should a bug report be submitted?

---

### Post by dcstar on 2009-04-30
> **WattoDaToydarian said:**
> I just discovered a bug in Nautilus where if you try to rename a file by changing the first letter from lowercase to uppercase it will fail saying:

And then it just deletes the file...
........

Some filesystems are case insensitive and there is no point in trying to do things like this - FAT filesystem, for instance.

Changing case in my Nautilus works fine on Linux filesystems.

---

### Post by WattoDaToydarian on 2009-04-30
Well the point is I wanted a nicer name for my file...

It seems to work for most people. One thing I think it might be is I added the pre-released and unsupported updates in synaptic.
Can someone try those and see if it causes this error?

---

