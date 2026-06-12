---
title: "installing livestation"
date: 2008-12-31
forum: General Help
---

### Post by mistaboins on 2008-12-31
happy new year all!
i'm trying to install livestation on 8.10 and having no luck. here's the instructions from the website:



    * Your download should start in a moment.
    * Once the file has downloaded, start a terminal session and navigate to the folder you downloaded the file to.
    * Type chmod +x ./Livestation-[version].run
    * Type ./Livestation-[version].run
    * Press q to skip the readme
    * Press y to accept the terms
    * Follow the prompts to complete installation. You may need sudo access to write some files

here's what i get in terminal:
mistaboins@mistaboins-desktop:~$ chmod +x ./Livestation-[version].run
chmod: cannot access `./Livestation-[version].run': No such file or directory
mistaboins@mistaboins-desktop:~$ Livestation-2.1.0.run
bash: Livestation-2.1.0.run: command not found
mistaboins@mistaboins-desktop:~$ Livestation-2.1.0.run
bash: Livestation-2.1.0.run: command not found
mistaboins@mistaboins-desktop:~$ chmod +x ./Livestation-[2.5.0].run
chmod: cannot access `./Livestation-[2.5.0].run': No such file or directory
mistaboins@mistaboins-desktop:~$ chmod +x ./Livestation-2.5.0.run
chmod: cannot access `./Livestation-2.5.0.run': No such file or directory
mistaboins@mistaboins-desktop:~$ 

the file was in desktop,

---

### Post by fiddler616 on 2008-12-31
You don't actually type "chmod +x", you substitute the +X with a number...I don't know enough to tell you which one though (chmod lets you make something executable, and different numbers indicate different privileges for different people)

---

### Post by Ahadiel on 2008-12-31
> **fiddler616 said:**
> You don't actually type "chmod +x", you substitute the +X with a number...I don't know enough to tell you which one though (chmod lets you make something executable, and different numbers indicate different privileges for different people)

Actually 'chmod +x file' does work.

> **mistaboins said:**
> happy new year all!
i'm trying to install livestation on 8.10 and having no luck. here's the instructions from the website:



    * Your download should start in a moment.
    * Once the file has downloaded, start a terminal session and navigate to the folder you downloaded the file to.
    * Type chmod +x ./Livestation-[version].run
    * Type ./Livestation-[version].run
    * Press q to skip the readme
    * Press y to accept the terms
    * Follow the prompts to complete installation. You may need sudo access to write some files

here's what i get in terminal:
mistaboins@mistaboins-desktop:~$ chmod +x ./Livestation-[version].run
chmod: cannot access `./Livestation-[version].run': No such file or directory
mistaboins@mistaboins-desktop:~$ Livestation-2.1.0.run
bash: Livestation-2.1.0.run: command not found
mistaboins@mistaboins-desktop:~$ Livestation-2.1.0.run
bash: Livestation-2.1.0.run: command not found
mistaboins@mistaboins-desktop:~$ chmod +x ./Livestation-[2.5.0].run
chmod: cannot access `./Livestation-[2.5.0].run': No such file or directory
mistaboins@mistaboins-desktop:~$ chmod +x ./Livestation-2.5.0.run
chmod: cannot access `./Livestation-2.5.0.run': No such file or directory
mistaboins@mistaboins-desktop:~$ 

the file was in desktop,

You forgot to change to ~/Desktop
```
cd ~/Desktop
chmod +x Livestation-2.5.0.run
./Livestation-2.5.0.run

```

---

### Post by fiddler616 on 2008-12-31
> **Ahadiel said:**
> Actually 'chmod +x file' does work.
Oh. Thanks for the heads-up. *retreats to a corner in shame*

---

### Post by kitts on 2009-02-28
thnaks for the commands. i did it.

---

