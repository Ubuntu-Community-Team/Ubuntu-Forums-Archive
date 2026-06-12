---
title: "Can not add more fonts"
date: 2006-08-19
forum: Desktop Environments
---

### Post by true_friend on 2006-08-19
I am using ubuntu 6.06. i deleted a font from fonts folder to add the newer version. but now i can not paste any font in the fonts folder. i treid also nautilus but can not add fonts through it also.
plz tell me some command line solution to add fonts in the main font folder. i mean "fonts:///"
Regards
True_Friend
Note: i also updated my font cache but can not add new fonts after it.

---

### Post by foolsh on 2006-08-19
its probably a permissions problem
try someting like this with the right directory and file names

sudo cp /foo/newfontfiles /bar/fontsfolder

---

### Post by jimmygoon on 2006-08-19
drag and drop them in there. Ubuntu and the fonts:/// folder won't acknowledge it until your reboot... yes even if you fc-cache -vf... So just try rebooting ;)

---

### Post by true_friend on 2006-08-19
tried it many times.
but ............ :(

---

### Post by sen~ on 2006-08-19
You can also create a font dir for your user:

```
 mkdir ~/.fonts
```

...then just copy your fonts to that folder an you can use them.

---

### Post by true_friend on 2006-08-19
hmmmmmmmm.
usr directory is hidden i think. i had made a directory called .cronfiles.
can not see it now.
so how to access these folders???

---

