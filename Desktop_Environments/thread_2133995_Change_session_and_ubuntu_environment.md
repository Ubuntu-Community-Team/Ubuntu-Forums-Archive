---
title: "Change session and ubuntu environment"
date: 2013-04-09
forum: Desktop Environments
---

### Post by arashiko28 on 2013-04-09
Can I create another Ubuntu session with the Edubuntu environment? Just to keep things separated, work from personal. Including the programs :)

---

### Post by Frogs Hair on 2013-04-09
Edit: Yes but they won't be separate. All applications and files would be available from either session. (mis-read)  Dual booting would separate them, but you would have to reboot.
 ```
sudo apt-get install edubuntu-desktop 
```

---

### Post by arashiko28 on 2013-04-09
Thanks, but turns out it happened exactly what I didn't wanted to happen, I didn't wanted edubuntu software on my main session, but only on the new one, now I have even the edubuntu logo on the task bar instead of the ubuntu logo.

---

### Post by stinkeye on 2013-04-09
> **arashiko28 said:**
> Thanks, but turns out it happened exactly what I didn't wanted to happen, I didn't wanted edubuntu software on my main session, but only on the new one, now I have even the edubuntu logo on the task bar instead of the ubuntu logo.

If you want to get back to pure ubuntu, look here.
[**_[COLOR="#B22222"]Getting Back to a Pure Ubuntu[/COLOR]_**]("http://www.psychocats.net/ubuntu/pureubuntu")
*Note this is for 12.10. If your using 12.04, follow the link on that page.
**Just noticed there isn't an Edubuntu removal command for 12.04.

To get what you want I think you may have to dual boot.

---

### Post by arashiko28 on 2013-04-09
I realized that but kind of wanted to avoid it... well there's the new version coming up, might as well do it all together :D, thanks anyway.;)

---

### Post by pinballwizard on 2013-04-09
Reload with Ubuntu, and then use a VM with Edubuntu for the kids...

---

### Post by gnugen on 2013-04-10
I think this command should work to get your ubuntu desktop back:

> sudo apt-get install ubuntu-desktop

As for the edubuntu session, it uses Unity, so you can just install the Edubuntu educational packages from the Ubuntu Software Centre and create a new user account for personal use. However, you will probably still be able to access your programs from another user account.

---

