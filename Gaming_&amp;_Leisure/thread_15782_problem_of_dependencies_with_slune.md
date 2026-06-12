---
title: "problem of dependencies with slune"
date: 2005-02-16
forum: Gaming &amp; Leisure
---

### Post by crashd on 2005-02-16
Hi all, 
I was installing slune (I have ubuntu hoary upgrade to today), but I receive this log of problem with dependencies:

root@ubuntu:/home/crashd # apt-get install slune
Reading Package Lists... Done
Building Dependency Tree... Done
Alcuni pacchetti non possono essere installati. Questo pu voler
dire che  stata richiesta una situazione impossibile oppure, se
si sta usando la distribuzione "unstable", che alcuni pacchetti
richiesti non sono ancora stati creati o rimossi da incoming.

Poich  stata richiesta solo una singola operazione  molto facile che
il pacchetto semplicemente non sia installabile, si consiglia
di inviare un "bug report" per tale pacchetto.
Le seguenti informazioni possono aiutare a risolvere la situazione:

I seguenti pacchetti hanno dipendenze non soddisfatte:
  slune: Depends: python (< 2.4) ma 2.4-0ubuntu6 sta per essere installato
         Depends: python-openal (>= 0.1.4-4) ma non sta per essere installato
E: Pacchetto non integro

If I add python-openal for the installation, I receive:

root@ubuntu:/home/crashd # apt-get install slune python-openal
Reading Package Lists... Done
Building Dependency Tree... Done
Alcuni pacchetti non possono essere installati. Questo pu voler
dire che  stata richiesta una situazione impossibile oppure, se
si sta usando la distribuzione "unstable", che alcuni pacchetti
richiesti non sono ancora stati creati o rimossi da incoming.
Le seguenti informazioni possono aiutare a risolvere la situazione:

I seguenti pacchetti hanno dipendenze non soddisfatte:
  python-openal: Depends: python (< 2.4) ma 2.4-0ubuntu6 sta per essere installato
  slune: Depends: python (< 2.4) ma 2.4-0ubuntu6 sta per essere installato
E: Pacchetto non integro

Thanks!

---

### Post by crashd on 2005-02-19
You succeeded to install it?  I would have to do one signalling to bugzilla?

---

