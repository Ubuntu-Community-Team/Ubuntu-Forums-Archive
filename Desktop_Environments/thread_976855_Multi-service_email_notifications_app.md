---
title: "Multi-service email notifications app"
date: 2008-11-09
forum: Desktop Environments
---

### Post by fizikz on 2008-11-09
Is there a notification application that can give popups and/or status area icons for new emails from a variety of services (gmail, hotmail, etc)? I am using cGmail for my gmail account, but I think it only works with gmail. I used to use aMSN which has popups and puts a new mail icon in the status bar area, but now I'm trying out Pidgin, and I don't see any similar options for hotmail notifications. I'd like it if I could have one application checking all my email accounts and consolidating all the notifications.

---

### Post by astoltz on 2008-11-09
Try mail-notification.  It's in the repositories...

---

### Post by fizikz on 2008-11-09
Thanks, that's just the kind of thing I'm looking for. It is fetching from my gmail account just fine, but it's not working with hotmail. I get an error message as follows:

"cannot execute "GetLive": Failed to execute child process "GetLive" (No such file or directory)"

Occasionally I also get a "unable to retrieve feed: Generic error" message for both hotmail and gmail accounts.

I would really like to get this or a similar application working right...

---

### Post by astoltz on 2008-11-10
I don't use hotmail, but it looks like you've got to install the "getlive" package.  It's also in the repos.

I'm afraid I can't help with the other error.

---

### Post by fizikz on 2008-11-10
I did find and install the 'getlive' package from the repositories. I think it's strange that the mail-notifications package wouldn't require it's dependencies to be installed, but anyways, I have it now. However, I still get the error about 'GetLive'. The other error seems not to be too important as it goes away on it's own. So, gmail is working fine, but hotmail still hasn't worked even with the 'getlive' package installed.

---

