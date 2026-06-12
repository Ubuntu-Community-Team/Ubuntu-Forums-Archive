---
title: "problem after attempting java install"
date: 2009-04-29
forum: General Help
---

### Post by tentaro on 2009-04-29
Using software manager (Kpackagekit) to install java 6 and it stalled on an unknown error. I couldn't report it since it was java so now when I try to do anything in the software manager I get in the attachment. I am not sure how to fix this since this as far as I know the Kubuntu equivalent of Synaptic and I am not sure what I am supposed to do with apt since I don't know exactly what is messed up.

---

### Post by Thelasko on 2009-04-29
What happens if you run```
sudo apt-get install sun-java6-jre
```?

---

### Post by tentaro on 2009-04-29
This is the best community online by far.

Thank you for the quick reply. It worked well. I got this:

```
tentaro@tentaro-desktop:~$ sudo apt-get install sun-java6-jre
[sudo] password for tentaro:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-13-1) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-13-1) but it is not going to be installed
  sun-java6-plugin: Depends: sun-java6-bin (= 6-13-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
tentaro@tentaro-desktop:~$
```

I ran the -f install and all is well with the world now. Thanks again for the quick reply. Now if I can just get games to render  in WIne properly. I will be in heaven....lol

---

### Post by Thelasko on 2009-04-29
> **tentaro said:**
> I ran the -f install and all is well with the world now. Thanks again for the quick reply.

Well I believe "-f" stands for force.  I'm a little worried that there is something else wrong with your system, and using force install only fixed a symptom.

P.S. It appears that [this is common]("http://www.debian.org/doc/manuals/apt-howto/ch-erros.en.html") and apt-get -f install should have fixed it.  If it happens again, post here.

---

