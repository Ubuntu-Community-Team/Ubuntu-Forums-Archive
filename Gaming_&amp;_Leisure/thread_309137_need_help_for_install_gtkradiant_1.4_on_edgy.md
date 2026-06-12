---
title: "need help for install gtkradiant 1.4 on edgy"
date: 2006-11-29
forum: Gaming &amp; Leisure
---

### Post by kr0n1x on 2006-11-29
hi, i downloaded linux-radiant-1.4.0.run and installed it!
but when i try to run program in terminal (radiant), terminal show me an error:
```
pasquale@pasquale-desktop:/lib$ radiant
./radiant.x86: ./libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
```

searching the error on google, i had found only 1 topic talking of it...without full help:( i've the problem anyway!

how to fix it? i tried with "sudo apt-get install gcc" but the last version of gcc for my edgy is 4.1!

i'm using: ubuntu 6.10
game for gtkradiant: wolfenstein enemy territory

i hope i wrote all infos...if no, ask me what you need for a good help:)

ps: sorry my bad english

bye

---

### Post by cronholio on 2006-11-29
Look [here.]("http://ubuntuforums.org/showthread.php?t=270605")

---

### Post by kr0n1x on 2006-11-29
thanks for reply, i read the last reply, but i don't understand how to fix the problem:( 

can you re-write how to fix it?

when i write: ldd /usr/lib/libstdc++.so.6
the terminal show me:
```
pasquale@pasquale-desktop:~$ ldd /usr/lib/libstdc++.so.6
        linux-gate.so.1 =>  (0xffffe000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7ecc000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7ec1000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7d8d000)
        /lib/ld-linux.so.2 (0x80000000)
```

this is disequal than the code shown by the poster of your topic linked.

how to modify my libstdc++.so.6? or i don't need to modify it??

please re-write the solution please:( thanks

edit: and when i try to move the file (unfixed), the terminal show me:
```
pasquale@pasquale-desktop:~$ sudo mv /usr/lib/libgcc_s.so.1 /usr/lib/libgcc_s.so.1.old
mv: impossibile fare stat di `/usr/lib/libgcc_s.so.1': Nessun file o directory
pasquale@pasquale-desktop:~$ 
```
i haven't libgcc_s.so.1 O_o

---

### Post by cronholio on 2006-11-29
Try

```
sudo mv /usr/lib/libgcc_s.so.1 /usr/lib/libgcc_s.so.1.old
```

If it doesn't help, revert it by

```
sudo mv /usr/lib/libgcc_s.so.1.old /usr/lib/libgcc_s.so.1
```

---

### Post by cronholio on 2006-11-29
> I haven't libgcc_s.so.1

Okay, then do this:

```
sudo aptitude install libgcc1
```

---

### Post by kr0n1x on 2006-11-29
mmm readed my "edit" in last post?

anyway, when i try these command in terminal, the terminal can't found files!
look:
```
pasquale@pasquale-desktop:~$ sudo mv /usr/lib/libgcc_s.so.1 /usr/lib/libgcc_s.so.1.old
mv: impossibile fare stat di `/usr/lib/libgcc_s.so.1': Nessun file o directory
pasquale@pasquale-desktop:~$ radiant
./radiant.x86: ./libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
pasquale@pasquale-desktop:~$ sudo mv /usr/lib/libgcc_s.so.1.old /usr/lib/libgcc_s.so.1
mv: impossibile fare stat di `/usr/lib/libgcc_s.so.1.old': Nessun file o directory
pasquale@pasquale-desktop:~$ radiant
./radiant.x86: ./libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
pasquale@pasquale-desktop:~$ 

```

translated: mv: impossible to make stat of 'dir/file': File or Directory doesn't exist
:( solution?

---

### Post by kr0n1x on 2006-11-29
> **cronholio said:**
> Okay, then do this:

```
sudo aptitude install libgcc1
```

the terminal say: libgcc1 is up to date :S

---

### Post by cronholio on 2006-11-29
Yes, I saw your edit. Check my post above. And thanks for the translation, but I know that much Italian.:D

---

### Post by cronholio on 2006-11-29
Okay, apparently it is in "/lib", so try this

```
sudo mv /lib/libgcc_s.so.1 /lib/libgcc_s.so.1.old
```

---

### Post by kr0n1x on 2006-11-29
forever equal error:
```
pasquale@pasquale-desktop:~$ sudo mv /usr/lib/libgcc_s.so.1 /usr/lib/libgcc_s.so.1.old
mv: impossibile fare stat di `/usr/lib/libgcc_s.so.1': Nessun file o directory
pasquale@pasquale-desktop:~$ sudo mv /usr/lib/libgcc_s.so.1.old /usr/lib/libgcc_s.so.1
mv: impossibile fare stat di `/usr/lib/libgcc_s.so.1.old': Nessun file o directory
pasquale@pasquale-desktop:~$ 
```

are you in irc? if yes, write server and channel please? when we fix the problem i write the solution here.

---

### Post by kr0n1x on 2006-11-29
> **cronholio said:**
> Okay, apparently it is in "/lib", so try this

```
sudo mv /lib/libgcc_s.so.1 /lib/libgcc_s.so.1.old
```

ehi now this work!!!!

i tried to do: radiant but nothing...forever: 

```
pasquale@pasquale-desktop:~$ sudo mv /lib/libgcc_s.so.1 /lib/libgcc_s.so.1.old
pasquale@pasquale-desktop:~$ radiant
./radiant.x86: ./libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
pasquale@pasquale-desktop:~$ 

```

now^?

---

### Post by cronholio on 2006-11-29
cronholio in #ubuntu at irc.freenode.net

---

### Post by kr0n1x on 2006-11-29
i and cronholio tried in irc to solve the problem, but without results for now:(

command tried: 
input: which radiant
output: /usr/local/bin/radiant

input: sudo cp /lib/libgcc_s.so.1.old /usr/local/bin/libgcc_s.so.1
       sudo cp /lib/libgcc_s.so.1.old /usr/lib/libgcc_s.so.1
       sudo cp /lib/libgcc_s.so.1.old /lib/libgcc_s.so.1

all commands works...but when i try: radiant
the terminal show me forever:
```
pasquale@pasquale-desktop:~$ radiant
./radiant.x86: ./libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
pasquale@pasquale-desktop:~$ 

```

someone has any idea?

---

### Post by kr0n1x on 2006-11-29
chatting on Quakenet, one my frends helped me with the problem:)

now my radiant work, now i show how to fix:

open a terminal and copy libgcc_s.so.1 to radiant directory!

example:
```
sudo cp /lib/libgcc_s.so.1 /usr/local/games/GtkRadiant-1.4/
```


thanks to my friend Darecon and also to cronholio for help:)

bye

---

### Post by cronholio on 2006-11-29
D'oh! And I told you before that wouldn't help. Sorry for that.

---

