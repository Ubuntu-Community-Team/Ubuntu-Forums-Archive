---
title: "Why freemind is in the repos?"
date: 2006-08-17
forum: Desktop Environments
---

### Post by Marcos.Rufino on 2006-08-17
Why freemind is in the repos if it didn't work? When I try to install it synaptic says it depends on libforms-java but this dependency is not available. I thought all the applications in the repos should easily install, with all their dependencies solved. This slipshod way of including new applications in the repos doesn't contribute to the credibility of the distro, I think.

I've tried to install freemind from its project website but the menu is a mess. The icon also doesn't appear.

---

### Post by Tomosaur on 2006-08-17
Uhm:
```

tom@tom-computer:~$ sudo apt-get install freemind
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package freemind

```

And I have all default repositories enabled. Are you sure you don't have any custom repositories enabled?

---

### Post by Lunar_Lamp on 2006-08-17
If you install an application yourself, you need to create the menu entry yourself using alacarte menu editor.

---

### Post by Marcos.Rufino on 2006-08-17
> **Tomosaur said:**
> Uhm:
And I have all default repositories enabled. Are you sure you don't have any custom repositories enabled?

You're right. I have the above in my source.list.
deb [http://eric.lavar.de/comp/linux/debian/](http://eric.lavar.de/comp/linux/debian/) experimental/
deb-src [http://eric.lavar.de/comp/linux/debian/](http://eric.lavar.de/comp/linux/debian/) experimental/

Thanks.

---

### Post by ardchoille on 2006-08-17
> **Marcos.Rufino said:**
> You're right. I have the above in my source.list.
deb [http://eric.lavar.de/comp/linux/debian/](http://eric.lavar.de/comp/linux/debian/) experimental/
deb-src [http://eric.lavar.de/comp/linux/debian/](http://eric.lavar.de/comp/linux/debian/) experimental/

Thanks.

Looks like you're using debian repos in Ubuntu. It's a really bad idea to use debian repos (or even debian .deb packages) in Ubuntu as it can break things. Your best bet is to stick with the official Ubuntu repos. If you need an app that isn't in the Ubuntu repos, look around for a .deb that was made for Ubuntu. If you can't find one, then you should compile the app yourself.

---

### Post by taurus on 2006-08-17
> **Marcos.Rufino said:**
> 
deb [http://eric.lavar.de/comp/linux/debian/](http://eric.lavar.de/comp/linux/debian/) experimental/
deb-src [http://eric.lavar.de/comp/linux/debian/](http://eric.lavar.de/comp/linux/debian/) experimental/

](*,) ](*,) ](*,)

---

### Post by hecato on 2006-08-17
I have downloaded and used freemind from the home site.. I have downloaded the full app (like 10Mb or little less) or something ike taht say... it have worked OK in 64-bits... ;).

---

