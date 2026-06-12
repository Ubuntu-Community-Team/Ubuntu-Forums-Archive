---
title: "How do I enable remote login"
date: 2009-01-25
forum: General Help
---

### Post by Arukas on 2009-01-25
I have no clue, how do i enable remote login in xubuntu, I know how to do it in Ubuntu, but i don't see the option in Xubuntu

---

### Post by richlowe101 on 2009-01-25
[http://ubuntuforums.org/showthread.php?t=371248]("http://ubuntuforums.org/showthread.php?t=371248") Does this help?

---

### Post by Arukas on 2009-01-25
That does not help at all.  Infact, it backwards from what I do.  Second, if you don't understand the problem you shouldn't be posting random links that you think apply.  Grow up.


I want to enable remote log-in in Xubuntu, and I can't figure out where to do it at.  Does anyone know where it is?

---

### Post by Sub101 on 2009-01-25
Go to:
System ==> Preferences ==> Remote Login

From there you can set the settings as you need.

How do you want to connect to the system? Through another Linux or from Windows?

---

### Post by richlowe101 on 2009-01-25
> **Arukas said:**
> That does not help at all.  Infact, it backwards from what I do.  Second, if you don't understand the problem you shouldn't be posting random links that you think apply.  Grow up.

Is that not a bit harsh considering I'm only trying to help? First of all its not exactly a difficult problem to understand. Second of all you're not going to get far in life biting the hand that feeds you. In addition as I'm new to the forum this is not exactly the welcome I'd hoped for. Thankyou for making that experience a little less pleasurable.

I hope you get the answer you need.

---

### Post by adamlau on 2009-01-25
Yup, a bit harsh, Arukas. richlowe101 was only trying to help. The phrase "remote login" entails many scenarios. Assuming you have GDM installed, start with:

```
/usr/sbin/gdmsetup
```

---

### Post by Arukas on 2009-01-25
Just to point out Xubuntu "System ==> Preferences ==> Remote Login" doesn't work in Xubuntu.  That's an ubuntu thing.  

Thanks adamlau, gdmsetup was the thing.  

Just as a note, you may have to forgive me, but I don't think I was to harsh.  I just had all I could stand  in the rescent weeks, with the "I think this MIGHT help" and post random link with appropriate key words. 

I know how to do a search, however, everything I find isn't what I need.  So I ask, that's what a forum is for.

---

### Post by mckemie on 2011-02-06
> **Arukas said:**
> Just to point out Xubuntu "System ==> Preferences ==> Remote Login" doesn't work in Xubuntu.  That's an ubuntu thing.  

Thanks adamlau, gdmsetup was the thing.  

Just as a note, you may have to forgive me, but I don't think I was to harsh.  I just had all I could stand  in the rescent weeks, with the "I think this MIGHT help" and post random link with appropriate key words. 

I know how to do a search, however, everything I find isn't what I need.  So I ask, that's what a forum is for.

With 10.10, there is no "Remote Login" under Preferences.  Under 10.10, gdmsetup does not offer remote options.

---

