---
title: "big trouble: can't format !"
date: 2009-05-05
forum: General Help
---

### Post by the_nomad on 2009-05-05
hello,

i'm trying to do a zero filling format (my 250GB SATA hard drive is full of errors, can't install ubuntu neither windows)... i am now on ubuntu 9.04 live cd where i opened a terminal and i left it 8 hours to "work" with this command 

```
sudo dd if=/dev/zero of=/dev/sda bs=1M
```

but nothing happenned :| i dont think is because of a processor/memory problem since i have a intel core2quad @ 2.4ghz and 2GB of RAM...

how long should a format like this take?
can anyone give me some ideeas on how can i "debug" my full of errros harddrive?

please help :( thanx in advance...

---

### Post by pastalavista on 2009-05-05
Try the partition editor (gparted) in System > Administration

---

### Post by cariboo on 2009-05-05
I would suggest you go th your hard drive's manufacturers web site and download and use their diagnotic tools to make sure the drive is fit for usage.

---

### Post by jbrown96 on 2009-05-05
Try this instead. It will actually give you some output, so you can see the progress and does the same thing

```
sudo shred -n 0 -zvv /dev/sda
```

---

### Post by the_nomad on 2009-05-05
gparted doesnt start ... says "searching /dev/sda..." but nothing happens afterall :| maybe i should wait longer?

l.e. and if i close and try start it again crashes

---

### Post by the_nomad on 2009-05-05
> **jbrown96 said:**
> Try this instead. It will actually give you some output, so you can see the progress and does the same thing

```
sudo shred -n 0 -zvv /dev/sda
```


indeed it gives me some output:

```
shred: /dev/sda: pass 1/1 (000000)...
shred: /dev/sda: pass 1/1 (000000)...144MiB/233GiB 0%


```

any ideea how this should take? does it depend on the amount of errors on my harddrive?

---

### Post by the_nomad on 2009-05-05
omg! that's only 1% (2,5GB) in 8 hours!! :|
is it normal? i mean, is there any way i can speed things up? does it have anything to do with the speed at which i've burnt the cd (16x) ?

---

### Post by pastalavista on 2009-05-05
Really, just use gaprted (from the live CD)... delete the partition and then format it to whatever filesystem you want.. shouldn't take more than 10 minutes

---

