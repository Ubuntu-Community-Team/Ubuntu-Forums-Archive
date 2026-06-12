---
title: "Ubuntu tweak 3rd party repos"
date: 2009-02-04
forum: General Help
---

### Post by Schok on 2009-02-04
I am using Ubuntu Tweak 0.4.4 on Ubuntu 8.10 64bit. Had a problem unlocking on the "Applications" tab. Everytime i try to unlock it says "Could not authenticate. An Unexpected Error has occured". How do i fix this?

I added a few third party softwares sources and when i update my ubuntu i had lots of stuff to update and my ubuntu warned me that i am about to "install softwares that can't be authenticated! Doing this could allow a malicious individual to damage or take control of you system"

Is it safe to update? How do i authenticate those sources?

---

### Post by Schok on 2009-02-05
bump. any help? in case anyone is wondering, here are the 3rd party repos i added:
1.OpenOffice.org
2.Skype
3.Firefox
4.Compiz Fusion
5.Gnome Do
6.Google
7.Ubuntu Tweak
8.Wine
9.Virtualbox(i am not using the OSE version btw)
10.Medibuntu

---

### Post by konqueror7 on 2009-02-06
some of them are save, but most of the repos there, if you read, are development repos...so it has a higher risk installing unstable applications...

also, i've added some repos from ubuntutweak, just update it, it usually ask for the root password...

also, some of those repos don't work, for example, i had a problem with the swiftweasel source...

---

### Post by Schok on 2009-02-06
Thanx for sharing the info~

---

### Post by BazookaAce on 2009-02-08
> **Schok said:**
> I am using Ubuntu Tweak 0.4.4 on Ubuntu 8.10 64bit. Had a problem unlocking on the "Applications" tab. **Everytime i try to unlock it says "Could not authenticate. An Unexpected Error has occured". **How do i fix this?

I added a few third party softwares sources and when i update my ubuntu i had lots of stuff to update and my ubuntu warned me that i am about to "install softwares that can't be authenticated! Doing this could allow a malicious individual to damage or take control of you system"

Is it safe to update? How do i authenticate those sources?

I'm having the same problem. How can i/we fix this? And does anybody have a complete list of all Intrepid Ibex sources?

---

### Post by practic on 2009-03-29
I was getting an authentication error with Ubuntu Tweak 4.6...which was strange because I was sure I had not gotten the error in the past.

Anyway, here's what I did:

Go to System -> Administration -> Authorizations

Under "com" look for "ubuntu-tweak", and under that, click on "Tweak"

If you are listed in the "Explicit Authorizations" box, click on the item and click the "Revoke" button.  Then click "Close".

Now try Ubuntu Tweak again.

---

### Post by BazookaAce on 2009-03-29
Thanks, but it doesn't work :(

---

### Post by matmat07 on 2009-06-08
Same problem here, I can't even find it in the autorization thing

---

### Post by BazookaAce on 2009-06-08
It's fixed here. The last update did the job. Remember to update.

---

### Post by matmat07 on 2009-06-08
I did and it's still there

---

### Post by BazookaAce on 2009-06-08
Hmm.. I really don't know what the problem is, since it just worked for me after updating. You can contact the developer of Ubuntu Tweak and ask him? :)

---

