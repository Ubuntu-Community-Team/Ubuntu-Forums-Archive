---
title: "Web Browser?"
date: 2010-09-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by UndueInfluence on 2010-09-02
Hello. Let me know if I should have posted this elsewhere. 
 
I have a Dell Mini9 with Ubuntu Linux. I believe it is the 8.x version. This morning the system notfied me to perform a software update. I did so.
 
After the update, the Firefox icon disappeared with a completely new icon in its place. The title is now simply "Web Browser." The browser seems to act like Firefox: same home page, same bookmarks, same history. I can get on the Web and to every site that I have tested so far.
 
When I go to "about" under the help menu, I get a notice that there is an XHTML error.
 
Does anyone have any idea what's going on here? I don't know whether I should reinstall anything or just ignore it.
 
Thanks!

---

### Post by Bronco24 on 2010-09-02
Hi. I suggest reinstall F-fox browser.

---

### Post by bobjack1550 on 2010-09-03
i also did the same but i got a 
Failed to execute child process "abrowser" (No such file or directory)

so i reinstalled firefox, it works all the tabs are there but all bookmarked pages are gone......and ideas

---

### Post by Elboully on 2010-09-03
Don't they get erased with a clean install of F-fox, unless you export them first?

---

### Post by mikewhatever on 2010-09-03
> **bobjack1550 said:**
> i also did the same but i got a 
Failed to execute child process "abrowser" (No such file or directory)

so i reinstalled firefox, it works all the tabs are there but all bookmarked pages are gone......and ideas

Look in .mozilla/firefox folder (nautilus ~/.mozilla/firefox). The new installation must have created another profile, but you can tell firefox to either use the old one, or to pull the bookmarks from it. The default profile should be named something like this - abcd1234.default. In case you want firefox to use it, start firefox from Terminal once with 'firefox -P default', and it will use the default profile henceforth.

---

### Post by ugm6hr on 2010-09-03
> **UndueInfluence said:**
> Does anyone have any idea what's going on here? I don't know whether I should reinstall anything or just ignore it.

This is specific to the Dell version of Ubuntu.

Don't worry about it.

---

