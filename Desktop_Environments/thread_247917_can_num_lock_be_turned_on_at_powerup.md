---
title: "can num lock be turned on at powerup"
date: 2006-08-31
forum: Desktop Environments
---

### Post by Emmett on 2006-08-31
I know how to turn numlock on in Kubuntu KDE settings but how can it be turned on when powering up my PC? Bios has it turned on but it is turned off when I log in.

Emmett

---

### Post by Malac on 2006-08-31
In adept look for numlockx

---

### Post by cstudent on 2006-08-31
```

sudo apt-get install numlockx

```

---

### Post by ebash on 2006-08-31
To turn on numlock at the GDM prompt, the screen that asks you for your login/password do the following:

After installing xnumlock you edit the file /etc/gdm/Init/Default

And add at the end, just before the 'exit 0', the following code:
```

#
# Set numlock on
#
if [ -x /usr/bin/numlockx ] ; then
        /usr/bin/numlockx on
fi

exit 0

```

---

### Post by Emmett on 2006-08-31
> **ebash said:**
> To turn on numlock at the GDM prompt, the screen that asks you for your login/password do the following:

After installing xnumlock you edit the file /etc/gdm/Init/Default

And add at the end, just before the 'exit 0', the following code:
```

#
# Set numlock on
#
if [ -x /usr/bin/numlockx ] ; then
        /usr/bin/numlockx on
fi

exit 0

```

That may work for gdm but what would the file be kdm? 

I looked at /etc/kde3/kdm but I still not sure which file it might be.

Thanks for the quick answers.

Emmett

---

### Post by Emmett on 2006-08-31
ebash Thank you for the gdm filename. 

By telling me the gdm filename I found the file kdmrc in /etc/kde3/kdm which allowed me to change the default to on.

Emmett

---

