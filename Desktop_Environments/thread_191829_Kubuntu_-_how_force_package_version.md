---
title: "Kubuntu - how force package version ?"
date: 2006-06-08
forum: Desktop Environments
---

### Post by Chareos on 2006-06-08
Hi guys,

1st of all: kubuntu is *excellent*. Top class quality.

Now I'm trying to get accustomed with Adept (I always used synaptic) and I'm liking it a lot.
I miss just a feature: I don't find a way to force a packet version.

Is there something I'm missing ?


Thanks for any suggestions.

Fabio
Italy

---

### Post by aysiu on 2006-06-08
Adept is a crippled package manager. ```
sudo aptitude update
sudo aptitude install synaptic
``` Yes, even in Kubuntu.

---

### Post by Chareos on 2006-06-08
I hoped for a way in Adept.
Sure I still use Synaptic just for blocking versions, but I don't like renundant applications.
(and I prefer Adept...)

Thanks for your answer.

---

### Post by manzuk on 2006-06-20
I'm using Kubuntu right now. AFAIK Adept can't lock a package to a certain version. So I tried to lock them with Synaptic.
The problem is, although they appear in synaptic as locked, Adept (and also adept_updater wich is the default app to handle updates in Kubuntu) want to change them to a newer version, and that's what Im trying to prevent!!!

Does anyone know what I can do to solve this? I do really need to keep those packages in their current version, but also need to upate other packages... (and its a real pain to de-select the packages i want to keep everytime I run an update)

Thank u

---

### Post by aysiu on 2006-06-20
This is a bit extreme, but you can try ```
sudo aptitude remove adept
sudo aptitude update
sudo aptitude install update-notifier
``` I use KDE a lot, and I've never found Adept to offer what I need. I use either the command-line or Synaptic.

---

### Post by rogeriovinhal on 2006-07-19
If I install update-notifier it will work OK on KDE just like Adept does?
Becasue I like to have it looking for security updates, so I don't have to update it manually everytime, but I also don't like the idea of not having the hold option to ignore the packages I wish to keep the current version.

---

### Post by manzuk on 2006-07-19
Well, that's what I've done, and it's working great! (I also use Syanptic along with Adept for packages admin - I think someone should merge their features, don't u?)
Hope that helps

---

### Post by rogeriovinhal on 2006-07-19
I have installed synaptic and update-notifier, but when I lock some package with synaptic, it still keeps telling me to update them in update-notifier.

Isn't that wrong?

---

### Post by rogeriovinhal on 2006-07-20
?

---

