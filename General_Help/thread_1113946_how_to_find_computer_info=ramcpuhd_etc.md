---
title: "how to find computer info=ram/cpu/hd etc"
date: 2009-04-02
forum: General Help
---

### Post by jesse c on 2009-04-02
Ubuntu 8.10-Where do i find the display that will show the internal specs of the computer that i have Intrepid installed on?

---

### Post by jespdj on 2009-04-02
```
sudo lshw
```

---

### Post by jesse c on 2009-04-02
thanks jespdk but something is weird with terminal results.It looks like the readout starts in the middle of a page,like it might be on page 2 or something .It also is giving me much more technical info than i can comprehend. i really just want to see -total ram available,cpu speed,hard drive size installed,etc,like i can find in "my computer" on my Windows machine and also on my Mac machine.

---

### Post by night_fox on 2009-04-02
```
cat /proc/cpuinfo   #dislays processor info - bogomips means million instructions per second
cat /proc/meminfo   #displays memory usage  - total is at top
df                  #displays mounted devices and their size, use etc
```

---

### Post by |Mitch| on 2009-04-02
nm

[misread the question]

---

### Post by batharoy on 2009-04-02
If you prefer a GUI tool hardinfo can be found through Synaptic or
```
sudo apt-get install hardinfo

```

---

### Post by jesse c on 2009-04-02
batharoy-i copied and pasted your command into terminal and restarted my computer but i cant find the application.Where do i find the gui prompt?Ive looked in all applications/places/system but dont recognize any new category

---

### Post by nebileix on 2009-04-02
to run the program, press alt-f2 and type

```
hardinfo
```

to add into menu, type

```
gmenu-simple-editor
```

and add into any directory u prefer.

---

### Post by batharoy on 2009-04-02
> **jesse c said:**
> batharoy-i copied and pasted your command into terminal and restarted my computer but i cant find the application.Where do i find the gui prompt?Ive looked in all applications/places/system but dont recognize any new category
System>Preferences>System Profiler and Benchmark

---

### Post by jesse c on 2009-04-02
perfect batharoy.i didnt notice that new apt in sys/pref but thats exactly what i was looking for.(is there no longer a thread tool to mark posts as SOLVED)?

---

