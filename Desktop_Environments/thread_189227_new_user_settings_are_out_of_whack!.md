---
title: "new user settings are out of whack!"
date: 2006-06-04
forum: Desktop Environments
---

### Post by uzi09 on 2006-06-04
hey all, this is really starting to frustrate me.

i've created a new user account so that if anyone else wants to use my computer, they can use the limited account. the only problem is, for some reason, half the things don't work properly.

off the top of my head, i recall that there is NO SOUND. i always get an error saying something about the gstreamer plugin is not installed and the sound always is muted.

the main account that was created with the installation works like a charm. no problems at all.

i've tried to remove the user, add it again, but the problem presists. i don't know whether it's a problem with permissions or perhaps the fact that when i installed software to get things running (although for sound, it worked out of the box), it put it in a place so that it's only available to the main user. but i really don't think it is the latter because i used aptitude for it.

so i don't know what is worng with it and i'm hoping you guys can help.

thanks

---

### Post by aysiu on 2006-06-04
Make sure your new user belongs to the same groups as your old user (well, except *admin*, of course).

*username* dialout cdrom floppy audio dip video plugdev lpadmin scanner

---

### Post by uzi09 on 2006-06-06
and aysiu saves the day again! ;)

lol thanks. one thing though, i remember in breezy there was a gui available for this stuff. is there one still available in dapper?
and secondly, do you know of any good tutorials/articles that explain users and their groups? i'd like to find out if there are any others.

thanks,
uzi

---

### Post by aysiu on 2006-06-06
[QUOTE=uzi09]i remember in breezy there was a gui available for this stuff. is there one still available in dapper?[/quote] Yes. See the attached screenshot. > and secondly, do you know of any good tutorials/articles that explain users and their groups? i'd like to find out if there are any others. No idea, but if you find one, please post it here.

---

### Post by Patsoe on 2006-06-06
[QUOTE=uzi09]
and secondly, do you know of any good tutorials/articles that explain users and their groups?
[/QUOTE]
I have a book with a good section on that... it is the "Debian GNU/Linux 3.1 Bible", ISBN 0-7645-7644-5. It is not as in-depth as the name suggests, but it definitely covers a lot of topics. Hope your local library is GNU-minded :)

---

### Post by uzi09 on 2006-06-07
@aysiu: oh crap, can't believe i overlooked that](*,) 

@patsoe: thanks very much, i'll be sure to check that out.

---

### Post by temcat on 2006-06-07
BTW note that in Ubuntu, users can read each other's files by default. I was shocked to know that (the distro I used previously restricted read access to other users' directories).

---

### Post by WorLord on 2006-06-07
@temcat: I was actually pleasantly surprised to find this out.  I remember thinking "It's about time!".

---

### Post by uzi09 on 2006-06-10
so i finally got around to getting this problem fixed....GUESS WHaT?!

I DIDN'T OVERLOOK IT! :(

I'm just missing it all together :evil: (see attached pic)

does anyone know what the command is to run it from command line?

---

### Post by aysiu on 2006-06-10
That's weird. The command is ```
gksu users-admin
```

---

### Post by uzi09 on 2006-06-10
hmm, so apparently, i don't even have the program on my ubuntu anymore :S.

nor can i apt-get/aptitude it :( - wth is going on!??!

---

### Post by aysiu on 2006-06-10
That's weird. I don't even know what package the command belongs to.

As a weird workaround, you can try this: ```
sudo aptitude update
sudo aptitude install kuser
gksudo kuser
```

---

### Post by uzi09 on 2006-06-10
k, so i'll give that a try and get that working, but to resolve the whole issue, any ideas what to do? perhaps a fresh install is required? (although i was hoping to avoid this as much as possible).

---

### Post by aysiu on 2006-06-11
For any new users you create, make sure they belong to these groups:

dialout 
cdrom 
floppy 
audio 
dip 
video 
plugdev 
lpadmin 
scanner

---

### Post by uzi09 on 2006-06-11
thank you, i'll make sure of that, but what i meant to say in the last post -- things seem to be missing which is really weird.

i've had problems with the log out button as well, and so far the only 2 things people seem to think it may be is:
1) the theme
2) aiglx that i installed (okay, well i'm the only one thinking it)

i really like both of these things, do you think perhaps i should just try to reinstall and try again? or do you think there is a way around it?

---

### Post by aysiu on 2006-06-11
There's probably a way around it. Maybe someone more knowledgeable than I can chime in.

---

