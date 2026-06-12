---
title: "Want specific user to boot to Firefox"
date: 2008-01-15
forum: Desktop Environments
---

### Post by sburckhard on 2008-01-15
I have a situation where I want a specific user aka: webuser to load up and only have firefox as thier choice, basically I dont want "webuser" to be able to install or do anything else.

Any good way of doing this?

Thanks!

---

### Post by riggsd on 2008-01-16
You could try setting their shell to firefox instead of bash...

```
su -
echo /usr/bin/firefox >> /etc/shells
usermod -s /usr/bin/firefox webuser
```

Closing firefox would end their login session.

---

### Post by sburckhard on 2008-01-16
hmm didnt work...

I have also been looking at kubuntu with the kiosk admin tools. might be a better way to go.

---

### Post by sburckhard on 2008-01-17
Any other ideas folks?  i mean someone here has had of tried making a web only kiosk machine???

---

