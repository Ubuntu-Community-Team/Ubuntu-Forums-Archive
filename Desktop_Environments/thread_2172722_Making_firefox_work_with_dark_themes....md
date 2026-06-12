---
title: "Making firefox work with dark themes..."
date: 2013-09-06
forum: Desktop Environments
---

### Post by Baldrick_NZ on 2013-09-06
Hi all,

When an author of a theme suggests to create a css file that has 'your_profile' in the path, does that generally mean one's username they log into Ubuntu with? Or something else?

This is part of the script I need to work with...```
'~/.mozilla/firefox/<YOUR_PROFILE>/chrome/userContent.css'
```

Sorry if it seems like a dumb question!

Cheers.

---

### Post by vasa1 on 2013-09-06
> **Baldrick_NZ said:**
> Hi all,

When an author of a theme suggests to create a css file that has 'your_profile' in the path, does that generally mean one's username they log into Ubuntu with? Or something else?

This is part of the script I need to work with...```
'~/.mozilla/firefox/<YOUR_PROFILE>/chrome/userContent.css'
```

Sorry if it seems like a dumb question!

Cheers.

Mine looks like this: ```
/home/vasa1/.mozilla/firefox/zbhohvqx.default/chrome/userContent.css
```
So it's a string of letters (and/or numbers). You may need to create the **chrome** folder and **userContent.css** if they aren't present. Both are case-sensitive. The latter has to be saved as a plain text file. So don't use a fancy word processor or, if you do, make sure you save as "text only".

Forgot to mention ... it doesn't have anything to do with your username you use for logging into Ubuntu.

---

