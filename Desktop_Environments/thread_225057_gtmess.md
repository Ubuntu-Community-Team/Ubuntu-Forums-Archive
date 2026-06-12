---
title: "gtmess"
date: 2006-07-29
forum: Desktop Environments
---

### Post by cyclister on 2006-07-29
Can somone plz help me with a gtmess from sourgeforge have tar that thing up, but then what?

Would be really glad if someone did know how to:)

---

### Post by passonno on 2007-02-13
Did you ever figure it out? 

I am installing it right now, and will let you know how it goes. 

pm me if you want and we can discuss it.

---

### Post by passonno on 2007-02-13
If you still care:

Make sure you have the libncurses packages, including the -dev package, then

cd to the directory where it was downloaded
tar xvzf gtmess-0.92.tar.gz
cd gtmess-0.92
cat install | more  (always read the install files, very important step)
then  

./configure
make
sudo make install


Hope that helps,

Anthony Passonno

---

