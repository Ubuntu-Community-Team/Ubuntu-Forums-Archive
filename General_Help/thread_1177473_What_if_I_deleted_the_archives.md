---
title: "What if I deleted the archives?"
date: 2009-06-03
forum: General Help
---

### Post by knottshawk on 2009-06-03
So my disk said it was full and a post I saw said to delete /var/cache/apt/archives. Well, I did that and now I can't add or remove any packages. What did I do wrong and how do I fix it?

---

### Post by s.fox on 2009-06-03
Hi,

Did you delete the folder or did you run:

```
sudo apt-get clean
```

-Ash R

---

### Post by dcraven on 2009-06-03
Did you delete the archives directory altogether or the contents inside it? If the former, try recreating the directory.

It would be more helpful for us if you gave us the error you get when you attempt to add or remove packages, that's for sure.

~djc

---

### Post by knottshawk on 2009-06-03
Sorry guys... I was able to add the directories back in and get it working again. Guess I hit the panic button too quickly. *sheepish*

---

