---
title: "cant append &quot;bash: sudo: Permission denied&quot;"
date: 2009-01-09
forum: General Help
---

### Post by max_power on 2009-01-09
im trying to catch errors and append them into a file.

im using:

```
2>&1 >> sudo tee errors.txt
```

i get:

bash: sudo: Permission denied


Any help here?
Thanks

---

### Post by Bachstelze on 2009-01-09
You should do:

```
2>&1 | sudo tee -a errors.txt
```

---

### Post by max_power on 2009-01-09
thank you!

---

