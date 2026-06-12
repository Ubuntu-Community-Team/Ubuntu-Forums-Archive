---
title: "Changing Environmental Variables Permanantly"
date: 2009-01-20
forum: General Help
---

### Post by colsandurz on 2009-01-20
I am trying to change an environmental variable, say PATH, in BASH.  If I do ```
$PATH=$PATH:/home
```the home directory will be added to the path.  But when I reboot my machine, it goes back to the default path.  I've also tried using the env command without success.  The only thing I can think of to do here is change something in the startup scripts (like init) but I'm not sure how to do this.

---

### Post by Ng Oon-Ee on 2009-01-20
> **colsandurz said:**
> I am trying to change an environmental variable, say PATH, in BASH.  If I do ```
PATH=PATH:/home
```the home directory will be added to the path.  But when I reboot my machine, it goes back to the default path.  I've also tried using the env command without success.  The only thing I can think of to do here is change something in the startup scripts (like init) but I'm not sure how to do this.
There's a few ways. If you're wanting this environment to change for you only, try editing ~/.profile

For all users, I'm not really sure. Only one user here on this laptop.

---

### Post by dcstar on 2009-01-20
> **colsandurz said:**
> I am trying to change an environmental variable, say PATH, in BASH.  If I do ```
PATH=PATH:/home
```the home directory will be added to the path.  But when I reboot my machine, it goes back to the default path.  I've also tried using the env command without success.  The only thing I can think of to do here is change something in the startup scripts (like init) but I'm not sure how to do this.

```
sudo gedit /etc/environment
```

---

### Post by ibutho on 2009-01-20
/etc/environment to make the changes global and ~/.bash_profile for an individual user.

---

### Post by Slim Odds on 2009-01-20
> **colsandurz said:**
> I am trying to change an environmental variable, say PATH, in BASH.  If I do ```
PATH=PATH:/home
```the home directory will be added to the path.  But when I reboot my machine, it goes back to the default path.  I've also tried using the env command without success.  The only thing I can think of to do here is change something in the startup scripts (like init) but I'm not sure how to do this.

This is not correct.

The correct way is:```
export PATH=$PATH:/home
```

To reference and environment variable you have to use $

And also use "export" to put it into the global environment

---

### Post by colsandurz on 2009-01-23
Oh yeah, I forgot about that.  I fixed it though.

---

