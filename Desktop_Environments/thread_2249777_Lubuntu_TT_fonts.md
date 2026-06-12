---
title: "Lubuntu TT fonts"
date: 2014-10-24
forum: Desktop Environments
---

### Post by mayagrafix on 2014-10-24
I have turned an old laptop into an appliance by using a Minimal install version of Lubuntu. It works great! only 85 megs. However, the one thing I use it for (reading PDF docs) could be made better by adding TT screen fonts (or any other screen fonts that are available). Is this possible in Lubuntu? if so, what command in a terminal should I execute?

Thanks!

---

### Post by BazBear on 2014-10-24
I think it should be 'sudo apt-get install ttf-mscorefonts-installer'. I think you'll also have to agree to a EULA, as it's under a MS copyright.

---

### Post by mayagrafix on 2014-10-25
Great answer. Thanks for your help. However, in order for the mscorefonts installer to work, I had to run this comand:
sudo dpkg -P ttf-mscorefonts-installer  
sudo apt-get install ttf-mscorefonts-installer 

Thanks again :<)

---

### Post by BazBear on 2014-10-25
Glad to help, though I'm a bit baffled why that command wouldn't pull it down from the repo and install it.

Oh well, all's well that ends well :)

---

