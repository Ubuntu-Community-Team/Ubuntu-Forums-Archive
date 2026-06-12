---
title: "Su Failure?!"
date: 2006-06-06
forum: Desktop Environments
---

### Post by TrendyDark on 2006-06-06
I recently installed Kubuntu to check out KDE and such, but I'm having a big problem. Anything that requires administrative mode is returning a "Su Failure". What's the deal? Any ideas/solutions?:confused:

---

### Post by aysiu on 2006-06-06
Can you post the output of this terminal command? ```
sudo aptitude update
```

---

### Post by Meads on 2006-06-06
use sudo command not just 'su'

---

### Post by TrendyDark on 2006-06-06
[QUOTE=aysiu]Can you post the output of this terminal command? ```
sudo aptitude update
```[/QUOTE]

```
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Reading package lists... Done
```

The problem I'm having is when I try to run Administrative Mode in applications (adjusting the time/date, etc.). It either doesn't work or says "Su Failure".

[QUOTE=Meads]use sudo command not just 'su'[/QUOTE]

I know that much, I've been using Ubuntu for a while now, 6+ months.

Edit: A quick question, should I have two seperate swap partitions for Ubuntu & Kubuntu?

---

### Post by aysiu on 2006-06-06
You need only one swap partition.

What's the output of ```
gksudo synaptic
```?

---

### Post by TrendyDark on 2006-06-06
I went ahead and reinstalled full Ubuntu and just did:

```
apt-get install kubuntu-desktop
```

switching between sessions seems to fix my problems and everything is working great (for now). Thanks for the help though!

---

