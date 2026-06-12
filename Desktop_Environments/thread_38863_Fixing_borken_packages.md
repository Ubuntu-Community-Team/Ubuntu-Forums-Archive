---
title: "Fixing borken packages"
date: 2005-06-02
forum: Desktop Environments
---

### Post by erik-the-red on 2005-06-02
Well, I finally was able to properly configure Synaptic. Turns out I had NO repositories turned on :)

libc6-i686
locales
ligblib2.0-data
lsb
ubuntu-desktop
ubuntu-base

These are affected. What can I do to fix them?

---

### Post by erik-the-red on 2005-06-02
Bring up my post.

---

### Post by erik-the-red on 2005-06-03
Bump

---

### Post by Knome_fan on 2005-06-03
Maybe it's just my usual stupidity, but I don't really understand your problem. You mention some packages that are affected, but don't mention by what they are affected.

Anyway, apt-get -f install as root in a terminal can help fix some issues.

---

### Post by erik-the-red on 2005-06-04
[QUOTE=Knome_fan]Maybe it's just my usual stupidity, but I don't really understand your problem. You mention some packages that are affected, but don't mention by what they are affected.

Anyway, apt-get -f install as root in a terminal can help fix some issues.[/QUOTE]

Sorry!

Well, the problem probably started because I did not turn on repositories in Synaptic.

Instead, I tried to download and manually configure many packages through the Online Debian Archive.

I guess I have some seriously unresolved dependency problems.

Can I just remove those programs and reinstall them through the Ubuntu disc?

---

### Post by Knome_fan on 2005-06-05
You could try that, but make sure that no other packages you absolutely need are removed in the process.

Also, did you try apt-get -f install? This will try to automatically fix your problems. Now if that's possible depends on what packages you installed exactly. If you really tried to install many packages from Debian proper, you might have a problem and removing the offending packages and reinstalling them from Ubuntu proper would probably be the best option.

---

