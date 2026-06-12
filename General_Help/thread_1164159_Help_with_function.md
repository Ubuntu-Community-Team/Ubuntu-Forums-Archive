---
title: "Help with function"
date: 2009-05-19
forum: General Help
---

### Post by KayakJim on 2009-05-19
In my ~/.bashrc, I have created the following function:
```

function findrep     {  grep -lr '$2' $1 | xargs sed -i -e 's|$2|$3|g';  }

```

When it runs, it creates backup files with a -e extension. 

Any ideas what is going wrong or how I can output what the command that is going to execute actually looks like?

---

