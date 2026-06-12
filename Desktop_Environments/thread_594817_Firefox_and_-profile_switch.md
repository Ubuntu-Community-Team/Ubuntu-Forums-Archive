---
title: "Firefox and -profile switch"
date: 2007-10-28
forum: Desktop Environments
---

### Post by dafi on 2007-10-28
Hi,

I've a problem with Firefox downloaded/updated from Ubuntu repository.
It doesn't support the "-profile" switch (all lowercase)

The tar.gz downloaded directly from mozilla website has support for -profile switch.

This switch bypasses the profile manager allowing to create profiles in every **already existing** directory
for example

```
export MOZ_NO_REMOTE=1
mkdir ~/myprofile
firefox -profile ~/myprofile
```

runs firefox creating profile files into ~/myprofile
The ~/.mozilla/firefox/profiles.ini isn't used.

Any idea because the ubuntu's firefox version has lost the switch?

---

### Post by por100pre1 on 2007-10-29
Try this:

```
firefox -P *profile*
```

or use the profile manager:

```
firefox -ProfileManager
```

Read more in the manual:

```
man firefox
```

press q to close the manual.

Hope it helps. :)

---

### Post by dafi on 2007-10-29
> **por100pre1 said:**
> Try this:

```
firefox -P *profile*
```

-P (uppercase) start a profile but you cannot specify target directory

Maybe my bad english doesn't explain better the problem.

Mozilla firefox downloaded from [mozilla ftp]("ftp://ftp.mozilla.org/pub/firefox/releases/2.0.0.8/linux-i686/en-US/firefox-2.0.0.8.tar.gz") has another switch **-profile** (dash followed by the lowecase string **profile**)
Using this switch
- you can  use your preferred profile directory (eg /tmp/myprofile)
- profile manager doesn't show profiles created using this technique


> **por100pre1 said:**
> or use the profile manager:

```
firefox -ProfileManager
```
So you see the UI from which select profile, I don't want this.

The firefox bundled in Ubuntu is a modified version from original one, period!

> **por100pre1 said:**
> 
Read more in the manual:
```
man firefox
```

press q to close the manual.

Hope it helps. :)
No words... :(

thanks for your help

---

