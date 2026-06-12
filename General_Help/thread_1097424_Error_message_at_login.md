---
title: "Error message at login"
date: 2009-03-15
forum: General Help
---

### Post by marenum on 2009-03-15
After I put in my password on the login screen it comes up with this message:

"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by others."

After that everything seems to be fine, but it's kind of annoying. Any ideas how I can get rid of it?

---

### Post by theozzlives on 2009-03-15
go to terminal and type ```
sudo chmod 644 ~/.dmrc
```

---

### Post by marenum on 2009-03-16
hmm, it's still coming up. Anything else?

---

### Post by orlox on 2009-03-16
maybe...

```
sudo chown <username> /home/<username>
```

---

