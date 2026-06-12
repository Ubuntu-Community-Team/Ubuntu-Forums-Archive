---
title: "How can I have GDM login screen remember my username?"
date: 2009-06-23
forum: General Help
---

### Post by CheeseEatingBulldog on 2009-06-23
We are running a pilot in a company and as users have to enter a domain and their userid each time they are presented with the login screen, I would like the username to be cached/remembered. I do not mean auto login, but rather that when the login screen appears it already has a userid filled in. Any ideas?

---

### Post by celticbhoy on 2009-06-23
I dont know how to achieve what you are asking, but could you not setup with a face browser login screen so that it is only a mouse click to select?

---

### Post by CheeseEatingBulldog on 2009-06-23
That would show all users on system, and I rather not have that.

---

### Post by celticbhoy on 2009-06-23
Not if you use the include/exclude box's in the user tab.

---

### Post by CheeseEatingBulldog on 2009-06-23
Is there really no other option? And do you mean include/exclude option is available in gdmsetup?

---

### Post by celticbhoy on 2009-06-23
If you start your login window preferences, and click on the user tab you will see that the include all users box in checked by default. If you uncheck this you select which users will appear in the face browser, then just give the user some generic corporate logo as the pic. I dont know if what you originally asked can be done or not, I was just giving you an option if cant find the answer you are looking for.

---

### Post by ikt on 2009-06-23
> **CheeseEatingBulldog said:**
> Is there really no other option? And do you mean include/exclude option is available in gdmsetup?

I believe there would be an option, I just don't think there is someone here to answer your question.

Possibly open a question on launchpad.

---

### Post by CheeseEatingBulldog on 2009-06-23
Yes and I appreciate the help, if nothing else can be found then I guess this is the only option. I just wanted to keep the original login as we are installing quite a few machines, so any added labour of setting up another login gdm (the standard ones for face are fugly) is a pain.

---

### Post by celticbhoy on 2009-06-23
How many machines? Are they all they same?

---

### Post by regala on 2009-06-23
> **ikt said:**
> I believe there would be an option, I just don't think there is someone here to answer your question.

Possibly open a question on launchpad.

or on a gnome user mailing, as it is where the REAL DEAL is.
it would anyway be a waste of time to open a 60000th bug on Launchpad, as it would be triaged along thousands of other ones in the next Triage Day...

---

### Post by CheeseEatingBulldog on 2009-06-23
> **celticbhoy said:**
> How many machines? Are they all they same?

Initial pilot is say 30 machines and intended is a 500+ rollout.

---

### Post by celticbhoy on 2009-06-23
I'm not sure of the name of the package I will look and get back though, but there is a util that allows you to exact copy the full hard disk. So the idea being you do one full install and setup then copy accross to all other machines. hopefully saving a bit of time.

---

### Post by CheeseEatingBulldog on 2009-06-23
> **celticbhoy said:**
> I'm not sure of the name of the package I will look and get back though, but there is a util that allows you to exact copy the full hard disk. So the idea being you do one full install and setup then copy accross to all other machines. hopefully saving a bit of time.

That would be really usefull, at the moment we are working with scripts. So a standard install and then running 2-3 scripts to install/change stuff. Would be nice to be able to make an "image" livecd / install cd. Cheers if you can find it.

---

### Post by celticbhoy on 2009-06-23
[http://wiki.freaks-unidos.net/mirror%20a%20linux%20installation](http://wiki.freaks-unidos.net/mirror%20a%20linux%20installation)

You can try looking at that, but its not what I am thinking of - still looking

---

### Post by celticbhoy on 2009-06-23
And this :-

[http://ubuntuforums.org/showthread.php?t=688872&highlight=hard+disk+copy](http://ubuntuforums.org/showthread.php?t=688872&highlight=hard+disk+copy)

and here :-

[http://ubuntuforums.org/showthread.php?t=581680&highlight=hard+disk+copy](http://ubuntuforums.org/showthread.php?t=581680&highlight=hard+disk+copy)

---

### Post by CheeseEatingBulldog on 2009-06-23
> **celticbhoy said:**
> And this :-

[http://ubuntuforums.org/showthread.php?t=688872&highlight=hard+disk+copy](http://ubuntuforums.org/showthread.php?t=688872&highlight=hard+disk+copy)

and here :-

[http://ubuntuforums.org/showthread.php?t=581680&highlight=hard+disk+copy](http://ubuntuforums.org/showthread.php?t=581680&highlight=hard+disk+copy)

Thanks for that! Will definity try that out. Also very useful for a backup usb drive for users who somehow B0rk their install.

---

### Post by celticbhoy on 2009-06-23
If you end up with 500 installs I think that a few live disks spread about would be quite handy

---

### Post by xatnet on 2009-06-23
It would appear this has been incorporated into GDM 2.22 Ubuntu has 2.20 though.
 
[https://bugs.launchpad.net/gdm/+bug/264553](https://bugs.launchpad.net/gdm/+bug/264553)

---

### Post by celticbhoy on 2009-06-23
Karmic has 2.27.3, and this option doesn't appear in the login config.

---

### Post by ikt on 2009-07-04
> **regala said:**
> 
it would anyway be a waste of time to open a 60000th **bug** on Launchpad, as it would be triaged along thousands of other ones in the next Triage Day...

I said **question**, not bug.

---

