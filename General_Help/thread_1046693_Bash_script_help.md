---
title: "Bash script help"
date: 2009-01-21
forum: General Help
---

### Post by Peter_G on 2009-01-21
I know this is being a bit rude so I  apologize, but I was wondering if someone could tell me how to make a bash script or something, where you drag a url onto the window, and it executes:

```
iplayer-dl $url
```

Thanks.

---

### Post by dagnabit dang doohickey on 2009-01-21
The following script may work for you. It requires that xsel is installed on your system. Save this script on your desktop, or wherever you find convenient, and make it executable. 
```
#!/usr/bin/env bash
xsel | iplayer-dl &
```
How it works:  Highlight the url and double-click the script. 

There may also be a convenient way to do this with a desktop launcher, but I don't use a desktop environment, so I wouldn't know about it.

---

