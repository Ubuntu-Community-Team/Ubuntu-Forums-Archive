---
title: "Saurbraten won't start."
date: 2006-10-23
forum: Gaming &amp; Leisure
---

### Post by geokok on 2006-10-23
I downloaded sauerbraten and unzipped the file into a directory in my
home folder. When I try to run it I get 
":~/apps/sauerbraten$ ./sauerbraten_unix 
./bin_unix/linux_client: error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory
"

Any clues how can I play the game?

---

### Post by geokok on 2006-10-23
I solved my problem by installing the missing dependency through synaptic.
Just in case others have the same problem too..

---

### Post by AdyE on 2007-01-25
> **geokok said:**
> I solved my problem by installing the missing dependency through synaptic.
Just in case others have the same problem too..

Hi, sorry to resurrect such an old post but I have the same problem. I have tried to locate said file in synaptic but can't seem to find it. Could anyone write an idiots mini how to please.
Thanx :-)

---

### Post by k420 on 2007-02-20
```
sudo apt-get install libSDL-mixer*
```

---

### Post by openix on 2007-02-25
I have a quick Sauerbraten install guide on my site at [http://www.openix.co.nz/sauerbraten.php]("http://www.openix.co.nz/sauerbraten.php")

Hope this helps someone

---

### Post by n8bounds on 2007-06-29
I get a 404 on that link.. did you move it?

---

