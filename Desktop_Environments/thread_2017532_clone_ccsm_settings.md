---
title: "clone ccsm settings?"
date: 2012-07-05
forum: Desktop Environments
---

### Post by chelmite2 on 2012-07-05
I want to copy my ccsm settings from one computer to another. How do I do that?

Thanks for any help you can give.

---

### Post by Krytarik on 2012-07-05
> **chelmite2 said:**
> I want to copy my ccsm settings from one computer to another. How do I do that?
For that, you can just use Export / Import under "Preferences (lower-left) -> Profile" in CCSM. :P

Regards.

---

### Post by chelmite2 on 2012-07-05
Excellent!  Thanks!

That allowed me to export the settings in a file.

I copied the file to my other system, used the import function, but the settings hadn't taken effect!
For example, under General/Focus & Raise Behaviour, I had "auto-raise" unchecked. However, in the imported system, the box was still checked!

---

### Post by Krytarik on 2012-07-05
> **chelmite2 said:**
> I copied the file to my other system, used the import function, but the settings hadn't taken effect!
For example, under General/Focus & Raise Behaviour, I had "auto-raise" unchecked. However, in the imported system, the box was still checked!
Maybe choose to *not* "skip default option values" on exporting!?

---

### Post by chelmite2 on 2012-07-05
Yeah, I figured that would be useful (and the option wasn't hidden), but it didn't work.

---

### Post by Krytarik on 2012-07-05
> **chelmite2 said:**
> Yeah, I figured that would be useful (and the option wasn't hidden), but it didn't work.
Another way would be to 'dump' the respective profile's GConf keys to a file:
```
gconftool-2 --dump /apps/compizconfig-1/profiles/PROFILENAME > FILENAME
```... and import them on the target system/user:
```
gconftool-2 --load FILENAME
```Notes: That path is for Ubuntu versions starting with Natty 11.04, for earlier versions it's just "compizconfig". And at least in Lucid 10.04, the profile stored in GConf is always the one that's *not* selected at that time, don't know if that's the same in the current Ubuntu versions.

---

### Post by Frogs Hair on 2012-07-05
If this is a Unity profile it may need to named as such . The following is from an OMG Ubuntu article. I exported a Compiz configuration had to do this when importing the changed configuration.  

Where it says “Please enter a name for the new profile:”, enter, “unity”. Then select add. At this point compiz will probably restart, don’t worry, this is normal… I think. Once Compiz has reloaded, you can test your new configuration .

---

