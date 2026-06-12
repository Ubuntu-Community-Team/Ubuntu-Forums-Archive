---
title: "ScummVM 0.8.0"
date: 2006-01-01
forum: Desktop Environments
---

### Post by shaj on 2006-01-01
Is there any way to get this version installed on Breezy?

Any help would be appreciated...

---

### Post by bonzodog on 2006-01-01
You can get 0.8.0 from [http://www.scummvm.org/downloads.php](http://www.scummvm.org/downloads.php) in .deb form as a 386 package.
download, then install with:

```
sudo dpkg -i scummvm_0.8.0-0.sarge.1_i386.deb
```

***Please note: this is from the unstable sid - it is liable to breakage***

if anything breaks during it's install do:

```
sudo apt-get -f install
```

It should work hopefully.

---

### Post by shaj on 2006-01-01
[QUOTE=bonzodog]You can get 0.8.0 from [http://www.scummvm.org/downloads.php](http://www.scummvm.org/downloads.php) in .deb form as a 386 package.
download, then install with:

```
sudo dpkg -i scummvm_0.8.0-0.sarge.1_i386.deb
```[/QUOTE]

I had done the above before posting, and it said I was missing two files...

I can't remember exactly but both started, I think, with lib.

One had something to do with flac and the other with midi

---

### Post by nozdormu on 2006-01-01
[QUOTE=shaj]I had done the above before posting, and it said I was missing two files...

I can't remember exactly but both started, I think, with lib.

One had something to do with flac and the other with midi[/QUOTE]

Those are other required packages.  Either get them with apt or search for them on Google.

---

### Post by ardchoille on 2006-10-02
scummvm 0.8.0 is in the universe repo.

---

