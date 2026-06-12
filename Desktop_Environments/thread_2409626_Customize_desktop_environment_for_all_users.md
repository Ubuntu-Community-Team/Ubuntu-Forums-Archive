---
title: "Customize desktop environment for all users"
date: 2019-01-04
forum: Desktop Environments
---

### Post by computermichael on 2019-01-04
I am testing an Ubuntu Desktop deployment for production. Currently, I have five machines authenticating via a FreeIPA Server. Ideally I would like to customize the lock screen and make light modifications (moving taskbar, changing desktop picture, etc., nothing big) when a user logs in for the first time and the home folder is created for their account. I would also like to bypass the welcome window asking about Livepatch that shows up when you log in for the first time. Is there a configuration file storing the desktop template used for new profiles, or would I need to run a script to accomplish the above?

---

### Post by CatKiller on 2019-01-04
> **computermichael said:**
> Is there a configuration file storing the desktop template used for new profiles

The template for a new user's Home folder is /etc/skel.

---

### Post by computermichael on 2019-01-04
Any way I can move over the profile configuration from one account to /etc/skel without breaking things? I'm trying to find the configuration in home/[MyAccount]/.gconf but the folder is empty.

---

### Post by CatKiller on 2019-01-04
I don't see why not. You'd need to adjust anything that refers to the specific username. Anything that isn't included gets generated from the defaults - /etc/profile, maybe?

I don't use Gnome, so I can't help you with the specifics of how the desktop environment handles things.

Your experimentation won't break anything other than your test account, which is simple to add and remove as many times as necessary until you've tweaked the settings to your preference.

---

