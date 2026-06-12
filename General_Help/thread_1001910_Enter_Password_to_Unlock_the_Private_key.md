---
title: "Enter Password to Unlock the Private key"
date: 2008-12-04
forum: General Help
---

### Post by pronto185 on 2008-12-04
[IMG]http://pronto185.com/linux/screens/other/12_04_08_13:44:52window.png[/IMG]

How do I stop this from happing, it happens no matter where i ssh to >.<

its quite annoying.

i've tried my user acc password, root password :\

---

### Post by Normi on 2009-02-06
Enter the pass phrase used to generate the key.

---

### Post by _sAm_ on 2009-02-06
Its very annoying!

This is what I did; Open ~/.gnome2/keyrings 
Then I moved the file file called login.keyring to a new directory in the same place(as backup).  Next time I used ssh it asked me to enter a password - and I pressed enter(in other words no password). After that it don't ask me any more.

---

### Post by asbesto on 2009-02-10
But what the hell is this damn keyring? What's it's use? 

I use ssh, I have my ssh keys and password, I really don't understand why such a complication!

:confused:

---

### Post by Slim Odds on 2009-02-10
If you folks find security annoying, don't use any.

Geeezzzzz.

---

### Post by _sAm_ on 2009-02-11
> **asbesto said:**
> But what the hell is this damn keyring? What's it's use? 

I use ssh, I have my ssh keys and password, I really don't understand why such a complication!

:confused:

You can read about it here; [http://en.wikipedia.org/wiki/Seahorse_(software](http://en.wikipedia.org/wiki/Seahorse_(software))

---

### Post by asbesto on 2009-02-11
> **Slim Odds said:**
> If you folks find security annoying, don't use any.

Geeezzzzz.


I'm used to ssh and password security since 1991! 

What kind of improvement in security give me this incredible holocaust of programs and daemons, seahorse, gnome-keyring, gnome-keyring-daemon and so on? 

What is this, "Security thru Complexity" ?!?!?

This is MADNESS!

:confused:
(this - is - SPARTAAAAAAAAAAAAAAAAAAAAAA)


Really, I can't understand how a program and a daemon that intercept my ssh session under a shell, copying and "administrating" my keyrings into the damn gnome thing, can be a "Security improvement" for me.

:confused:

Is there a way to kill all this damn stuff? :(

---

