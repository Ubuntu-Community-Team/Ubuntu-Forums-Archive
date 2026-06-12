---
title: "Is there any way I can setup PATH and CLASSPATH variables"
date: 2006-11-22
forum: Desktop Environments
---

### Post by SwaroopKunduru on 2006-11-22
Hi All,

I am setting my PATH and CLASSPATH variables in my .bash_profile and they donot work. Where else should I set these variables.

Regards,

Swaroop Kunduru.

---

### Post by ciscosurfer on 2006-11-22
Let's say your PATH variable, viewable in a terminal by entering in **evn** or **printenv** or **echo $PATH** if you just want to see your path.

You can edit your .bash_profile either via the command line (using vi or nano, for example) or from the GUI (using GEdit or Kate, for exaple).

Let's say your .bash_profile setup looks something like this:
```
PATH=$PATH:$HOME/bin
```And you want to add /usr/local/bin to your path, you would add it like this:```
PATH=$PATH:/usr/local/bin:$HOME/bin
```Now, save the file and logout.

The next time you login, your new directory path will be set in your $PATH.  

Another way to do this without logging out and then back in is to issue the following in a terminal:```
source .bash_profile
```You'll now be able to run commands that originate from the directory you set in your $PATH without having to enter its absolute name.

---

### Post by scxtt on 2006-11-22
as far as i can remember, .bash_profile will only be sourced when connecting to a login shell (i.e. SSHing into your box from another box) - but if you're just opening a new shell from an X session, it won't be ... so i'd put something like **PATH=$PATH:<whatever>** and **CLASSPATH=$CLASSPATH:<whatever>** in ~/.bashrc if you want that kinda performance ...

---

### Post by ciscosurfer on 2006-11-22
> **scxtt said:**
> as far as i can remember, .bash_profile will only be sourced when connecting to a login shell (i.e. SSHing into your box from another box) - but if you're just opening a new shell from an X session, it won't be ... so i'd put something like **PATH=$PATH:<whatever>** and **CLASSPATH=$CLASSPATH:<whatever>** in ~/.bashrc if you want that kinda performance ...Not sure about that :-k

---

### Post by scxtt on 2006-11-22
> **ciscosurfer said:**
> Not sure about that :-kthat's fine :p ...

i've seen this question before (on this forum) and i did some testing to come to that conclusion ...

---

### Post by Peepsalot on 2006-11-22
> **scxtt said:**
> as far as i can remember, .bash_profile will only be sourced when connecting to a login shell (i.e. SSHing into your box from another box) - but if you're just opening a new shell from an X session, it won't be ... so i'd put something like **PATH=$PATH:<whatever>** and **CLASSPATH=$CLASSPATH:<whatever>** in ~/.bashrc if you want that kinda performance ...
edit: Nevermind, I'm just confusing myself.  I'm just going to say that I agree with scxtt

---

### Post by ciscosurfer on 2006-11-22
> **scxtt said:**
> that's fine :p ...

i've seen this question before (on this forum) and i did some testing to come to that conclusion ...Sourcing .bash_profile from a current login session works for me.  Logging out and then back in again also works for me.

---

### Post by scxtt on 2006-11-23
yeah, **_if_** you source it ... that wasn't the issue we were discussing above - if you just edit it and open a shell w/in the GUI ...

---

### Post by ciscosurfer on 2006-11-24
> **scxtt said:**
> yeah, **_if_** you source it ... that wasn't the issue we were discussing above - if you just edit it and open a shell w/in the GUI ...But that's the point -- you either need to source the file from within your current session, or log out and log in to accomplish the task.

To what issue were you referring above (opening a shell within a GUI -- I don't think that what the OP was asking...)

---

### Post by scxtt on 2006-11-24
> **ciscosurfer said:**
> But that's the point -- you either need to source the file from within your current session, or log out and log in to accomplish the task.

To what issue were you referring above (opening a shell within a GUI -- I don't think that what the OP was asking...)yes, neither way was explicitly stated - IMO it's safe to assume the OP was setting those variables, opening a non-login shell and expecting it to work ...

no one (esp. me) was saying "Sourcing .bash_profile from a current login session works for me." WOULDN'T work ...

---

