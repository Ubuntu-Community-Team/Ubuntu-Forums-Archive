---
title: "40gb and auto shut down"
date: 2009-02-07
forum: General Help
---

### Post by Ishai Cohen on 2009-02-07
ok im downloading a file with wget
and its over more 4 hours
and i want to go sleep soon
so is there a way to do that my pc will shut down more 4 hours? :)

second question
my hard drive is 160gb

now, i right click on my computer and saw i have 120gb left

now i have no idea how i used 40gb 8D
any clue?

---

### Post by kayvortex on 2009-02-07
You can use the shutdown program:
```
sudo shutdown -h 23:45
```
will halt the system at 23:45.
Take a look at shutdown's man page for more info
```
man shutdown
```

As for the disk space, you can use the du command to examine directory sizes:
```
du -hsc /dir/to/examine1 /dir/to/examine2 ...
```
will list the sizes of the directories "/dir/to/examine1" "/dir/to/examine2" etc.
Again, take a look at its man page for more info:
```
man du
```
This will give you a clue as to what's taking up so much space. Perhaps it could be log files taking up so much room: maybe /var is taking up all that space?

---

### Post by Ishai Cohen on 2009-02-08
wow thanks

about the second thing, the problem is that when i right click on my computer i also see that i only used 8gb xD

so i still dont know where 32gb went ^_^

---

### Post by kayvortex on 2009-02-08
One thing that has just occurred to me is that maybe the "problem" is that you've not taken into account that you've partitioned your disk: could you tell me what
```
sudo fdisk -l
```
prints out?

---

