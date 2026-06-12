---
title: "Installing programs without a login"
date: 2009-06-11
forum: General Help
---

### Post by eljefe on 2009-06-11
My friend is doing an AFS type of  Scholarship thing in Costa Rica. Her Windows machine became infected and it was replaced with Ubuntu, Jalopy I think.

It has been set up so that when they boot up, there is NO login at all.

Is there any way that she can install stuff without having a login of any kind? She just wants to get skype running again so she can talk to her folks again.

She is an English speaker in a spanish speaking country with no Linux experience so things are a bit tougher: )
I set up a VM here with spanish language on Jalopy so I can at least instruct her coherently !

---

### Post by DGortze380 on 2009-06-12
> **eljefe said:**
> My friend is doing an AFS type of  Scholarship thing in Costa Rica. Her Windows machine became infected and it was replaced with Ubuntu, Jalopy I think.

It has been set up so that when they boot up, there is NO login at all.

Is there any way that she can install stuff without having a login of any kind? She just wants to get skype running again so she can talk to her folks again.

She is an English speaker in a spanish speaking country with no Linux experience so things are a bit tougher: )
I set up a VM here with spanish language on Jalopy so I can at least instruct her coherently !

There is a user name and password, it's jsut set to automatically log-in.

Yes, she can install skype, but it involves reseting a number of things. 

No offense, but the request sounds like she's bypassing some type of configuration (idk who did the install, or who owns the machine)... all I'll say is there is a password, it is needed to install skype. Use your imagination and google.

---

### Post by statistic on 2009-06-12
She must have a user that she is logging in as, even if it doesn't prompt her for a password at login. If you do get that password, you'll need to hope it has sudo priviledges.

If none of this is possible, you'll either need to contact whoever set it up for an administrator password, or if noone would mind then you could do what I think it is eljefe is hinting at.

Sorry if I'm wrong eljefe, but if you're hinting at what I think you're hinting at, I don't think it's at all sketchy to mention, it's up to the user if they wish to use it.

I think he's suggesting you google how to change the root password using the single user mode login. If you can't get into single user mode even, you can do more interesting things which would involve a live cd, mounting the hard drive manually changing the password in more creative ways.

If I really shouldn't be mentioning this then just edit my post, I don't think it's a bad thing to do.

---

### Post by eljefe on 2009-06-12
> **statistic said:**
> She must have a user that she is logging in as, even if it doesn't prompt her for a password at login. If you do get that password, you'll need to hope it has sudo priviledges.

If none of this is possible, you'll either need to contact whoever set it up for an administrator password, or if noone would mind then you could do what I think it is eljefe is hinting at.

Sorry if I'm wrong eljefe, but if you're hinting at what I think you're hinting at, I don't think it's at all sketchy to mention, it's up to the user if they wish to use it.

I think he's suggesting you google how to change the root password using the single user mode login. If you can't get into single user mode even, you can do more interesting things which would involve a live cd, mounting the hard drive manually changing the password in more creative ways.

If I really shouldn't be mentioning this then just edit my post, I don't think it's a bad thing to do.
Ah.. got ya, I was reading about it yesterday I think. The problem is we are not sure if the person who installed it (who is not at hand) even remembers the password. I am not sure if we want to do what is being alluded to either! If we cant get in touch with the "installer" soon we may have to revisit. Thanks guys : )

---

### Post by Legace on 2009-06-12
> **eljefe said:**
> Ah.. got ya, I was reading about it yesterday I think. The problem is we are not sure if the person who installed it (who is not at hand) even remembers the password. I am not sure if we want to do what is being alluded to either! If we cant get in touch with the "installer" soon we may have to revisit. Thanks guys : )


[http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/](http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/)

---

### Post by statistic on 2009-06-12
> **Legace said:**
> [http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/](http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/)

Ahh nice legace, I wasn't sure if using a chroot would work properly for changing passwords. Thanks for that.

---

