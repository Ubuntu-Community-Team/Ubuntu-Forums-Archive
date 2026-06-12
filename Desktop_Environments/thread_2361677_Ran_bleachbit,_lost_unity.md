---
title: "Ran bleachbit, lost unity"
date: 2017-05-19
forum: Desktop Environments
---

### Post by UncleMonty on 2017-05-19
I am running ubuntu 16.04 LTS 64 bit. I ran bleachbit yesterday. Since then unity is not loading properly - I can only access files and folders, and have to load applications via terminal. What can I do to rectify this please?

---

### Post by RobGoss on 2017-05-19
Hello and welcome, try running the following command,

```
unity --reset
```

This should reset the Unity desktop, make sure you reboot to allow the changes 

I would look at Bleachbit and make sure you don't have anything checked that should not be deleted, I use Bleachbit and I also use Unity never had this issues before

---

### Post by Frogs Hair on 2017-05-19
For Unity versions after Ubuntu 12,04 use the following commands to reset compiz an Unity. Try reseting compiz first.

Reset Compz:

```
sudo apt-get install dconf-tools
``````
 dconf reset -f /org/compiz/
```

Reset Unity:

```
setsid unity
```

---

### Post by flocculant on 2017-05-19
> **UncleMonty said:**
> I am running ubuntu 16.04 LTS 64 bit. I ran bleachbit yesterday..... What can I do to rectify this please?

Next time I suggest that you take notice of what bleachbit says it is going to do, you run it with root rights.

If it said it was going to delete your next born would you just Enter?

**Read** what tools say they **will** do - the chances are the tool will do what is says - even more so when sudo or your first born is involved.

Losing Windows should never equate to losing your mind - ever.

---

### Post by UncleMonty on 2017-05-20
> **flocculant said:**
> Next time I suggest that you take notice of what bleachbit says it is going to do, you run it with root rights.

If it said it was going to delete your next born would you just Enter?

**Read** what tools say they **will** do - the chances are the tool will do what is says - even more so when sudo or your first born is involved.

Losing Windows should never equate to losing your mind - ever.

The moral of the story is never use Unity whilst tired!

---

### Post by UncleMonty on 2017-05-20
> **Frogs Hair said:**
> For Unity versions after Ubuntu 12,04 use the following commands to reset compiz an Unity. Try reseting compiz first.

Reset Compz:

```
sudo apt-get install dconf-tools
``````
 dconf reset -f /org/compiz/
```

Reset Unity:

```
setsid unity
```


Hi thanks, I tried this and it didn't work :s

---

### Post by RobGoss on 2017-05-20
> **flocculant said:**
> Next time I suggest that you take notice of what bleachbit says it is going to do, you run it with root rights.

If it said it was going to delete your next born would you just Enter?

**Read** what tools say they **will** do - the chances are the tool will do what is says - even more so when sudo or your first born is involved.

Losing Windows should never equate to losing your mind - ever.



We learn by trial and errors

---

### Post by deadflowr on 2017-05-20
> **UncleMonty said:**
> The moral of the story is never use Unity whilst tired!
Less unity and more bleachbit being something to play around with when tired is the problem.
> **UncleMonty said:**
> Hi thanks, I tried this and it didn't work :s
Might as well use a more robust way
I'd try installing ccsm from one of those terminals, if it's not installed already
```
sudo apt-get install compizconfig-settings-manager
```
then open; just type ccsm to open.
Then go to the unity plugin (the name changes sometimes, but should be something like Ubuntu unity plugin)
open it and in the left side you should be able to enable it.
Take whatever the default options it ask you to select (default options will be highlighted in orange,hard to explain but you'll understand when you see it)
It should reload unity, it'll seem like the screen is going bonkers for a minute, but just wait and do not do anything until it's set.
Bonus would be to check several other settings in ccsm as well, like move windows, resize windows, place windows, expo, viewport switcher, desktop wall and scale.
(scale less so than the others as unity depends on it, so when you enable unity scale should be auto-enabled)

After all that see how unity works then.

hope it helps. 
or make sense

---

### Post by LinuXXuniL on 2017-05-20
It is not a bleachbit problem, I have the same issues and I didn't ran bleach bit. I am stuck at the desktop wallpaper with no unity at all. Tried multiple workarounds but it looks nothing wants to restart unity, hmmm!

---

### Post by wildmanne39 on 2017-05-20
Please start your own thread so you can get the help you need, just because bleachbit may not be the cause of your problem does not mean it was not the cause of his.

Bleachbit has a bad habit of removing packages that are needed, I do not use it for that very reason.

---

### Post by LinuXXuniL on 2017-05-20
Indeed! Sorry!

---

### Post by wildmanne39 on 2017-05-20
No worries here.:)

---

### Post by deadflowr on 2017-05-20
> **LinuXXuniL said:**
> It is not a bleachbit problem, I have the same issues and I didn't ran bleach bit. I am stuck at the desktop wallpaper with no unity at all. Tried multiple workarounds but it looks nothing wants to restart unity, hmmm!

There is more than one way to skin a cat...
The Op skinned it one way.
You skinned it another.

---

### Post by LinuXXuniL on 2017-05-21
Yes sir! The thing is it happens to me for the 4th time, it is such a frustrating thing! I do not know why this is happening and it is strange I cannot fix it with what I have tried. At the end of all I've made an upgrade to 17.04 and that seems to work.

On the other hand I am pretty glad they will give up on Unity next year.

---

