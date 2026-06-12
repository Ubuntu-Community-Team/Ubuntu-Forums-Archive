---
title: "Regnum launcher issues"
date: 2011-06-02
forum: Gaming &amp; Leisure
---

### Post by Dleacy on 2011-06-02
Ok had a look in the regnum forums and ubuntu ones but have not found a solution.

Running natty 32 bit, I downloaded the installer from the regnum website and it installs fine with out an issue. When I start the launcher i get a no handler for image error which apparently is the logo not loading, this is not much of an issue but is just a mild annoyance. It is supposed to be an issue with libpng and I have done the recommended libpng12 install with no luck.

The other issue is that it hangs. it moves past the verifying stage and reaches about 70k then hangs. It has hung at lower amounts but 70 is the highest it has got.

If anyone has any ideas please help! I was thinking of running the windows version through wine but there looks to be a lot of problems with this

Cheers all!!

Edit: running the launcher through terminal brings this

dan@dan-ubuntu:~$ regnum/rolauncher
libhal.so: cannot open shared object file: No such file or directory
libhal-storage.so: cannot open shared object file: No such file or directory

---

### Post by Perfect Storm on 2011-06-03
```
cd regnum
./rolauncher
```

---

### Post by Dleacy on 2011-06-03
All this does is launch the rolauncher. terminal still brings up the same libhal error and it still hangs on verifying.

Made some progress on the verifying issue, the launcher downloads the updated launcher from a http site so I am downloading through the link using firefox. It even hangs in there, the only way to make progress is to pause and restart the download repeatedly to "force" it to go a little further.

If anyone has the updated rolauncher can they link it somehow with dropbox or something similar it should be in regnum/selfupdate

Cheers

---

### Post by Dleacy on 2011-06-03
UPDATE

After using the stop start method i described above I have new launcher which has solved the problem with  the image handling. however still the same problem, gets past verifying stage this time but stops at 220k. I have no idea what its downloading this time but if any one has any idea that would be ace.

if someone has a working Regnum could they somehow post their files for download?

---

### Post by Conzar on 2011-06-06
> **Dleacy said:**
> 
dan@dan-ubuntu:~$ regnum/rolauncher
libhal.so: cannot open shared object file: No such file or directory
libhal-storage.so: cannot open shared object file: No such file or directory
Try this:
```

cd to /usr/lib

```
then
```

sudo ln -s libhal.so.1.0.0 libhal.so
sudo ln -s libhal-storage.so.1.0.0 libhal-storage.so

```

---

### Post by Dleacy on 2011-06-07
Ok ill give it a bash, im on holiday tomorrow but ill update when im back as im struggling with network maanger at the moment as well!

---

