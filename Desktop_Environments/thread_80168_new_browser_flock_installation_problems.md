---
title: "new browser flock installation problems"
date: 2005-10-21
forum: Desktop Environments
---

### Post by ShagzModo on 2005-10-21
Can anyone tell me how to get this new browser flock installed? i downloaded the
flock-0.4.8.en-US.linux-i686.tar.gz file from [http://www.flock.com/fiveways/togetstarted/](http://www.flock.com/fiveways/togetstarted/) I have this browser installed on another PC posessed by the Devil (Micro$oft iexplore). This New browser will have a very big impact on b rowsers to come.... I know how to unpack archives and i already tried installing this, but it's not working.... The installation won't start.
This package ain't available with apt get yet (I think)
I'm using the standard repositories that came with my breezy badger installation, and i also have universe repositories enabled.
Am i overlooking something?

Best regards,

Shagz Modo

---

### Post by chanders on 2005-10-22
Cd into the directory you extracted the files in and type this command in a terminal window

```
./flock
```

---

### Post by darkomen on 2005-10-22
Hello I have a problem when execute flock. I put "./flock" in the console (in the directory whit flock) gives to an error of `permission denied` when the permision of files are.
-rwxrwxrwx   1 darkomen darkomen     5112 2005-10-20 00:35 flock

 if I execute it as root also gives the error. somebody can help me?

---

### Post by dcarpenter on 2005-10-22
i downloaded flock just to check it out, and after extracting it i just ran the flock program and it worked... no installation needed.  Just run flock from the folder it gets extracted to, in my case the desktop.

---

### Post by gmc on 2005-10-23
Flock is compiled against libstdc++ v5. You may need to install it for Flock to work.

# sudo apt-get install libstdc++5

G.

---

