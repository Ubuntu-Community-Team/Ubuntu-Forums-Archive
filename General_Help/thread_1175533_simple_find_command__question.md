---
title: "simple find command  question"
date: 2009-06-01
forum: General Help
---

### Post by meg23 on 2009-06-01
When I use this command:

```
find /home -name '*.avi'
```

I get the following: 
```

/home/bobbob/.miro/Movies/myvideo.avi
```

Is there an option to not print the location of the file? I just want the file name. 

Thanks, MG

---

### Post by binary10 on 2009-06-01
```

find /home -name '*.avi' -printf "%f \n"

```

---

### Post by meg23 on 2009-06-01
Thats it! Thanks!

---

