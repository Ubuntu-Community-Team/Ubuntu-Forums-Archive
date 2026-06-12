---
title: "Disable shutdown buton on logout screen"
date: 2006-08-04
forum: Desktop Environments
---

### Post by Narf on 2006-08-04
Is there a way to disable the shutdown button?
As far as I can remember, in the 5.* I could easily disable or enable it for each user. Unfortunately I couldn't find a way to do that in Dapper(even though it's possible for "Hibernate" and "Suspend") and it bugs me to hell as I run a few services that I need to be up 24/7 and my little brother simply shuts down the computer whenever he finishes playing his games, no matter how hard I try to explain him that I don't want him to do it.:-x

---

### Post by louis_nichols on 2006-08-05
you can simply modify rights for the shutdown command file to make it read-able just for your user...

---

### Post by it.henrik on 2006-08-05
does this disable the option from the logout screen?

---

### Post by louis_nichols on 2006-08-05
yes. basically, any user that doesn't have read rights on the file won't be able to shutdown the pc. now, if the icon disappears from the menu, I'm not sure, but that might not be so important...

---

### Post by Narf on 2006-08-06
And how do I do that?

---

### Post by louis_nichols on 2006-08-07
> **Narf said:**
> And how do I do that?

like this:

```
sudo chmod 700 /sbin/shutdown
```

---

### Post by Narf on 2006-08-16
Well, it doesn't work. :/
I guess it's because it uses sudo to run shutdown anyway...

---

### Post by louis_nichols on 2006-08-16
Well... then make it un-executable. you can shutdown after that with *init 0*. It's kind of un-orthodox, but it should work. Assuming, of course, that the shutdown command is indeed the one called when you press the button, and not some other script which uses init 0 directly. That I'm not sure of...

---

