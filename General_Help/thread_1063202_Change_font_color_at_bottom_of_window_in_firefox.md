---
title: "Change font color at bottom of window in firefox"
date: 2009-02-07
forum: General Help
---

### Post by jonlemur on 2009-02-07
I don't know how it got turned white in the first place, but the font at the bottom of the window in firefox is very hard to read, being white against a grey background.  This is the text that displays things like "Done" or shows what site a link points to when you hover over it.  I haven't been able to find what configures that font.  Any ideas?

---

### Post by gettinoriginal on 2009-02-07
That is your status bar, and is part of the browser, so should be the same font as the toolbars.  Go to Edit, Preferences, Content, Colors, and make sure that the line "allow pages to select their own colors" is checked.

---

### Post by mb_webguy on 2009-02-07
I don't know what changed it, but you can change it back using the userChrome.css file.  Look in your ~/.mozilla/firefox directory.  You should see at least one oddly-named folder, something like "tfcqzw68.default" (though it will be different for you).  If you see more than one such folder, then you need to figure out which one is your primary profile.  Inside that folder, you should see one named "chrome", and inside that a file named "userChrome-example.css".  Copy this file, and rename the copy to "userChrome.css".  Edit this file and add the following line to the end of the file:```
#status-bar { color: #000000 !important; }
```

Save the file, then restart Firefox.  The statusbar text should now be black.

---

### Post by jonlemur on 2009-02-07
Adding that line to the file worked.  Thanks!

---

