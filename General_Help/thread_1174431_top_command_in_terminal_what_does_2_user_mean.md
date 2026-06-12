---
title: "top command in terminal what does 2 user mean"
date: 2009-05-30
forum: General Help
---

### Post by colonelpotter on 2009-05-30
[SIZE=3]Top command in terminal says two users like I have to people logged in but I should be the only one [top - 19:50:17 up  2:36,  2 users][/SIZE]

---

### Post by redmk2 on 2009-05-30
> **colonelpotter said:**
> [SIZE=3]Top command in terminal says two users like I have to people logged in but I should be the only one [top - 19:50:17 up  2:36,  2 users][/SIZE]

I see 2 users.  Phillip and root.

---

### Post by jerome1232 on 2009-05-30
If I remember correctly each terminal open counts as a user, pop open like 5 of those terminals you should see more users. So your logged in to your x session and your logged in to that terminal session you have open.

---

### Post by dcstar on 2009-05-30
> **colonelpotter said:**
> Top command in terminal says two users like I have to people logged in but I should be the only one [top - 19:50:17 up  2:36,  2 users]

You do **not** have 2 users "logged in", there are two users in the system running processes - root and you, only one is "logged in".

---

### Post by colonelpotter on 2009-05-31
I understand now. I typed q and it stopped top and showed 1 user.

---

### Post by mcduck on 2009-05-31
> **dcstar said:**
> You do **not** have 2 users "logged in", there are two users in the system running processes - root and you, only one is "logged in".

No, actually it really *does* mean 2 users logged in. Every terminal you open acts as a new log in session. It just doesn't mean two *different* users, one user can log in multiple times.

(most likely there are several more users running, many system services run as daemons which are users of their own.)

You can use the command "who" to check current users and where they are logged in. Alternatively, "w" will also show what the users are doing...

---

### Post by jensa on 2009-05-31
The only problem i'm able to identify in that screenshot is a Folder containing the very best of Foreigner. That is impossible. It cannot be! There's nothing best about Foreigner..! ;-)

---

