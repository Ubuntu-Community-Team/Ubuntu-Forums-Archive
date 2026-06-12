---
title: "Please help with Anymeal"
date: 2009-04-16
forum: General Help
---

### Post by Desolo_Amour on 2009-04-16
I'm having a problem with "Anymeal" (I love to cook so I thought I'd be a cool app). Every time I try to start it and it come on correctly. Then I am supposed to connect and no matter if I pick embedded or network I get an error message. The message is "Failed to create directory '/home/faery/.kde/share/apps/anymeal/db': Is a directory". Does anyone have a clue what's wrong?

---

### Post by codeseer on 2009-04-16
Have you tried creating that directory for it?

---

### Post by Desolo_Amour on 2009-04-16
I'm not sure how. I'm REALLY new to ubuntu. I've only worked with Windows before now.

---

### Post by codeseer on 2009-04-16
> **Desolo_Amour said:**
> I'm not sure how. I'm REALLY new to ubuntu. I've only worked with Windows before now.

In the top right corner of your screen, click Applications, click Accessories, click Terminal and copy/paste this into it:

```

mkdir /home/faery/.kde/share/apps/anymeal/db

```

..and hit Enter.

---

### Post by Desolo_Amour on 2009-04-17
Ok I tried to create it and it wouldn't let me

---

### Post by codeseer on 2009-04-17
What did it say?

Does it not let you do it when you use:

```
mkdir ~/.kde/share/apps/anymeal/db
```

Have you tried to create it through the file viewer (nautilus)?
Go to Places at the top left of your screen, click Home, hit CTRL+H, go down as deep as there are already folders starting at the .kde folder an then seeing if the share folder is under it, when you get to a folder that isn't there right-click and 'create folder'.

---

### Post by meeko on 2009-04-17
I bet the parent directories do not exist, hence you would need to use
```
mkdir -p ~/.kde/share/apps/anymeal/db
```

---

