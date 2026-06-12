---
title: "Terminal command for CHMOD"
date: 2006-04-28
forum: Desktop Environments
---

### Post by localhost on 2006-04-28
Running apache, need the command to chmod /var/www and all subfolders to 777. SOmething like

sudo chmod -f 0777 /var/www

That's not it though.

---

### Post by Qrk on 2006-04-28
Use -R to make it recursive```

sudo chmod -R 0777 /var/www
```

---

### Post by localhost on 2006-04-28
Thanks alot, I tried that before...must have been because I used a lower case R.

---

### Post by cgjones on 2006-04-28
Is there a specific reason you need to set the permissions that permissive on the web directory?

---

