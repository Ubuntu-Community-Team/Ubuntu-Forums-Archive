---
title: "Update to Gnome 3"
date: 2010-05-23
forum: Desktop Environments
---

### Post by G9M29 on 2010-05-23
Hello all
I've just installed Ubuntu 10.04 and I was wondering how can I update my Gnome to 3 even though it is still not released offic. 

Please tell me how Can i update it, I try once but it got all fu**** up and I reinstallled my Ubuntu, so please can someone tell my step by step, how can I do it :) 

tnx a lot.

---

### Post by wojox on 2010-05-23
You can't. To many dependency issues. Which is why it screwed up before.

You could install Gnome-Shell from the repo's.

---

### Post by sharath.puranik on 2010-05-23
**I would suggest that you dont do it and wait for a stable release, there is no saying what will happen to your OS. It's not stable enough for installation.**

If you insist on a tutorial:
Fist of all install build-dep (sudo apt-get install build-dep   This will install any necessary dependencies needed to successfully   compile and run gnome-shell.
```
  [I]
sudo apt-get build-dep  gnome-shell[/I] 

```Once you have installed all of the  required packages and libraries, open a terminal and type:
```

*sudo apt-get install gnome-shell*  This will  install Gnome-Shell. 

```Once installed, you can start Gnome-Shell  by typing the following command in a terminal:
```

*gnome-shell  --replace*  

```I suggest running it from a  guest  session, as it will ‘kill’ compiz, requiring you to manually restart it.
```

*compiz.real --replace*

```- thanks to d0od from omgubuntu.co.uk

---

