---
title: "Banshee 0.9.11.1?"
date: 2005-11-12
forum: Deferred/Invalid Requests
---

### Post by GameGod on 2005-11-12
Hi guys,

Any chance we'll see a backport of Banshee 0.9.11.1?

Thanks!

GameGod

---

### Post by jdong on 2005-11-12
Yes -- once the underlying Mono backports are done. This will take some time and coordination with the Ubuntu Mono Team, as backporting a language interpretor can have significant (positive, negative alike) impact on other Mono stuff.

---

### Post by GameGod on 2005-11-12
Sounds good, thanks!

(Any vague idea what the timeline is for this? ... if not, I understand... I develop too) ;)

---

### Post by jdong on 2005-11-12
Timeline is unknown, there are too many fluid parameters to predict.

---

### Post by vassie on 2005-11-14
If anyones interested, I have created my own deb's here

[http://www.benvassie.net/2005/11/14/how-to-compile-banshee-09111-on-breezy/](http://www.benvassie.net/2005/11/14/how-to-compile-banshee-09111-on-breezy/)

Ben

---

### Post by jdong on 2005-11-14
UPDATE: Seems like siretart and the Ubuntu MOTU team wants to do this as a breezy-updates package, because of all the red tape Backports would have to go through :)

---

### Post by Praetorian on 2005-11-14
What a great program it's almost iTunes (which is in my opion the best media player). I only miss some features but I hope they will be present in future releases like shown on this page
[http://www.banshee-project.org/index.php?title=FeatureRequest&curid=979&diff=145&oldid=144](http://www.banshee-project.org/index.php?title=FeatureRequest&curid=979&diff=145&oldid=144)
But it is a very promising app. :D

---

### Post by vassie on 2005-11-17
Hello

As with 0.9.11.1, I have posted deb's and a procedure on how to build 0.9.12 on my site

[http://www.benvassie.net/2005/11/17/banshee-0912-for-breezy/](http://www.benvassie.net/2005/11/17/banshee-0912-for-breezy/)

Ben

---

### Post by jadugarr on 2005-11-19
[QUOTE=vassie]Hello

As with 0.9.11.1, I have posted deb's and a procedure on how to build 0.9.12 on my site

[http://www.benvassie.net/2005/11/17/banshee-0912-for-breezy/](http://www.benvassie.net/2005/11/17/banshee-0912-for-breezy/)

Ben[/QUOTE]

Thanks for the debs Ben.  I did notice that after the upgrade that my banshee shortcut was removed from the applications menu, but that was easily fixed.

---

### Post by vassie on 2005-11-23
[quote=jadugarr]Thanks for the debs Ben.  I did notice that after the upgrade that my banshee shortcut was removed from the applications menu, but that was easily fixed.[/quote]

I'm not too sure what went on there, I built them the same way I built older versions, and they all had menu entried

I hope an official backport comes along soon, 0.9.13 will have Creative Zen support :D

Ben

---

### Post by lusepuster on 2005-12-16
Hi; I tried building the Banshee package myself on my iBook, but after having built and installed it apparently succesfully, it wouldn't run. It still claimed it needed GTK-SHARP 2.4.0, though I had changed the file configure.ac as described. The error seemed to have to do with banshee.exe in the /usr/local/lib directory. Any idea what might be wrong?

---

