---
title: "Conky imap"
date: 2008-12-28
forum: General Help
---

### Post by Gizmo688 on 2008-12-28
My conky script runs fine once its opened, but after a bit, the email counts go to zero. Code included...

```

   ${color 2D2828}${font FreeSans:size=16}@${font}  BamaMail: ${imap_unseen server user pass}
   ${color 2D2828}${font FreeSans:size=16}@${font}  Alltel: ${imap_unseen server user pass}
```

---

### Post by Gizmo688 on 2008-12-30
bump...

would it help if i said i cant use evolution for one of these servers if conky is running?

---

### Post by Matteus_Blanc on 2010-11-25
I know it's been two years since this questions was posed but the answer is useful and doesn't seem to be too easy to find on google.

Essentially your problem is caused by conky exceeding the number of retries and giving up. The default for retries is 5 so you should up this to say 20 using the -r option. Here is what I have:

```

imap localhost username * -i 30 -f INBOX -r 20
```

If you still get the zero emails effect then up the number. Tends to be a problem where there are network issues between your conky client and the server.

---

