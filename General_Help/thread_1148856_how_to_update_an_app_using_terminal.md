---
title: "how to update an app using terminal??"
date: 2009-05-04
forum: General Help
---

### Post by Ubu_linux on 2009-05-04
[FONT=Franklin Gothic Medium][SIZE=3]Hi everyone, this is my first post here, I just installed Ubuntu tweaks application, it asked me to update it, but it hangs, I wanna update the software using the terminal, the app called( ubuntu tweak), how can I do that!!

Cheers![/SIZE][/FONT]:guitar:

---

### Post by lemcoe9 on 2009-05-04
How did you install the program? Did you use apt-get or Synaptic? If so, you can just run:

```
sudo apt-get update
```

And if there is an update available, it will update it. 

If not, it would depend on how you installed it to begin with.

---

### Post by Tilex on 2009-05-04
> **Ubu_linux said:**
> [FONT=Franklin Gothic Medium][SIZE=3]Hi everyone, this is my first post here, I just installed Ubuntu tweaks application, it asked me to update it, but it hangs, I wanna update the software using the terminal, the app called( ubuntu tweak), how can I do that!!

Cheers![/SIZE][/FONT]:guitar:

Make sure the repositories (where the system fetches the packages) are uncommented in ```
/etc/apt/sources.list
```

Once you've taken out the "#", you may try to update the system with 
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install tweak

```

I'm not sure if "tweak" is the name of the package you are looking for, but hope that helps !

---

### Post by Ubu_linux on 2009-05-04
> **lemcoe9 said:**
> How did you install the program? Did you use apt-get or Synaptic? If so, you can just run:

```
sudo apt-get update
```And if there is an update available, it will update it. 

If not, it would depend on how you installed it to begin with.







Hi, 
I downloaded the the ubuntu tweak from a site, it was a debian application, and I installed it , I already used the method of sudo apt-get update, but every time I run the app , the update notifier pops up!
can I use a command in terminal, to update a specfic application?

---

### Post by Ubu_linux on 2009-05-04
> **Tilex said:**
> Make sure the repositories (where the system fetches the packages) are uncommented in ```
/etc/apt/sources.list
```Once you've taken out the "#", you may try to update the system with 
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install tweak

```I'm not sure if "tweak" is the name of the package you are looking for, but hope that helps !


hi, thanks

the program is already installed, I just need to update it by using the terminal.

Cheers

---

### Post by Tilex on 2009-05-05
Well if the program (package) in the repositories is not newer than the version installed, it won't propose you an update.

It is possible, however, that there exists a newer version in "the wild" compared to the one in the repositories.  In that case, you might need to download/install the package manually.

---

