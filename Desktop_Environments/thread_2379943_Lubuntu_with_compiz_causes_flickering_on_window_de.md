---
title: "Lubuntu with compiz causes flickering on window decoration"
date: 2017-12-11
forum: Desktop Environments
---

### Post by aubreybourke on 2017-12-11
Hi,

Im using Lubuntu with compiz. 

1. First I install all compiz packages

```
sudo apt-get install compiz*
```

2. Then I enable the window decoration in compiz configuration manager

3. Then I do a ```
compiz --replace
```

and it causes flickering on the window decoration.

Can anyone help me fix this?

---

### Post by Autodave on 2017-12-14
Since no one else has jumped in, let me try.  First off, I have never heard of anyone running Compiz in Lubuntu. I am not sure that you actually can. But anyway, what are the specs of the machine you are using? Does it have a dedicated graphics card in it? If so, what one? Have you installed any drivers for the card? If so, what one and where did you get it from?

---

### Post by mc4man on 2017-12-15
Don't use lubuntu so just a shot in the dark.
Install compizconfig-settings-manager
Open it (command is ccsm
Open the OpenGl plugin > Texture Filter, set to "Fast"
Close ccsm, log out/in & see

---

