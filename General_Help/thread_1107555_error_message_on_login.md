---
title: "error message on login"
date: 2009-03-26
forum: General Help
---

### Post by godneal on 2009-03-26
Ok before i start i will say that i have been useing ubuntu for three weeks and will love it till the day that i die anyway im compleatly new to Ubuntu  and all that stuff and i messed up so now its time to learn how to fix the problem. anyway i was trying to make my home folder accessible on the network because i have three work computers all with completely different resources so i tinkered in the permissions on my home directory and now i get this error when i log in

$Home/.dmrc file is being ignored.  this prevents the default session and language form being saved.  File should be owned by user and have 644 permissions.  User's $Home directory must be owned bu user and not writable by other users

Things i have already tried
1 Changed all the settings back the way i found them. Problem was they dont stay changed.  Once i close they go back to the settings i put on there and i still get the error listed above,

2.  
neal@game-desktop:~$ USER=`whoami`
neal@game-desktop:~$ sudo chown -R ~ $USER:$USER
chown: invalid user: `/home/neal'
neal@game-desktop:~$ neal=`whoami`
neal@game-desktop:~$ sudo chown -R ~ neal:neal
chown: invalid user: `/home/neal'

---

### Post by absolutezero1287 on 2009-03-26
> **godneal said:**
> Ok before i start i will say that i have been useing ubuntu for three weeks and will love it till the day that i die anyway im compleatly new to Ubuntu  and all that stuff and i messed up so now its time to learn how to fix the problem. anyway i was trying to make my home folder accessible on the network because i have three work computers all with completely different resources so i tinkered in the permissions on my home directory and now i get this error when i log in

$Home/.dmrc file is being ignored.  this prevents the default session and language form being saved.  File should be owned by user and have 644 permissions.  User's $Home directory must be owned bu user and not writable by other users

Things i have already tried
1 Changed all the settings back the way i found them. Problem was they dont stay changed.  Once i close they go back to the settings i put on there and i still get the error listed above,

Try this:
sudo chown -R ~ `whoami`:`whoami`

---

### Post by karlr42 on 2009-03-26
I don't think that will work, you're calling whoami with root privileges..
```
$  sudo whoami 
root

```
And you definitely don't want your $HOME owned by root :)

---

### Post by absolutezero1287 on 2009-03-26
> **karlr42 said:**
> I don't think that will work, you're calling whoami with root privileges..
```
$  sudo whoami 
root

```
And you definitely don't want your $HOME owned by root :)

Wow...that was a really dumb mistake on my part. Good thing you caught that!

```

USER=`whoami`
sudo chown -R ~ $USER:$USER

```

---

### Post by godneal on 2009-03-27
This is what i get when i run the commands in the terminal.
and no changes are actualy made when i run this




neal@game-desktop:~$ USER=`whoami`
neal@game-desktop:~$ sudo chown -R ~ $USER:$USER
chown: invalid user: `/home/neal'
neal@game-desktop:~$ neal=`whoami`
neal@game-desktop:~$ sudo chown -R ~ neal:neal
chown: invalid user: `/home/neal'

and thank you all for your help

---

### Post by godneal on 2009-03-27
ok it just got worse i was able to install software with the software manager. this is the error i get



Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

help what do i do it was working a second ago and i have already had to reinstall ubuntu to fix another problem and i really dont want to have to do that again but will if i cannot find a solution.


ok app installer fixed ran synaptic and found one broken package i selected filter by broken mark for reinstall and then ran the update manager and it reinstalled the packages that were broken login problem still here just not the installer

---

### Post by absolutezero1287 on 2009-03-27
> **godneal said:**
> This is what i get when i run the commands in the terminal.
and no changes are actualy made when i run this




neal@game-desktop:~$ USER=`whoami`
neal@game-desktop:~$ sudo chown -R ~ $USER:$USER
chown: invalid user: `/home/neal'
neal@game-desktop:~$ neal=`whoami`
neal@game-desktop:~$ sudo chown -R ~ neal:neal
chown: invalid user: `/home/neal'

and thank you all for your help

No problem.

It looks like your user is "neal". So do this:
```

sudo chown -R ~ neal:neal

```
neal=`whoami` is not correct.

---

### Post by snova on 2009-03-27
> **absolutezero1287 said:**
> No problem.

It looks like your user is "neal". So do this:
```

sudo chown -R ~ neal:neal

```
neal=`whoami` is not correct.

I don't think that will quite do it either, as the username has to come first. :)

In a nutshell, this should work:

```
sudo chown neal:neal ~ -R
chmod 644 ~/.dmrc
```

The first command could take a while, depending on how many files you have.

---

### Post by absolutezero1287 on 2009-03-28
I've used the chown command many times. I don't know how I made such a simple mistake! :lolflag:
Good thing you came along!

---

