---
title: "Installing Heroes of Newerth"
date: 2010-04-27
forum: Gaming &amp; Leisure
---

### Post by Xorlathor on 2010-04-27
So I downloaded the .sh file from the HoN site, and I enabled executing it as a program. When I click run, nothing happens. When I click run in terminal, the terminal flashes up then disappears. 

If I run the program directly through the terminal, it results in the following:

```
robert@robert-laptop:~$ '/home/robert/Downloads/HoNClient-0.3.3.1.sh' 
156200+0 records in
305+1 records out
156200 bytes (156 kB) copied, 0.171436 s, 911 kB/s



PANIC
  Initial setup failed. Cannot continue.

```

I can't figure out what I'm doing wrong...

---

### Post by gio31 on 2010-04-27
try chmod

---

### Post by gio31 on 2010-04-27
btw i have HON installed in my pc and i never encountered any problems

---

### Post by Xorlathor on 2010-04-27
How would that code look like?

---

### Post by tekkidd on 2010-04-27
try this 

```
cd /directory/
```

```
chmod +x filename
```

```
./filename
```

---

### Post by Xorlathor on 2010-04-27
> **tekkidd said:**
> try this 

```
cd /directory/
```

```
chmod +x filename
```

```
./filename
```

Doing those commands results in the same output as before: 

```
robert@robert-laptop:~/Downloads$ ./HoNClient-0.3.3.1.sh
156200+0 records in
305+1 records out
156200 bytes (156 kB) copied, 0.166368 s, 939 kB/s



PANIC
  Initial setup failed. Cannot continue.

```

---

### Post by anku247 on 2010-04-27
how i got it to work

put the file on desktop

type cd Desktop


then sh the file name 

should pop up for install

---

### Post by gio31 on 2010-04-28
the code should look like these

chmod +x /home/wesker/Desktop/HoNClient-0.3.1.sh


then

./HoNClient-0.3.1.sh

hope that it works

---

### Post by EarthMind on 2010-04-28
Or it's possible that the installation file is corrcupted, probably because it wasn't completely/correctly downloaded. Just download it again and try again.

---

