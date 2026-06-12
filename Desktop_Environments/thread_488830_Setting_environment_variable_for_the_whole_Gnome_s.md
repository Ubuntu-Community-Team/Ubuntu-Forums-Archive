---
title: "Setting environment variable for the whole Gnome session"
date: 2007-06-30
forum: Desktop Environments
---

### Post by chicha on 2007-06-30
Hi all :)

Here is my problem :

I have several users on my computer. They all use KDE. I use Gnome ;).
I exported in my /etc/profile file the variable OOO_FORCE_DESKTOP=kde, so that it impacts all users.

I would like to override this variable for me only (OOO_FORCE_DESKTOP=gnome).
Putting "export OOO_FORCE_DESKTOP=gnome" into my .bashrc, .bash_profile or even .gnomerc (as I have seen in some posts) does not work.

What I want is when I launch OOO through the Gnome menu, this environment variable is set.
What I do not want : change the menu entry for OOO ;)

Is there a clean solution for my problem ?
Thank you very much for your help !

Cheers,
Chicha

---

### Post by ComplexNumber on 2007-06-30
you could put something like this in /etc/profile:

```
 if [ "$USER = <your username>" ]
set OOO_FORCE_DESKTOP=gnome
else
set OOO_FORCE_DESKTOP=kde
fi
```


i can't really test because there is only me on my system. i don't know if it will work or not, but it may be worth a try. there are conditional statements in there that say 'if user equals root, then  do this, else do that'. for example:
```
  if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
```

if you can find out your id, then you should be able to adopt the first bit of code in this post to suit

---

### Post by RedSquirrel on 2007-07-03
> **chicha said:**
> Hi all :)

Here is my problem :

I have several users on my computer. They all use KDE. I use Gnome ;).
I exported in my /etc/profile file the variable OOO_FORCE_DESKTOP=kde, so that it impacts all users.

I would like to override this variable for me only (OOO_FORCE_DESKTOP=gnome).
Putting "export OOO_FORCE_DESKTOP=gnome" into my .bashrc, .bash_profile or even .gnomerc (as I have seen in some posts) does not work.

What I want is when I launch OOO through the Gnome menu, this environment variable is set.
What I do not want : change the menu entry for OOO ;)

Is there a clean solution for my problem ?
Thank you very much for your help !

Cheers,
Chicha
Does it work if you use ~/.profile instead of the other ones you listed? You might want to give another name to your .bash_profile and see if having only .profile works.

---

