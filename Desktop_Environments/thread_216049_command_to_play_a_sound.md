---
title: "command to play a sound?"
date: 2006-07-14
forum: Desktop Environments
---

### Post by shanepardue on 2006-07-14
i'm using checkgmail and it allows for you to type a command for when new email arrives. what would be the command for playing a sound? i know i would have to provide my own sound, but how would i command it to play?

thanks!

---

### Post by jayemef on 2006-07-14
Does it need an actual command, or just a file? I'm not familiar with the program, but I would assume it had its own way of playing sounds. If so, you should be able to just include a path to a sound file. If not, you can use the play command:

```
$ sudo apt-get install sox
$ play *path_to_sound_file*
```

---

### Post by shanepardue on 2006-07-15
[IMG]http://img.photobucket.com/albums/v330/shanepardue/Screenshot.png[/IMG]

[SIZE="2"]maybe this will help you help me. ha

wouldn't that just require a command?[/SIZE]

---

### Post by jayemef on 2006-07-15
Yup, looks like it needs a command to me. Just go with my suggestion -- it should work. There may already be an app that comes with Ubuntu that will do the same, but play is what I've always used in the past. It's small and to the point.

---

### Post by shanepardue on 2006-07-15
any idea where i can get a sound like the one used by google's own gmail notifier? i've grown accustomed to it from my windows days. no biggie if not.

---

### Post by jayemef on 2006-07-15
Have any buddies who are Windows users? If so, see if one of them doesn't mind installing it. Then it's just a matter of locating the file that's getting played and sending it to you.

---

