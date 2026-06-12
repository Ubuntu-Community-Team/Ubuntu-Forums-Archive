---
title: "Password-Less Login Doesn't Work in KDE 3.5.9"
date: 2008-07-06
forum: Desktop Environments
---

### Post by Brando569 on 2008-07-06
I finally got frustrated with my parents infecting their computer with spyware and other nasty stuff because then my dad would complain about it and I would have to reinstall windows, now I'm forcing them to use Kubuntu (since all they do is check their email and browse the web) but the password-less logins for KDE 3.5.9 don't work (if I click the login button without entering a password it says "Login Failed". They don't have passwords on their windows accounts and will most likely start complaining if they have to type in a password each time they want to login.

I set passwords for both of their accounts but IIRC the password-less logins option allows you to have a password but allows you via KDM to login without typing one, or am I mistaken?

---

### Post by Bubba64 on 2008-07-06
You probably have to enter a user name somewhere in the password-less logins
process, just guessing. :)

---

### Post by ramaswamyps on 2008-07-06
you probably will have to edit kdmrc file.
there are all options available.
[B]be careful in changing the login arrangement.
you may be locked out of the system.[/B]

---

### Post by Brando569 on 2008-07-06
yes i did have to, there are two secions labeled [X*Core] and in the first one the AllowNullPassword was set to false while under the second one it was set to true. so i changed the previous one and we're good to go. thanks.

---

