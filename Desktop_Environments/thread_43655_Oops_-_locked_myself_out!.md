---
title: "Oops - locked myself out!"
date: 2005-06-22
forum: Desktop Environments
---

### Post by pintong on 2005-06-22
Being the newbie I am, I ran chown on /usr/bin and now I can't run anything as root without getting the following kind of errors:

 "Failed to run /usr/sbin/synaptic as user root: Child terminated with 1 status."

Any ideas on how to correct this? I miss using Gnome :(

---

### Post by az on 2005-06-22
Lordy!  Lordy!  Lordy....

---

### Post by pintong on 2005-06-22
[QUOTE=azz]Lordy!  Lordy!  Lordy....[/QUOTE]
Hmmm, I tried that, but no luck. Any other suggestions? ;)

---

### Post by az on 2005-06-22
...I had to take a moment....

I am really sorry, but "he's dead, jim!"

---

### Post by az on 2005-06-22
It is really difficult to restore all the permissions/ownership in /usr/bin back to a secure state.  Perhaps someone else can think of al alternative to backing up your home folder and reinstalling...

Again, I am sorry.  The "Lordys" were to underline the severity of the problem, and not to make fun of you!  I apoligize if it seemed inappropriate...

---

### Post by bored2k on 2005-06-22
[QUOTE=azz]It is really difficult to restore all the permissions/ownership in /usr/bin back to a secure state.  Perhaps someone else can think of al alternative to backing up your home folder and reinstalling...

Again, I am sorry.  The "Lordys" were to underline the severity of the problem, and not to make fun of you!  I apoligize if it seemed inappropriate...[/QUOTE]
 Azz what if he logged as root through the security console and chown everything back ?


Oh and pintong, excuse azz, he's as real as they get ;).

---

### Post by pintong on 2005-06-22
[QUOTE=azz]It is really difficult to restore all the permissions/ownership in /usr/bin back to a secure state.  Perhaps someone else can think of al alternative to backing up your home folder and reinstalling...

Again, I am sorry.  The "Lordys" were to underline the severity of the problem, and not to make fun of you!  I apoligize if it seemed inappropriate...[/QUOTE]
Haha, no, they didn't seem inappropriate. I just figured this would be easier to solve than it probably is.

A fix would be nice, but the installation is only 2 days old, so all is not lost.

---

### Post by az on 2005-06-22
Well, you can get things to work, but if you get some ownerships wrong, you open yourself up to security vulnerabilities.

---

### Post by pintong on 2005-06-22
[QUOTE=bored2k]Azz what if he logged as root through the security console and chown everything back ?[/QUOTE]Hmm, where would this "security console" be?

---

### Post by pintong on 2005-06-22
> Well, you can get things to work, but if you get some ownerships wrong, you open yourself up to security vulnerabilities.Oh, well, I may have only chowned the folder, not all of its contents. Then again, I'm new to Linux and I'm not sure if there's even a difference.

---

### Post by bored2k on 2005-06-22
[QUOTE=pintong]Oh, well, I may have only chowned the folder, not all of its contents. Then again, I'm new to Linux and I'm not sure if there's even a difference.[/QUOTE]
 I meant recovery console..

---

### Post by desdinova on 2005-06-22
there is a difference  between chown a folder and the contents of it

heres what my /usr/bin looks like


 ls -al /usr | grep bin
drwxr-xr-x    2 root   root 36864 2005-06-22 22:14 bin
drwxr-xr-x    2 root   root  8192 2005-06-22 20:11 sbin

---

### Post by pintong on 2005-06-23
[QUOTE=desdinova]there is a difference  between chown a folder and the contents of it

heres what my /usr/bin looks like


 ls -al /usr | grep bin
drwxr-xr-x    2 root   root 36864 2005-06-22 22:14 bin
drwxr-xr-x    2 root   root  8192 2005-06-22 20:11 sbin[/QUOTE]
Thanks, but how do I change my /usr/bin to those read/write settings (remember, I'm new)? I'd guess I need to chmod them, but I'm not sure how to use chmod.

---

