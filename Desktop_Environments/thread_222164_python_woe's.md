---
title: "python woe's"
date: 2006-07-24
forum: Desktop Environments
---

### Post by OrganicPanda on 2006-07-24
hey guys i'm having alot of fun with blender over the past couple of days, what an amazing program, look what i made [* My Cup'o'Buntu*]("http://www.organicpanda.net/upload/stuffs/cup_withspoon_yes.jpg") But anyway thats besides the point,i downloaded lots of lovely python scripts but when i start blender from the terminal i get:

```

panda@panda-desktop:~/.blender$ /home/panda/.blender/blender
Compiled with Python version 2.3.
Could not find platform independent libraries <prefix>
Could not find platform dependent libraries <exec_prefix>
Consider setting $PYTHONHOME to <prefix>[:<exec_prefix>]
'import site' failed; use -v for traceback
Checking for installed Python... No installed Python found.
Only built-in modules are available.  Some scripts may not run.
Continuing happily.

```

and then it starts but apparently without python support, it has an instruction in the middle there but i have no idea what it's asking me to do, any help?

cheers guys n gals,
panda

---

### Post by Paerez on 2006-07-24
try running:
```
sudo aptitude install python
```
to make sure python is installed, then run blender.

Nice cup, btw. But shouldn't the mug be brown/orange :D

---

### Post by OrganicPanda on 2006-07-24
Yeah i guess i should make an official ubuntu render. not a bad idea for an avater really, i'm in need of one..... anyway back on topic i had tried that before i posted but i was returned a rather dissapointing:

```

panda@panda-desktop:~$ sudo aptitude install python
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
panda@panda-desktop:~$  

```

which isn't exactly helpful lol, ideas?

---

### Post by Paerez on 2006-07-24
try reinstalling blender to make sure it has all its dependencies:
```
sudo aptitude --reinstall install blender
```

also can you give me:
```
python -V
```

---

### Post by OrganicPanda on 2006-07-24
python -V gives me

```
panda@panda-desktop:~$ python -V
Python 2.4.3
panda@panda-desktop:~$
```

the thing about blender is that you download the newest version from the blender site, untar it and it runs from there so i put it in .blender because it seemed logical,so you could argue it's not really installed atall

---

### Post by OrganicPanda on 2006-07-27
nobody?

---

### Post by etank on 2006-07-27
Since that one is not really installed try the one from the repo. It may not be the same version but that would possibly call the dependencies that you are missing. Then try the one that you currently have and if it works remove the one from the repo.

It's worth a shot.

---

### Post by OrganicPanda on 2006-07-28
ahh thats quite a good plan, i'll get on that

---

