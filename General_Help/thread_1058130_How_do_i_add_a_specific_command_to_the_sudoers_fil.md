---
title: "How do i add a specific command to the sudoers files ?"
date: 2009-02-02
forum: General Help
---

### Post by Major_Kong on 2009-02-02
How i can add the "sudo apt-get -qy update" command to sudoers ?

---

### Post by cmnorton on 2009-02-02
What are you asking? Are you asking for the syntax or which editing tool to use? If you are asking which tool to use, enter

sudo visudo

and you'll get the file to edit. sudo gksudo will give you a graphical editor.

---

### Post by jerome1232 on 2009-02-02
> **Major_Kong said:**
> How i can add the "sudo apt-get -qy update" command to sudoers ?

As far as I know you can only dictate which program users can run with escalated privileges, not the exact command they can run.

---------

so in summary you can allow them to run apt-get as any other user, but you can't specify the exact options they are allowed to give apt-get.

---

### Post by Major_Kong on 2009-02-02
> **jerome1232 said:**
> As far as I know you can only dictate which program users can run with escalated privileges, not the exact command they can run.

---------

so in summary you can allow them to run apt-get as any other user, but you can't specify the exact options they are allowed to give apt-get.

Will it work if i "wrap" it in a script, and add the script to sudoers ?

---

### Post by jerome1232 on 2009-02-02
Sounds like a good idea to me!

I would try it and then test it to make sure it's working as expected.

---

### Post by Major_Kong on 2009-02-02
I think i'm going to look a bit harder. Adding a script to always be run in super user mode, might not be a good idea...

---

### Post by dagnabit dang doohickey on 2009-02-02
*apt-get update* is already one of the daily cron jobs.

---

### Post by Major_Kong on 2009-02-02
> **dagnabit dang doohickey said:**
> *apt-get update* is already one of the daily cron jobs.

Ok then. 

Some background:
The command i wanted to run is part of a bash script to check for avaliable updates, to be used by conky. (i'm running openbox, so no gnome update checks)

But if it's already a cron job, i guess i don't really need to run that part of the script.
Thanks for the help. :D

---

### Post by kerry_s on 2009-02-02
> **Major_Kong said:**
> Ok then. 

Some background:
The command i wanted to run is part of a bash script to check for avaliable updates, to be used by conky. (i'm running openbox, so no gnome update checks)

But if it's already a cron job, i guess i don't really need to run that part of the script.
Thanks for the help. :D

you only need to put the path to apt-get, example:

%users ALL=NOPASSWD: /path/to/apt-get

then in your script just use "sudo apt-get whatever"
as long as you start it with sudo your good to go.

i don't recommend it though, you should use a bash alias(alias u='sudo apt-get update') if your to lazy to type it out, but if your going to use a script in conky make sure you put a time on it or it will be run every time conky refreshes, that's a lot of overhead.

---

### Post by adamlau on 2009-02-02
I prefer the more traditional approach of:

```
visudo
%*group* ALL=(root) NOPASSWD:/path/to/script
groupadd *group* && gpasswd -a *username* *group*
```

Where *grou*p is your chosen group name and *username* is your chosen login name.

---

### Post by Major_Kong on 2009-02-03
> **kerry_s said:**
> you only need to put the path to apt-get, example:

%users ALL=NOPASSWD: /path/to/apt-get

then in your script just use "sudo apt-get whatever"
as long as you start it with sudo your good to go.

i don't recommend it though, you should use a bash alias(alias u='sudo apt-get update') if your to lazy to type it out, but if your going to use a script in conky make sure you put a time on it or it will be run every time conky refreshes, that's a lot of overhead.

I gave up on adding the command to sudoers. If it's already scheduled to run, i don't really need to run it.
Commented that part of the script (the update sources part), and just kept the line where it counts the avaliable updates.

---

