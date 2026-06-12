---
title: "Some apt suggestions for Gutsy?"
date: 2009-02-21
forum: General Help
---

### Post by amkr on 2009-02-21
I just started rolling with Gutsy (kicked out moronic Windows). Can you please suggest some apts that are handy and also those that are gonna make me NOT miss Windows (such as Guitar Pro5, WinRar, Picasa etc on Ubuntu Gutsy).:popcorn:

---

### Post by Slim Odds on 2009-02-21
Well, first off, Gutsy is obsolete.

You should be using Hardy instead.

---

### Post by amkr on 2009-02-21
> **Slim Odds said:**
> Well, first off, Gutsy is obsolete.

You should be using Hardy instead.

Well that ^ was helpful! Anyways, it seems u know Ubuntu (by that coffee thingy) so can you please tell me how do I update the it from Gutsy to Hardy or Ibex (without Internet)? Can I just do it like I do apts with gdebi-gtk? Any help will be appreciated. Thanx in advance!

PS: I'm an absoulte Ubuntu newbie, so stop laughing at my ignorance already, ;)

---

### Post by Slim Odds on 2009-02-21
How did you get Gutsy in the first place?

---

### Post by yeleek on 2009-02-21
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

and

[https://help.ubuntu.com/community/IntrepidUpgrades](https://help.ubuntu.com/community/IntrepidUpgrades)

Regards

---

### Post by amkr on 2009-02-22
> **Slim Odds said:**
> How did you get Gutsy in the first place?

Friend gave an old DVD to me. Told me to check it out. If I like, I can update to Ibex.

---

### Post by mb_webguy on 2009-02-22
> **amkr said:**
> I just started rolling with Gutsy (kicked out moronic Windows). Can you please suggest some apts that are handy and also those that are gonna make me NOT miss Windows (such as Guitar Pro5, WinRar, Picasa etc on Ubuntu Gutsy).:popcorn:

GuitarPro will [apparently]("http://appdb.winehq.org/appview.php?iAppId=246") run on Linux under [Wine]("http://www.winehq.org/") (which is good for those must-have Windows-only applications).  You might, however, want to check out [TuxGuitar]("http://www.tuxguitar.com.ar/").  It's apparently not as polished as GuitarPro, but it's native to Linux, and it's free (and in the repositories, so you can install it with Add/Remove Applications, Synaptic, or with the command "sudo apt-get install tuxguitar" in the terminal).

Picasa works just fine on Ubuntu.  Just download and install the Linux version from the [Google website]("http://picasa.google.com/linux/").

As for WinRar, you don't need it.  File Roller, the default Archive Manager in Ubuntu, supports rar archives through the packages rar (for creation) and unrar or p7zip-rar (for extraction).  I suggest using p7zip-rar instead of unrar because you'll also automatically get p7zip-full, which allows for the creation and extraction of several other types of archives.  Install them through Synaptic, or in the terminal with the command "sudo apt-get install rar p7zip-rar".

---

### Post by amkr on 2009-02-22
Thanx dude! That helped a lot!

---

