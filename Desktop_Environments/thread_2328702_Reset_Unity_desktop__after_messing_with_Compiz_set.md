---
title: "Reset Unity desktop  after messing with Compiz settings  on 16.04"
date: 2016-06-23
forum: Desktop Environments
---

### Post by expatver on 2016-06-23
I have done a search here and what I have been able to find so far has been for pre 16.04 versions of Ubuntu. 

Before messing about with  compiz much more I wanted to verify if..... with Tweak Tool installed, the command

unity-tweak-tool --reset-unity

will work from CLI with a non functioning  desktop i.e clear  conflicting compiz things that break the desktop beyond functionality.........
From this thread

[https://askubuntu.com/questions/17610/how-do-i-reset-my-unity-configuration](https://askubuntu.com/questions/17610/how-do-i-reset-my-unity-configuration)

 Been there before with other Linuxes and trying to be armed beforehand.

Thanks

Expat

---

### Post by QDR06VV9 on 2016-06-23
Another method to reset the the configuration run this:

```
dconf reset -f /org/compiz/

```
Then, to reset unity run:

```
setsid unity
```

And you can reset Unity, **wiping all changes to configuration using Unity** Tweak Tool.

```
sudo apt-get install unity-tweak-tool
unity-tweak-tool --reset-unity

```

---

### Post by expatver on 2016-06-23
Runrickus

Many kind thanks for this! Excellent CLI help.

Now I will copy it to the tablet before proceeding further with Compiz fun.

As an aside, like the Dalai Lama quote very much. Agree  completely. 

Regards

Expat

---

### Post by QDR06VV9 on 2016-06-23
Your Very Welcome!:)
And Thanks for the sentiment.
Best Regards

---

### Post by carvalhana on 2017-03-07
Thank you very much!
I was having the same issues too...
Now it's SOLVED!!!!
Thanks
:popcorn:

---

