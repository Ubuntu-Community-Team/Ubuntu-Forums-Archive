---
title: "Google earth server login fails when running as a normal user"
date: 2009-03-01
forum: Desktop Environments
---

### Post by dukeinlondon on 2009-03-01
I've installed google earth 5 in my home directory (as my regular user i.e. no sudo) and it starts up fine but if I run it without sudoing, it just sits there displaying no data whatsoever. In the file menu, I have the option to do a server login, but that doesn't work

Sudoing makes it work, it displays the start-up tip and the globe and the file menu has an option to do a server log-out. 

Any idea what could cause the server login to fail in this configuration ?

Thanks

---

### Post by m3peters on 2009-04-10
For the record, the solution I found to this problem is documented at [Thread 206711]("http://ubuntuforums.org/showthread.php?t=206711").

In short, you need to recursively set the owner of ~/.config/Google and ~/.googleearth:

```

sudo chown -R username:username ~/.config/Google
sudo chown -R username:username ~/.googleearth/

```

For me, somehow ~/.config/Google was owned by root while ~/.googleearth was owned by me.

Symptoms of this issue are: all Options in the Options Dialog are greyed out, a black (blank) sky with no Earth, and of course, as originally posted, an inability to log into the Earth server.

I apologize for resurrecting this.

---

### Post by andersja on 2009-04-21
Thanks for sharing the fix! I had the same problem!

---

### Post by shane2peru on 2009-04-22
> **m3peters said:**
> For the record, the solution I found to this problem is documented at [Thread 206711]("http://ubuntuforums.org/showthread.php?t=206711").

In short, you need to recursively set the owner of ~/.config/Google and ~/.googleearth:

```

sudo chown -R username:username ~/.config/Google
sudo chown -R username:username ~/.googleearth/

```

For me, somehow ~/.config/Google was owned by root while ~/.googleearth was owned by me.

Symptoms of this issue are: all Options in the Options Dialog are greyed out, a black (blank) sky with no Earth, and of course, as originally posted, an inability to log into the Earth server.

I apologize for resurrecting this.


No apology necessary.  Thanks this fixed my problem too!

Shane

---

