---
title: "keeps asking for xubuntu cd"
date: 2009-05-22
forum: General Help
---

### Post by Zom-b on 2009-05-22
I have been trying to update my system, but it keeps poping up telling me to put xubuntu 9.04 in my cdrom, I am upgrading from ubuntu 8.04 to ubuntu 9.04 I don't know why it's asking me for the cd rom?

---

### Post by wpshooter on 2009-05-22
Try going into software sources and unchecking the box for installing updates from Ubuntu CD.

---

### Post by Zom-b on 2009-05-23
that will have to wait, because I dont' know how to do that from ttyl1 and currently my computer is acting up and only letting me into ttyl1 T-T

---

### Post by Zom-b on 2009-05-23
alright, how do I do that from either, terminal, or aptitude?

---

### Post by taurus on 2009-05-23
```
sudo nano -Bw /etc/apt/sources.list
```
and place a # in front of the entry for cdrom (usually the first line).  Save it and exit with <Ctrl>x.

Then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Zom-b on 2009-05-23
also, I am in aptitude, and it says it can't resolve archive.ubuntu.com or security.ubuntu.com or de.archive.ubuntu.com

---

### Post by Zom-b on 2009-05-23
> **taurus said:**
> ```
sudo nano -Bw /etc/apt/sources.list
```
and place a # in front of the entry for cdrom (usually the first line).  Save it and exit with <Ctrl>x.

Then run

```
sudo apt-get update
sudo apt-get upgrade
```

alright, after I saved and exit, I try doing the update, and it fails to update, going through everything saying it can't be resolved and finally telling me 

```

W: Some index files failed to download, they have been ignored, or older ones used instead.
W: You may want to run apt-get update to coreect these problems

```

but even then it hasn't used any of the sources at all.

---

### Post by Zom-b on 2009-05-23
alright I tried 
```

sudo apt-get upgrade

```

and that still didn't work, so then I tried

```

sudo apt-get update --fix-missing

```

and that seems to be doing something, I have my fingers crossed

because before when I did that it refused to work, so maybe getting rid of that cdrom upgrade may have been the fix I needed

---

### Post by taurus on 2009-05-23
Post the whole output of this command.

```
sudo apt-get update
```
Is your network working?  Do you have to configure proxy to access the net?

---

### Post by Zom-b on 2009-05-24
> **taurus said:**
> Post the whole output of this command.

```
sudo apt-get update
```
Is your network working?  Do you have to configure proxy to access the net?

I can't really do that, because the computer I am using is my fiances computer and the one I'm trying to get working is my, so I can't really post the output, I had to go into recovery mode and use the root to mess with it, but it more or less when through the entire source.list and said it couldn't fetch any of the links, then would say it couldn't resolve them

it's still going through the apt-get upgrade --fix-missing,
if that doesn't work I will take a picture of the screen and upload it

as for if my network is working, I don't know, but if I'm just in root, I would assume it's not.

---

### Post by Zom-b on 2009-05-24
hehe if nothing else the fact that my laptop keep messing stuff up is a great way to learn ubuntu via the school of hardknocks. which seems to be the best way of doing it, at least it gives me a reason not to procrastinate on doing stuff lol

---

### Post by Zom-b on 2009-05-24
here's the output for what it says when I do ```
apt-get update
```

this is probably because I don't have internet correct? how would I check that?

---

### Post by Zom-b on 2009-05-24
> **Zom-b said:**
> here's the output for what it says when I do ```
apt-get update
```

this is probably because I don't have internet correct? how would I check that?

alright, I connected a cat5 cable from my router to my laptop and did a update
and am doing an upgrade also, hopefully -this- is the end of this problem...

---

### Post by Wiley Hunter on 2009-05-24
One thing that I've not seen posted here yet (and I just did some upgrades from 8.04 LTS to 9.04 over the weekend) is that you must upgrade to 8.10 then 9.04.  Not sure WHY, but that is what I came across while I was doing mine.  I had to go to Software Sources (in 'System'/'Admin') then the 'Updates' tab, at the bottom of that tabbed screen is 'Release Update' click the dropdown arrow and select 'Normal Releases'.  Then you will have to sit through both updates (which on my DSL took about 2-1/2 hours or so total).

Good luck (hope something here helps ya)

Wiley

---

### Post by Zom-b on 2009-05-24
> **Wiley Hunter said:**
> One thing that I've not seen posted here yet (and I just did some upgrades from 8.04 LTS to 9.04 over the weekend) is that you must upgrade to 8.10 then 9.04.  Not sure WHY, but that is what I came across while I was doing mine.  I had to go to Software Sources (in 'System'/'Admin') then the 'Updates' tab, at the bottom of that tabbed screen is 'Release Update' click the dropdown arrow and select 'Normal Releases'.  Then you will have to sit through both updates (which on my DSL took about 2-1/2 hours or so total).

Good luck (hope something here helps ya)

Wiley

well that's how I was doing it, but somewhere along the line it really messed up and I have been trying to fix it since lol

---

