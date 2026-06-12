---
title: "Large problem with my .ICEauthority file. Main user account not booting."
date: 2010-02-27
forum: Desktop Environments
---

### Post by Trougedoor122 on 2010-02-27
Hello all, the problem I am facing is one that is very annoying, I can't boot into my main user account. every time I try i get the following errors: 
 
"Could not update ICEauthority file /home/justin/.ICEauthority" 
 
"There is a problem with the configuration server. (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)"
 
I have tried countless solutions to this problem, and would like to put it out in advance that this is probably not a problem with file permissions as all of the fixes I have tried for that didn't work. I encrypted my home folder during installation and recently changed my password but didn't unwrap my new passphrase. Any help in the matter would be greatly appreciated.

---

### Post by Trougedoor122 on 2010-03-02
Um... Can I have some help please?

---

### Post by nothingspecial on 2010-03-02
> **Trougedoor122 said:**
>  I encrypted my home folder during installation and recently changed my password but didn't unwrap my new passphrase. Any help in the matter would be greatly appreciated.

You can probably solve this by changing your password again.

Login to a root recovery shell and issue ```
passwd username
```

Change your password then try to log in normally with the new password.

---

### Post by Trougedoor122 on 2010-03-06
Changing my password didn't work.

---

### Post by Oldbones on 2010-05-10
I am having this same problem as well.  Here's my situation.

I didn't like how 10.04 upgraded my system, so I opted for a clean install.  I'm using a Dell Inspiron 1501 which has an ATI graphics card (w/ nvidia chip :confused:) whose display doesn't work with the Live CD.  I therefore installed with a alternate CD - which worked great.  

Here's where everything went wrong:  I had a /home partition I **didn't** format that I was expecting to use with the freshly installed kernel.  While going through the alternate-install-CD menu system, I simply placed in all the current credentials (username password) expecting to only have one user name.   

I've explored the threads and can't get any satisfaction.  I could format the /home participation but I would lose a lot of time building my system back up.

I can get to the terminal easy enough by hitting ctrl+alt+F1

-Oldbones

---

