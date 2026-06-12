---
title: "Warcraft 3 (do I need winetools?)"
date: 2007-06-16
forum: Gaming &amp; Leisure
---

### Post by Tadpole on 2007-06-16
I read through [the HOWTO](http://ubuntuforums.org/showthread.php?t=45407) but stopped short at #3 because apparently winetools doesn't exist, or at least isn't available in a Debian package. Apparently I need it to create a fake windows drive, and install TrueType Font Arial and DCOM98.

Is it okay to skip that step entirely?

---

### Post by Anonii on 2007-06-16
Are you sure you did the : sudo apt-get update?
If you are sure, then:
The third step will also install Wine, which is essential, but you can bypass it if you install Wine by yourself (which exists as a package) and then download and compile winetools manually (not that tough, don't be afraid.). It's weird, tho, because the complains about winetools not existing started in the last page of that guide you posted.
Install wine by executing this: sudo apt-get install wine
Now, follow the instructions in this post [http://ubuntuforums.org/showpost.php?p=2796057&postcount=114](http://ubuntuforums.org/showpost.php?p=2796057&postcount=114) to install the winetools. 
After that, I think that it's OK to continue with the guide.

---

### Post by Anonii on 2007-06-16
Also, from what I noticed that howto is terribly old (in the open-source world, and especially for the Wine project 2 years are terribly many). The next steps require you to change the old config file of Wine, which right now is replaced with a cute nifty GUI config manager. I don't think it will be hard to change the Windows version using it, but just pointing it out. Also, the repository you added for the binary of wine (the first step) may be dead (or have the winetools package removed), after 2 years. 
I'd suggest you leaving that guide alone (except if you read all the pages and see what changed these 2 years), and following the install notes from the application database of Wine (which may be somewhat complicated. In that case, continue with your previous guide), here:
[http://appdb.winehq.org/appview.php?iAppId=897](http://appdb.winehq.org/appview.php?iAppId=897)  (It won't explain how to install Wine there, but you can do that using this guide: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine) )

---

### Post by Tadpole on 2007-06-16
> I'd suggest you leaving that guide alone (except if you read all the pages and see what changed these 2 years), and following the install notes from the application database of Wine (which may be somewhat complicated. In that case, continue with your previous guide), here:
[http://appdb.winehq.org/appview.php?iAppId=897](http://appdb.winehq.org/appview.php?iAppId=897) (It won't explain how to install Wine there, but you can do that using this guide: [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine) )
Isn't it fine to just use Synaptic to install wine?

Thanks very much for the app db link. I had no idea that existed and it looks like it'll help out a lot.

---

### Post by Anonii on 2007-06-16
> **Tadpole said:**
> Isn't it fine to just use Synaptic to install wine?

Thanks very much for the app db link. I had no idea that existed and it looks like it'll help out a lot.
Actually, the link I posted ([https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)) says the same thing, in the first paragraph.

---

