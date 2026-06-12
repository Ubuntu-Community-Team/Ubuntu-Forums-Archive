---
title: "Problem with nvidia drivers from apt-get"
date: 2005-11-18
forum: Desktop Environments
---

### Post by cmsimike on 2005-11-18
I just recently installed 5.10 (upgraded from 5.04, and by upgrade, i mean format/reinstall). I tried to apt-get the nvidia drivers exactly as i did in 5.04 and, though they are installed and configured correctly (as-per ubuntuguide.org) I am not getting graphics acceleration. further more, when trying to run glxgears, nothing outputs to the console anymore, where as before the console would show the fps.

thanks

---

### Post by invalid on 2005-11-18
```
glxgears -iacknowledgethatthistoolisnotabenchmark
```

Cb

---

### Post by cmsimike on 2005-11-18
never said that it was a benchmark. i said that now glxgears doesnt show anything to stdout where as before it used to show the fps. this happened after i did an apt-get for the nvidia drivers

---

### Post by invalid on 2005-11-18
Just type it.

Cb

---

### Post by cmsimike on 2005-11-18
erm.... how about no

---

### Post by invalid on 2005-11-18
I am sorry you think this is a joke, or that you think I am trying to poke fun at you. If you would take two seconds to copy paste the command, you would see that you get output. 

Do a search on the forums, and you will find that this is infact the way you must run glxgears now in order to have any results.

If after you do this, and you still get no results or you just want to do something, feel free to report me as a bad post. Your choice.

Cb

---

### Post by Hairy_Palms on 2005-11-19
i can see why people would think  this stuff is made up, but that genuinely is the way to run it.

---

### Post by cmsimike on 2005-11-19
[QUOTE=invalid]```
glxgears -iacknowledgethatthistoolisnotabenchmark
```

Cb[/QUOTE]

Well what do you know...well YOU knew. I didn't. Sir(or Madam) I truly apologize for not listening to you.


<~~pwned

---

### Post by oxEz on 2005-11-19
Or you can try:
```
glxgears -printfps
```

---

### Post by invalid on 2005-11-19
[QUOTE=oxEz]Or you can try:
```
glxgears -printfps
```[/QUOTE]
Hey thanks for this. I will start posting this flag instead, so I can quit being flamed by people who think I am trying to make a joke. It's just happend too much!

Cheers,
Cb

---

### Post by Drain on 2005-11-19
[QUOTE=invalid]Hey thanks for this. I will start posting this flag instead, so I can quit being flamed by people who think I am trying to make a joke. It's just happend too much!

Cheers,
Cb[/QUOTE]

If it helps, I didn't doubt you - I learned after doubting "sudo apt-get moo" that there are some wacky linux commands. ;-)

---

### Post by invalid on 2005-11-19
Hehe, yes indeed, the fun world of linux!

Cheers,
Cb

---

### Post by cmsimike on 2005-11-19
[QUOTE=invalid]Hehe, yes indeed, the fun world of linux!

Cheers,
Cb[/QUOTE]

Again, I am sorry!


omg LOL @ sudo apt-get moo

---

### Post by ren wins on 2005-11-19
funny
glxgears doesnt do anything different for me when i use -printfps or -iknowsomethingsomethingnobenchmark

---

