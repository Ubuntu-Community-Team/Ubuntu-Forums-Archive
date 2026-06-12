---
title: "Can you ban me temporarily?"
date: 2009-12-28
forum: Forum Feedback &amp; Help
---

### Post by Cam42 on 2009-12-28
I spend way to much time on this stupid computer, and would like to be banned, for say a month. Is this possible?

---

### Post by jpeddicord on 2009-12-28
Perhaps there are more sane methods:

"ban:"
```
sudo bash -c 'echo -e "\n127.0.0.1 ubuntuforums.org" >> /etc/hosts'
```

"unban:"
```
sudo sed -i s/.*ubuntuforums\.org// /etc/hosts
```

---

### Post by CharlesA on 2009-12-28
> **jpeddicord said:**
> Perhaps there are more sane methods:

"ban:"
```
sudo bash -c 'echo -e "\n127.0.0.1 ubuntuforums.org" >> /etc/hosts'
```

"unban:"
```
sudo sed -i s/.*ubuntuforums\.org// /etc/hosts
```
This would work 100% :D

---

### Post by Joeb454 on 2009-12-29
You could even put it in cron ;)

That said, I think we could do it, though I'm not 100% sure

---

### Post by proxess on 2009-12-29
This thread has been marked as "way too geek". :arrow:

---

### Post by Cam42 on 2009-12-29
heh, too bad I don't run Linux regularly.

---

### Post by jpeddicord on 2009-12-29
> **Cam42 said:**
> heh, too bad I don't run Linux regularly.

Windows has a hosts file too: C:\windows\system32\drivers\hosts I think.

Add "127.0.0.1 ubuntuforums.org" as a line to that file and you're set. :D

---

