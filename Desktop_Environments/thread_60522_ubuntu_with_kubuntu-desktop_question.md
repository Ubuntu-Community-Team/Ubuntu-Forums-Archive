---
title: "ubuntu with kubuntu-desktop question"
date: 2005-08-28
forum: Desktop Environments
---

### Post by sal on 2005-08-28
i have ubuntu installed and am using kubuntu-desktop.

what i need help with is the following:

i use firefox as the default web browser, when i go to save a file,
it opens in the nautoles file manager and ask me where to save the file.

how do i get firefox to use konq as the default file manager so it will load instead of nautoles.

i use kontact as my default email client but when i click on an email link in firefox it loads evalution.

how do i get firefox to load kontact instead of evalution when i click on email links.

thanks.

---

### Post by Ramses on 2005-08-29
I don't think it is possible to use konqueror as filebrowser with firefox, but i could be wrong though.
Here is a tip for email problem, this is from: [http://forums.suselinuxsupport.de/index.php?showtopic=18336&pid=105769&st=0&#entry105769](http://forums.suselinuxsupport.de/index.php?showtopic=18336&pid=105769&st=0&#entry105769) 

Open Firefox, type the following in the firefox address line:

```
about:config
``` 

Next click the right mouse button and select :

```
New | String
``` 

Then in the New String, enter the following:

```
network.protocol-handler.app.mailto
``` 

For the String Value, enter:

```
kmail
```

---

