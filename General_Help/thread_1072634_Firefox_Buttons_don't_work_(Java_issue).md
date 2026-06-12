---
title: "Firefox Buttons don't work (Java issue?)"
date: 2009-02-17
forum: General Help
---

### Post by dwieeb on 2009-02-17
My homepage is google, so when I tried to search, the button on Google didn't work. I tried the form buttons out everywhere and none work. I had to install Arora to post this message. All the HTML links work fine. I don't know whats wrong, has anyone had this error before?

---

### Post by kanikilu on 2009-02-17
Not sure why it would have anything to do with Java since forms like that are just HTML. Anyways, you might try ruling out a Firefox profile problem by creating a new one. You can do that by closing any current Firefox windows and running:
```
$ firefox -ProfileManager
```

---

### Post by dwieeb on 2009-02-17
Thanks for your reply,
but when I tried to create a new profile, it gave me another error:
```
Profile couldn't be created. Probably the chosen folder isn't writable.
[Exception... "Component returned failure code: 0x80004005 (NS_ERROR_FAILURE) [nsIToolkitProfileService.createProfile]"  nsresult: "0x80004005 (NS_ERROR_FAILURE)"  location: "JS frame :: chrome://mozapps/content/profile/createProfileWizard.js :: onFinish :: line 233"  data: no]
```

---

