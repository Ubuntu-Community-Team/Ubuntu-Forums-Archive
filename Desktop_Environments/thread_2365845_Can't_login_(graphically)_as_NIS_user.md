---
title: "Can't login (graphically) as NIS user"
date: 2017-07-11
forum: Desktop Environments
---

### Post by samson-danziger on 2017-07-11
I have seen many other threads about being unable to login as a NIS user, but none of them really describe the problem I am having. Hopefully this is the correct place to be posting this question. 

I have already setup my desktop as a NIS client, and I have correctly setup autofs to mount my NIS user home directory, and from the terminal, I can login as that user. I can see that if I su into my NIS user account, I have all my files there. I.e the results of 

```
su samsond
ls
```

and

```
ssh samsond@some-server
ls
```

are the same. 

If I press Ctrl+Alt+F3 I can access a virtual terminal, and login as my NIS user. What I want to do is login as my user from the login screen, as in, rather that logging in as my local user, login as my NIS user. This was working last Friday, but when I tried it after a restart yesterday morning, can choose the user from the login screen, but after I type in my password, the screen goes black, it flashes a bit, and then goes back to the login screen. I believe it checks the password and accepts it, but after that it fails to load the desktop, and just goes back to the login screen. If I type the wrong password it says the password is incorrect. 

I am using Ubuntu Gnome 17.04 64bit. My kernel version is 4.10.0-26-generic. Display manager is gdm3.

---

