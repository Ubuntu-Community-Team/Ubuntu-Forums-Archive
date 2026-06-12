---
title: "Need help compiling GIMP 2.3.x"
date: 2006-03-03
forum: Desktop Environments
---

### Post by pixelnate on 2006-03-03
I would really like to try out GIMP 2.3.x, but I cannot figure out how to compile it along side the v2.2 that is already installed. I was trying to follow the instrux on this page: [http://gimp.org/release-notes/gimp-2.3.html](http://gimp.org/release-notes/gimp-2.3.html)  , but I really can't seem to wrap my mind around the script they suggest building.

Can somebody please help shed some light on how I would use that script to get GIMP 2.3.x installed? Thanks in advance.

---

### Post by Ampersand on 2006-03-03
Firstly, you need to make sure you've got the build-essential package installed. You then download and unzip the gimp 2.3 source. Open a terminal, go to the directory containing the source and compile it using:
```

./configure --prefix=/opt/gimp-2.3
make
sudo make install

```

For the script, run
```
sudo nano /usr/bin/gimp-2.3
```

copy
```

#!/bin/sh

PATH=/opt/gimp-2.3/bin:$PATH
export PATH
LD_LIBRARY_PATH=/opt/gimp-2.3/lib
export LD_LIBRARY_PATH

/opt/gimp-2.3/bin/gimp-2.3 "$@"

```
into it (you can use the middle mouse button to paste), then finally make it executable using the command:
```
sudo chmod 755 /usr/bin/gimp-2.3
```

---

