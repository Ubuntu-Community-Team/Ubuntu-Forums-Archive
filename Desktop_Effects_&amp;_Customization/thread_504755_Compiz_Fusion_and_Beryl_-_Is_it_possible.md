---
title: "Compiz Fusion and Beryl - Is it possible?"
date: 2007-07-19
forum: Desktop Effects &amp; Customization
---

### Post by maduranga on 2007-07-19
I want to install new themes such as transparent effect for windows decorators and a good looking gnome panel. But currently i'm using Compiz Fusion. Are there any built-in function in Compiz Fusion that i can make my windows decorators transparent? or do i have to install a separate program to do that?   maybe beryl or something.

---

### Post by Espreon on 2007-07-19
Yes do this:

```
sudo apt-get install beryl-manager emerald emerald-themes libemeraldengine0 beryl
```

Then goto System>Administration>Sessions

and hit new then for the name , name it Beryl Manager, then for the command type beryl-manager

Now goto Applications>System Tools>Beryl Manager

Now right-click the Ruby icon and select the wm to be Compiz
Now select the Window decorator to be Emerald, and voila!

---

### Post by maduranga on 2007-07-22
it works. thx :)

---

### Post by AriciU on 2007-07-22
Or just upgrade to the latest compiz fusion from GIT and install the damn Fusion Icon. Having both Compiz Fusion and Beryl defies logic IMO.

---

### Post by maduranga on 2007-07-23
i have already install compiz fusion. but how can i upgrade it?

this is what i have added to my sources list when i was installing compiz fusion.


# Treviño’s Ubuntu Feisty EyeCandy Repository (GPG key: 81836EBF)
# Many eyecandy 3D apps: Beryl, Compiz, Fusion, AWN and kiba-dock
# built using latest available (working) sources from git/svn/cvs...
deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy
deb-src [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) feisty eyecandy

---

