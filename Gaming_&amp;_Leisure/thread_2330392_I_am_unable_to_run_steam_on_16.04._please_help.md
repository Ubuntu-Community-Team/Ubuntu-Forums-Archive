---
title: "I am unable to run steam on 16.04. please help"
date: 2016-07-11
forum: Gaming &amp; Leisure
---

### Post by Spacedementia87 on 2016-07-11
Hello everyone,

I installed steam on 16.04 a while ago a got it to run.

Tried to boot it up again today and got some errors.

I have since uninstalled steam and purged. removed steam-launcher.

I have also updated graphics drivers.

Reinstalled steam from:

apt-get install steam

all ran ok. Then:

```
james@james-Laptop:~/.steam/steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu$ steam
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2016-07-11 14:55:44] Startup - updater built Jun 16 2014 11:16:02
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)

```

Can anyone help?

---

### Post by QIII on 2016-07-11
Hello!

Did you install Steam from the repository or from their website priginally?

What graphics adapter and driver are you using?

"Some errors" doesn't tell us much.  Knowing the details of errors is critical to diagnosing your problem.

---

### Post by QDR06VV9 on 2016-07-11
> **Spacedementia87 said:**
> Hello everyone,

I installed steam on 16.04 a while ago a got it to run.

Tried to boot it up again today and got some errors.

I have since uninstalled steam and purged. removed steam-launcher.

I have also updated graphics drivers.

Reinstalled steam from:

apt-get install steam

all ran ok. Then:

```
james@james-Laptop:~/.steam/steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu$ steam
ILocalize::AddFile() failed to load file "public/steambootstrapper_english.txt".
[2016-07-11 14:55:44] Startup - updater built Jun 16 2014 11:16:02
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
SteamUpdateUI: An X Error occurred
X Error of failed request:  BadValue (integer parameter out of range for operation)

```

Can anyone help?
Is this on a Nvidia Card?

---

### Post by banceu_sergiu_ione on 2016-07-11
Try run this in terminal

```

cd $HOME/.steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu
mv libstdc++.so.6 libstdc++.so.6.bak
cd $HOME/.steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu
mv libstdc++.so.6 libstdc++.so.6.bak

```
then start steam and see if work

---

### Post by Spacedementia87 on 2016-07-11
> **QIII said:**
> Hello!

Did you install Steam from the repository or from their website priginally?

What graphics adapter and driver are you using?

"Some errors" doesn't tell us much.  Knowing the details of errors is critical to diagnosing your problem.

I think I originally installed it from the deb file from the website. I have e since removed it from the package manager and tried installing again both ways.

I am using nVidia 645M

I know, not helpful but I can't remember exactly. They were similar to the ones I posted but not exactly the same.

> **runrickus said:**
> Is this on a Nvidia Card?

Yes a 645M

> **banceu_sergiu_ione said:**
> Try run this in terminal

```

cd $HOME/.steam/ubuntu12_32/steam-runtime/i386/usr/lib/i386-linux-gnu
mv libstdc++.so.6 libstdc++.so.6.bak
cd $HOME/.steam/ubuntu12_32/steam-runtime/amd64/usr/lib/x86_64-linux-gnu
mv libstdc++.so.6 libstdc++.so.6.bak

```
then start steam and see if work

Yup I have tried that.

In fact I have tried completely removing steam including the ~/.steam directory.

---

### Post by QDR06VV9 on 2016-07-11
Have a look here: [http://askubuntu.com/questions/541343/problems-with-libgl-fbconfigs-swrast-through-each-update](http://askubuntu.com/questions/541343/problems-with-libgl-fbconfigs-swrast-through-each-update)

---

### Post by howefield on 2016-07-12
Thread moved to the "*Gaming & Leisure*" forum.

---

