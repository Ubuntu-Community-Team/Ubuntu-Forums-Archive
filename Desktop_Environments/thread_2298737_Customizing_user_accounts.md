---
title: "Customizing user accounts"
date: 2015-10-13
forum: Desktop Environments
---

### Post by kablizzo on 2015-10-13
Greetings! I am setting up an OS for a PXE server. I've gotten the latest version of Ubuntu installed, removed Unity and loaded Xfce (there are some older systems being used as clients). Now I need to add all the user accounts.

I would like specific bookmarks to be loaded into firefox and certain shortcuts added and removed from the rat menu. Is there a way I can do this without going into each individual profile and changing it? I haven't created the profiles yet so maybe there is a default or some template user profile I can change?

I apologize for then newb question, but that is what I am.

---

### Post by TheFu on 2015-10-13
ansible to automate HOME setup
 or 
modify /etc/skel/ with whatever settings you want. [https://askubuntu.com/questions/186487/how-to-ensure-that-all-new-users-have-the-same-profile-settings-as-the-current-u](https://askubuntu.com/questions/186487/how-to-ensure-that-all-new-users-have-the-same-profile-settings-as-the-current-u)
 or
using NFS so that the directories for every user on every system are the same ... basically /home would be form 1 disk that is on the network.  Most places use LDAP for userid management when they have more than 5 users and 5 workstations to be shared. With LDAP and NFS home directories, whenever a user logins in on any of the workstations, their HOME is used. Very convenient.  It also means they can ssh into other machines and their HOME will be available there, highly convenient, provided the config files are setup so this works correctly.
 or
if these are guest users, there is a way to setup the defaults. [https://help.ubuntu.com/community/CustomizeGuestSession](https://help.ubuntu.com/community/CustomizeGuestSession)

The main issue with firefox is that profiles are created using random  names  as  a security measure.  If you hard code them, some level of security is reduced.

For firefox, you might just replace the firefox command with one that always opens the tabs?```

firefox -new-tab  [http://ubuntuforums.org/](http://ubuntuforums.org/) -new-tab  [https://www.duolingo.com/](https://www.duolingo.com/) -new-tab  [https://forecast.io/](https://forecast.io/)
```

This probably isn't  useful today.

---

### Post by joe.koenig on 2015-10-14
Hi kablizzo,

pardon my ignorance, but what is a "rat menu"?

---

### Post by kablizzo on 2015-10-14
> **TheFu said:**
>  ansible to automate HOME setup 
 
That seems like a powerful tool. I should learn it but for now it's over my head.

> **TheFu said:**
>  modify /etc/skel/ with whatever settings you want. [https://askubuntu.com/questions/186487/how-to-ensure-that-all-new-users-have-the-same-profile-settings-as-the-current-u ]("https://askubuntu.com/questions/186487/how-to-ensure-that-all-new-users-have-the-same-profile-settings-as-the-current-u")

This is exactly what I need! THANK YOU!!!!
 
> **TheFu said:**
>  The main issue with firefox is that profiles are created using random  names  as  a security measure.  If you hard code them, some level of security is reduced.

For firefox, you might just replace the firefox command with one that always opens the tabs?```

firefox -new-tab  [http://ubuntuforums.org/](http://ubuntuforums.org/) -new-tab  [https://www.duolingo.com/](https://www.duolingo.com/) -new-tab  [https://forecast.io/](https://forecast.io/)
``` 

I like the open-tabs-by-default solution as well. You, sir, deserve a beer! If you are ever in the Portland, OR area it's on me.

> **TheFu said:**
>  This probably isn't  useful today.

Very useful thank you so much!!

---

### Post by kablizzo on 2015-10-14
> **joe.koenig said:**
> Hi kablizzo,

pardon my ignorance, but what is a "rat menu"?

It's probaby not what the equivelant-to-a-start-menu is called in Xfce. But that's what I call it.

---

