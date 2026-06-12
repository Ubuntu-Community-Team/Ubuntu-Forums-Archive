---
title: "Avida error: instruction set file doesn't exist"
date: 2007-12-18
forum: Education &amp; Science
---

### Post by thelinuxguy on 2007-12-18
I installed Avida from the Feisty repository and tried to create a new world. However, after the final step, I keep getting an error message that says:
```

instruction set file specified in world file doesn't exist
event file specified in world file doesn't exist

```

The relevant options I have selected are as follows:
Simple setup (recommended)
Initial organism file: /usr/share/avida/organism.default
Grow from one organism
Environment files: /usr/share/avida/environment.cfg
New World file: /home/thelinuxguy/Avida/genesis
Work directory: /home/thelinuxguy/Avida

And a listing of my /usr/share/avida 
```

ls /usr/share/avida -l
total 41
-rw-r--r-- 1 root root  499 2007-03-02 06:45 analyze.cfg
drwxr-xr-x 3 root root  928 2007-12-18 13:02 doc_html
-rw-r--r-- 1 root root 1285 2007-03-02 06:45 environment.cfg
-rw-r--r-- 1 root root 1941 2007-03-02 06:45 events.cfg
-rw-r--r-- 1 root root 7648 2007-12-19 00:29 genesis
-rw-r--r-- 1 root root 7757 2007-03-02 06:45 genesis.4stack
-rw-r--r-- 1 root root  831 2007-03-02 06:45 inst_set.4stack
-rw-r--r-- 1 root root 1584 2007-03-02 06:45 inst_set.default
-rw-r--r-- 1 root root 1555 2007-03-02 06:45 organism.default
drwxr-xr-x 2 root root  144 2007-12-18 13:02 preset_organisms

```

I tried editing /usr/share/avida/genesis and changed line 25 and 26 to include the full path:
```

INST_SET /usr/share/avida/inst_set.default         # File containing instruction set
EVENT_FILE /usr/share/avida/events.cfg             # File containing list of events during run

```

What am I missing here?

---

### Post by thelinuxguy on 2007-12-22
** bump **

---

### Post by r4e on 2008-03-07
This might be a bit late for you, but for anyone else having problems with getting avida running the following resolved the issue for me. Throughout these instructions, substitute your username for {user}.

1. Copy the contents of /usr/share/avida to an avida folder in your home directory:

mkdir /home/{user}/avida
cd /usr/share/avida
cp -r * /home/{user}/avida

2. Open the genesis world file in vim or your favorite text editor:

vim /home/{user}/avida/genesis

After using the Insert key to switch into edit mode in vim, change DEFAULT_DIR  (~line 24) to:

```

DEFAULT_DIR /home/{user}/avida
 
```

If using vim, Esc from edit mode, then save and quit by typing:

:wq!

3. Launch avida with the command:

```

avida-qt-viewer

```

4. Select "Use Existing World" and click Next

5. As your world file, select:

/home/{user}/avida/genesis

6. Select /home/{user}/avida as the work directory.

7. Run the simulation: File -> Start Avida

8. Enjoy watching artificial life evolve.

r4e

---

### Post by thelinuxguy on 2008-03-08
Its definitely not late. Had got busy with other stuff and couldn't get Avida working before that. Thanks for the info. I will try it out later in the day.

---

### Post by UndiFineD on 2010-05-03
same issue here with lucid
and the suggested solution does not work for me

Random Seed: 0 -> 136937209
ENV: Loading file 'environment.cfg'.
ENV: Loading reaction 'NOT' with trigger 'not'.
ENV: Loading reaction 'NAND' with trigger 'nand'.
ENV: Loading reaction 'AND' with trigger 'and'.
ENV: Loading reaction 'ORN' with trigger 'orn'.
ENV: Loading reaction 'OR' with trigger 'or'.
ENV: Loading reaction 'ANDN' with trigger 'andn'.
ENV: Loading reaction 'NOR' with trigger 'nor'.
ENV: Loading reaction 'XOR' with trigger 'xor'.
ENV: Loading reaction 'EQU' with trigger 'equ'.
Loaded Instruction Library "inst_set.default" with 26 instructions.
Initializing Population...<cPopulation>
Building world 60x60 = 3600 organisms.
Geometry: Unknown
...Building Integrated Time Slicer...
Segmentation fault
undifined@head:~/avida$

---

### Post by CYarb on 2010-11-25
> **UndiFineD said:**
> same issue here with lucid
and the suggested solution does not work for me

Random Seed: 0 -> 136937209
ENV: Loading file 'environment.cfg'.
ENV: Loading reaction 'NOT' with trigger 'not'.
ENV: Loading reaction 'NAND' with trigger 'nand'.
ENV: Loading reaction 'AND' with trigger 'and'.
ENV: Loading reaction 'ORN' with trigger 'orn'.
ENV: Loading reaction 'OR' with trigger 'or'.
ENV: Loading reaction 'ANDN' with trigger 'andn'.
ENV: Loading reaction 'NOR' with trigger 'nor'.
ENV: Loading reaction 'XOR' with trigger 'xor'.
ENV: Loading reaction 'EQU' with trigger 'equ'.
Loaded Instruction Library "inst_set.default" with 26 instructions.
Initializing Population...<cPopulation>
Building world 60x60 = 3600 organisms.
Geometry: Unknown
...Building Integrated Time Slicer...
Segmentation fault
undifined@head:~/avida$

I am having the same issue as you. 

Bump.

---

### Post by froggykodok on 2011-02-13
FWIW, I followed the instructions, but I ignored the username replacement bit and just put /home/usr/avida and it worked.

---

### Post by funkyade on 2011-04-25
If you are serious in using this software, you are far better compiling it from source yourself. The version in the repository is very out-of-date (2.07b against 2.12.2).

It's pretty easy to do:

First, get the latest stable source from [here]("http://avida.devosoft.org/download/"). Unarchive it, then copy the folder into somewhere sensible, like ~/src, giving you a folder called avida-2.12.2-src inside.

Then,

```
sudo apt-get install build-essential libncurses5-dev cmake
cd ~/src/avida-2.12.2-src
./build_avida
```

and that's it... To get it running read the documentation and the README, they are quite explanatory.

---

