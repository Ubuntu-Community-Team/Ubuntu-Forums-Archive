---
title: "How to tell which Line Number??(In a File)"
date: 2008-12-09
forum: General Help
---

### Post by matey3 on 2008-12-09
Hi;

Can some one tell me how to go about reading only line number 117 of my.config file ,please?



I am getting an error message saying that my file has an error in it in line number 117.
I dont know how to grab that line number with nl command (and I cant stand vi).
vi is like roach motel you can go in easy but cant get out or come out, alive ;)
lol it makes me say  god bless dos 5 editor ;)
j/k..
thanks to you in advance!


Oh there is another dilemma, I assume the error message is saying line 117 of those lines which do NOT start with a # mark? Am I right? 
basically if somethign is being rem-ed out then the program doesnt read it? or does it? or depends?

Thanks a lot!

---

### Post by bogdan.veringioiu on 2008-12-09
Hi.

Sorry, but I give you the vi steps:

vi my.config

:117

And you go to line 117
To see the line numbers:
:set number

To exit
:q!

Bogdan

---

### Post by sdennie on 2008-12-09
You could also use head and tail for this:

```

tail -117 name_of_file | head -1

```

---

### Post by crwmike on 2008-12-09
Also, gedit can be set to display line numbers on the left margin.

---

### Post by taurus on 2008-12-09
```
vi +117 my.config
```
or
```
nano +117 my.config
```

---

### Post by phinullfermata on 2008-12-09
You could also use awk:

```
  awk 'NR==117' my.config 
```

---

### Post by matey3 on 2008-12-09
I give you all a Big Thank You!

I will jot all the replies down and use them. The vi is pretty cool, i knew it.
I know your help will make life so much easier...

P.S.
if you ever need road-side assistance just raise your hands and give me a 'V I' sign , I'll surely stop to help you!
:)
thanks very much!
Regards;

---

