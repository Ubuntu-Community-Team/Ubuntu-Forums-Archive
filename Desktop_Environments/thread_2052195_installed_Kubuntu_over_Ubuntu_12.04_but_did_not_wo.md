---
title: "installed Kubuntu over Ubuntu 12.04 but did not work"
date: 2012-09-02
forum: Desktop Environments
---

### Post by tehno 2 on 2012-09-02
I had Kubutnu 12.04 which was shot after installing updates and could not fix the problem. So I installed Ubuntu 12.04 from CD and I did not like the desktop and tried Edubuntu which I did not like either.
Then I decided to switch over to Kubuntu again and used this command to do that
> sudo apt-get install kde-full
the install went through and after restarting, it showed Kubuntu log in screen, but after signing in, it went to Edubuntu desktop environment.

Can some one help me to fix this problem.

Thanks

---

### Post by JRV on 2012-09-02
Try:
```

sudo apt-get install kubuntu-desktop

```

---

### Post by tehno 2 on 2012-09-02
> **JRV said:**
> Try:
```

sudo apt-get install kubuntu-desktop

```


I just did but it did not work as well,
Thanks for responding

---

### Post by timcredible on 2012-09-02
you might try cinnamon as the desktop, it's really nice

---

### Post by tartalo on 2012-09-02
In the screen where your user and password is asked, you must choose Kubuntu session.

Since you installed Kubuntu on top of Ubuntu, the greeter might be either LightDM (Ubuntu's default) or KDM (Kubuntu's default), I don't know.

If it's LightDM this session menu appears clicking the "engine" above the field where you enter your username, if it's KDM the session menu below that field.

I hope I explained myself.

EDIT: This is LightDM [http://cdn.shuffleos.com/wp-content/uploads/2011/11/lightdm-login-screen-mate.jpg](http://cdn.shuffleos.com/wp-content/uploads/2011/11/lightdm-login-screen-mate.jpg)

---

### Post by tehno 2 on 2012-09-02
Dear Tartalo,

Yes you did explain yourself and you did that very well.
I never thought of that.

Thanks to you and to all other responses

Problem solved

---

