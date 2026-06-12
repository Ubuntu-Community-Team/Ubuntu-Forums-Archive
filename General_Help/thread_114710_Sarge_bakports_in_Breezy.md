---
title: "Sarge bakports in Breezy"
date: 2006-01-09
forum: General Help
---

### Post by sbaush on 2006-01-09
Hi all.
i've seen that sometimes the sarge version of a software is more stable than a ubuntu version. Is a good idea to put the debian sarge repository (deb [http://www.backports.org/debian/](http://www.backports.org/debian/) sarge-backports main) in the /etc/apt/sources.list?

I tried to add this line but a lot of software need update so I have remove the repository and ask to you before update!

Thanks to all!

Bye bye

---

### Post by gingermark on 2006-01-09
In a word, No. Dependency Hell will await if you permanently have a Debain repo enabled.

---

### Post by sbaush on 2006-01-09
so you suggest me to use this tip only for isolated packages, for example to upgrade firefox to 1.5 (this package is not in ubuntu-repository) and then remove the line form source.list

---

### Post by arnieboy on 2006-01-09
[QUOTE=sbaush]so you suggest me to use this tip only for isolated packages, for example to upgrade firefox to 1.5 (this package is not in ubuntu-repository) and then remove the line form source.list[/QUOTE]
firefox is not an isolated package. it will come with a million libs from the sarge repos and will bork your ubuntu libs. so dont do that.

---

### Post by sbaush on 2006-01-09
ok, it was an example...
I installed 1.5 from source when released!

---

### Post by mclien on 2006-01-15
Another question on this subject then:

I would like to add kmailcvt, for importing mail from a former system.
so what to do while this is not in the repositories?

(It is for sure not a single package)

---

### Post by arnieboy on 2006-01-15
[QUOTE=mclien]Another question on this subject then:

I would like to add kmailcvt, for importing mail from a former system.
so what to do while this is not in the repositories?

(It is for sure not a single packe)[/QUOTE]
check in the ubuntu repos. if its not there, compile from source.

---

### Post by mclien on 2006-01-15
[QUOTE=arnieboy]if its not there, compile from source.[/QUOTE]
Oh, what a nice tip for a distro ment to the beginners. :rolleyes:

---

### Post by arnieboy on 2006-01-15
[QUOTE=mclien]Oh, what a nice tip for a distro ment to the beginners. :rolleyes:[/QUOTE]
ubuntu is not for beginners. its merely beginner friendly in certain aspects. if u want an absolutely beginner's distro, try Mepis or Linspire.

---

### Post by mclien on 2006-01-15
[QUOTE=arnieboy]ubuntu is not for beginners. its merely beginner friendly in certain aspects. if u want an absolutely beginner's distro, try Mepis or Linspire.[/QUOTE]
OK, your point.

Now mine:
Is it 'best choice' not to have a tool for importing mail from other systems/ distros, if you want people to change to ubuntu? (and want touse KDE, perhaps)

BTW: it's included with sarge...

---

### Post by newuser111 on 2006-01-16
i can see kmailcvt in synaptic and all my repos are breezy

---

