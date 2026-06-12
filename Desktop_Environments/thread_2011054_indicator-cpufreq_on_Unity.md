---
title: "indicator-cpufreq on Unity"
date: 2012-06-26
forum: Desktop Environments
---

### Post by KenSharp on 2012-06-26
Is it possible to use a widget with Unity?

[This]("http://kennystechtalk.blogspot.co.uk/2012/06/granola-testing.html") kind of explains why I need it.

I don't know if my CPU is stuck at full clock frequency (given it's running hot all the time I'm guessing it is). Is there another way I can check and **change** this if it's not possible to use the widget?

cpufreqd was automatically removed when I updated Natty --> Oneiric --> Precise and I don't want to install it again if there is something else that has replaced it.

TIA

---

### Post by Frogs Hair on 2012-06-26
The CPU scaling and frequency indicator is in the Ubuntu 12.04 software center.

---

### Post by KenSharp on 2012-06-26
It seems whatever Granola did, it has solved itself. Good! :)

---

### Post by KenSharp on 2012-06-26
Hmmm, okay, but in Natty I could control each processor individually. In Precise it's not clear if I'm controlling both processors at the same time, and there is no preferences menu.

It just so happens I would prefer to control both at the same time.

---

### Post by KenSharp on 2012-07-05
[https://bugs.launchpad.net/indicator-cpufreq/+bug/691721](https://bugs.launchpad.net/indicator-cpufreq/+bug/691721)

---

### Post by KenSharp on 2012-07-06
[https://bugs.launchpad.net/indicator-cpufreq/+bug/691721/comments/28](https://bugs.launchpad.net/indicator-cpufreq/+bug/691721/comments/28) answers my question!

---

### Post by Drupalizer on 2012-10-04
> **Frogs Hair said:**
> The CPU scaling and frequency indicator is in the Ubuntu 12.04 software center.

Yeah but it didn't work for me just kept crashing so I just found something that's works perfect " Jupiter "

```


sudo add-apt-repository ppa:webupd8team/jupiter
sudo apt-get update
sudo apt-get install jupiter


```

---

