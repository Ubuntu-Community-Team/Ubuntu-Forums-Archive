---
title: "Can't use &quot;dell-team&quot; software sources"
date: 2009-03-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by geoffm on 2009-03-03
When I try to select the [http://ppa.launchpad.net/dell-team/ubuntu](http://ppa.launchpad.net/dell-team/ubuntu)

I can't run the package manager, it says:

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8B9FBE5158B3AFA9

What's the problem?

---

### Post by mionescu on 2009-03-03
You probably need to add the PPA key to your system. You can read more about it at
[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

Scroll down to "Installing software from a PPA", "Adding a PPA's keys to your system".

---

### Post by sirebral on 2009-03-03
Did you complete this step?:

> Step 1: Visit the PPA's overview page in Launchpad. Let's go back to the AWN Testing team's PPA that we were looking at earlier.

Step 2: Click the key fingerprint on the overview page. It'll look something like this: B0BE17C2A0C914F086B7B8327D2C7A23BF810CD5`.

Step 3: This will take you to the key's page in the Ubuntu keyserver. Click the ID, which looks something like this: BF810CD5

Step 4: Copy the public key, which will be something like: -- i.e. the portion starting:

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXS1/wEEALis4to4JdgrkdRunmSTfB2tYRq99Cdcgdh9up4HzAf1yTZU1EtmETPP1Uy2
vnAFf/cCunL5VRywNJB3QOxiHdvNlijbdsa0H/fT/ulq+A4iDljUEfsaJug+dAB5uEJE0BzZ
agRjgLbFvRYtsKf3BwZizbo4XtWSAm3JSjZCGZKTABEBAAG0IkxhdW5jaHBhZCBQUEEgZm9y
IEF3biBUZXN0aW5nIFRlYW2IRgQQEQIABgUCSXqnWgAKCRBBf7ZCSCH+JPZMAJ4xW7gbpuA+
yedehvDQWdJHHUgseQCgy6NOmAyXqRKrIXWERkXw6h9TsRuItgQTAQIAIAUCSXS1/wIbAwYL
CQgHAwIEFQIIAwQWAgMBAh4BAheAAAoJEH0seiO/gQzVpSID/0FXxTSLtxPHrT7IE9eif5qJ
vjOjzcmOCXe9/3G0ctV8IfYHx0VynddjxgTqJ9WuEjMLVHRgXvK1Rw1XMlik+MeyyHrr9EWQ
DUFbUs+Yc2usRyZY8pVe2Uwy2x7lFsi6VBfo0k9jVsu1l1qBU9BhANJDUTHjR15aPYiUJiZa
13CZ
=a6Gh
-----END PGP PUBLIC KEY BLOCK-----

Step 5: Paste the public key into a text editor and save it.

Step 6: Open System->Administration->Software Sources and click the Authentication tab.

Step 7: Click Import Key File, select the key you saved earlier and you're done!

---

### Post by sirebral on 2009-03-03
Works for me.  I am running with LPIA also.  You just need the key.

---

### Post by floborg on 2009-03-04
These directions are missing one important thing.  Go here for the key:

[https://launchpad.net/~dell-team/+archive/ppa]("https://launchpad.net/~dell-team/+archive/ppa")

Now, my key error warning is gone when I run the Update Manager, but does anyone know why the kernel updates never have the list of changes?

---

### Post by floborg on 2009-03-21
> **floborg said:**
> ...but does anyone know why the kernel updates never have the list of changes?

Anyone know why the Update Manager can never seem to download the list of changes?

---

