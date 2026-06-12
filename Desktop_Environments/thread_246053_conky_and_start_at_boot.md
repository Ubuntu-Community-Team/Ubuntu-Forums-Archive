---
title: "conky and start at boot"
date: 2006-08-28
forum: Desktop Environments
---

### Post by mitjab on 2006-08-28
i add it to systm/settings/sesion but not working. Conky start at boot after gnome is loading, but then dissapear.

Can anyone tell me why?

---

### Post by kpkeerthi on 2006-08-28
Can you post the screenshot of session startup window?

---

### Post by kerry_s on 2006-08-28
You can make a script to have it start after natilus.
Create a text file name it " .conky " click on it to open it in gedit, put this in side->

```
#!/bin/sh
sleep 5
 conky
 fi
```

Now cose it and right click on it and go to the permissions and check the box next to execute to make it excutable. Now add it to your startup> /home/user/.conky

that's it just adjust the  time as needed to get it how you want.

---

### Post by szf on 2006-08-28
Are you using the repository Conky or a checkinstall-built one?

---

### Post by P_Badger on 2006-10-21
> **kerry_s said:**
> You can make a script to have it start after natilus.
Create a text file name it " .conky " click on it to open it in gedit, put this in side->

```
#!/bin/sh
sleep 5
 conky
 fi
```

Now cose it and right click on it and go to the permissions and check the box next to execute to make it excutable. Now add it to your startup> /home/user/.conky

that's it just adjust the  time as needed to get it how you want.

Thanks! This worked like a charm.

---

