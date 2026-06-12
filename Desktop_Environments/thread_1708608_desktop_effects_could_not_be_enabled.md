---
title: "desktop effects could not be enabled"
date: 2011-03-16
forum: Desktop Environments
---

### Post by Zeck on 2011-03-16
I have an geforce 9800 nvidia graphics card and have enabled restricted drivers for this card.

Direct rendering is enabled when I check in Terminal. I'm typed 'compiz' from the terminal and I get below result:

```
compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0
```

I'm using Acer V193w LCD display. I'm not sure this issue maybe arising from my LCD display. Could somebody tell me how to fix this problem?

---

### Post by andrewthomas on 2011-03-19
Post the results of 

```
glxinfo|grep OpenGL
```

Did you use  --replace with compiz?

```
compiz --replace &
```

---

