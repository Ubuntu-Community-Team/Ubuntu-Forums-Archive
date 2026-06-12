---
title: "FIrefox resets configurations"
date: 2009-05-23
forum: General Help
---

### Post by kostaz8 on 2009-05-23
Yesterday the electricity went off and after I opened my pc many problems appeared like i couldnt connect to the internet now its ok but firefox is a mess.It's like all the changes were reset the bookmarks are gone and i cant make any other configurations if i try to make google my homepage firefox redirects me to mozzila.something.com i hit ctrl+B to make a bookmark and nothing happens.But if i do on the terminal sudo firefox everything is back to normal can someone help me>?/

---

### Post by kostaz8 on 2009-05-23
bump

---

### Post by Legace on 2009-05-23
Close Firefox.
Then open terminal and execute the following:
```
mv ~/.mozilla/firefox ~/.mozilla/firefoxold
```

Then try to open firefox again.

---

### Post by kostaz8 on 2009-05-23
Thnx problem solved.

---

