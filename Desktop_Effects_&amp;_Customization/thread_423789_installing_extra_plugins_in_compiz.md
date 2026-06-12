---
title: "installing extra plugins in compiz"
date: 2007-04-26
forum: Desktop Effects &amp; Customization
---

### Post by dckirba on 2007-04-26
Hello all,

I've installed feisty and have everything working including desktop effects with a minimum of us! Yay for the team, great job. \\:D/ 

I installed gnome-compiz-manager and compiz extra. However, these do not include the animation, thumbnail and 3d plugins.

I downloaded the animation and 3d plugins from the compiz site.

My questions:

1. do I just do the normal 'make, make install' to install these plugins? Do I have to do anything special before I do this?
2. Any idea where I can find the thumbnail plugin?

I am happy that compiz is working well and I really don't want to install beryl if I can get all the effects I want through plugins in compiz. 

Thanks in advance,
David K

---

### Post by Kevin on 2007-04-26
1. Yes, make, make install.  (you don't need sudo)
2. The thumbnail plugin is not available for compiz yet.  It required some hacks to work in beryl that weren't included in compiz.  Once we get Xorg 7.3 and the next version of compiz, we'll have full input redirection, which allows us to make all sorts of effects like that, so be patient :)

---

### Post by dckirba on 2007-04-26
Thanks for the quick reply Kevin. Will go ahead and install when I get home tonight. And I will try being patient :) That's a tough one!

Cheers,
David K

---

### Post by mikibg on 2007-04-26
I install extra plug and Compiz-Settings 0.07 ,,,,3d works but when I want to setup give me that 3d do not install???
Second how to install animation plug in Compiz-Settings 0.07??Try to google this topic but nothing

---

### Post by blamecanada on 2007-04-26
I could never get anywhere near the flexibility of beryl with compiz, although what compiz has feels much more polished and stable. Until I can figure out how to easily add and edit plugins as I can with beryl I won't be moving to Compiz. Now that they have merged again, hopefully we will get all the plugins of beryl with the stablilty of compiz.

---

### Post by mikibg on 2007-04-26
this 0.3.6 compiz in fiesty is ....s.... hope they send us update ...so much plug do not work with this version

---

### Post by dckirba on 2007-04-26
Hiyya Kevin,

well I got home and tried make and make install and got a small error. Not sure how to fix it though:

```
david@ChomonKora:~/Desktop/animation$ make
[: 1: ==: unexpected operator
-e compiling : animation.c -> build/libanimation.loPackage compiz was not found in the pkg-config search path.
Perhaps you should add the directory containing `compiz.pc'
to the PKG_CONFIG_PATH environment variable
No package 'compiz' found
/bin/sh: libtool: not found
make: *** [build/libanimation.lo] Error 127
david@ChomonKora:~/Desktop/animation$ locate compiz.pc
david@ChomonKora:~/Desktop/animation$ find compi*.*
find: compi*.*: No such file or directory
david@ChomonKora:~/Desktop/animation$ 
```

I tried finding the path to compiz.pc but wasn able to find such a file. I&#7743; rather clueless when it comes to things like this, so help would be appreciated ;)

Also, while browsing through gconf-editor, I saw that compiz has the widget plugin. Does this mean I can use the screenlets plugin?

Cheers,
David K

---

### Post by dckirba on 2007-04-26
My mistake, didn have the -dev packages installed. Should work now! G´nite!

---

### Post by dckirba on 2007-04-26
Rightho!

All dev packages installed, but I still get an error when I type make:

```
david@ChomonKora:~/Desktop/animation$ make
[: 1: ==: unexpected operator
-e compiling : animation.c -> build/libanimation.lo/bin/sh: libtool: not found
make: *** [build/libanimation.lo] Error 127
david@ChomonKora:~/Desktop/animation$ 

```

Not sure what to do from here,

cheers,
Me

---

### Post by mikibg on 2007-04-26
Animation And 0.3.6 Do Not Work....with Compiz-Settings 0.07
Xaxaxaxaxa
Must Have 0.4 Or 0.5

---

### Post by dckirba on 2007-04-27
Hmm... are you sure about this? Because it said 0.3.5 and higher on the compiz site where I downloaded it from.

David

---

### Post by mikibg on 2007-04-27
ok I do something ....cccc and it is work....but I can not see settings  ...only 1 animation magic lamp ....because have problem to install animation.shemas ...:mad:
same problem with 3d but find the way how to start

---

### Post by dckirba on 2007-04-27
Hey Mik,

let me know what you did. Slowly please :) I am really bad at figuring these kinda things out :)

Thanks,
David K

---

### Post by mikibg on 2007-04-27
I can write you how to do that but ,,,,,no need for this sh,,,belive me
I can not belive that thay put half install in system like fiesty ,,,full or nothing !!!!
bro I delete everything name compiz after 2 days of wright from fiesty and run beryl ...listen music ...and :popcorn: 
:lolflag:

---

