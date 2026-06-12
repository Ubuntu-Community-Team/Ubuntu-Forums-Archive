---
title: "Help getting ISO-8859-1 input in english ubuntu"
date: 2005-09-09
forum: Desktop Environments
---

### Post by Lapse on 2005-09-09
Hey
I want to be able to type in ISO-8859-1 everywhere in my ubuntu when I set it to english language. Now when I set it to english I can type characters like ä å and ö in files, name folders with them etc. etc... but I can't use them in aterm for example.

I really want to have english menus, term messages and stuff, and be able to use ISO-8859-1 **everywhere**.

---

### Post by John Nilsson on 2005-09-10
Actually, if you are using Hoary, the default isn't ISO-8859-1 but rahter a Unicode encoding called UTF-8.

The problem is that not all applications has been upgraded to support Unicode (Unicode encodings require more than 8bit per character. In the case of UTF-8, bit/char varies between 8 and 32. Most of ISO-8859-1 characters are handled by 8bit, but åäö isn't)

---

