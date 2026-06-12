---
title: "cant log in HELP PLEASE"
date: 2006-06-19
forum: Desktop Environments
---

### Post by Hg80 on 2006-06-19
I have had this problem for a few days now and have even been told to delete .ICEauthority which i have done.
basicly when i log in under X i get a message telling me my last login lasted 10 seconds and below viewing further info gives me this:
```
/etc/gdm/presession/Defult: Registering your session with wtmp and utmp
/etc/gdm/presession/Defult: running: /usr/bin/session -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0 Xsevers" -h" -l" :0" "hg"
/etc/gdm/xsession : Beginning Session setup...
mkdtemp: private sokectdir permission denied
```

Please help me resolve this as im using windows till i can log into ubuntu

---

### Post by John Jason Jordan on 2006-06-20
[QUOTE=Hg80]I have had this problem for a few days now and have even been told to delete .ICEauthority which i have done.
basicly when i log in under X i get a message telling me my last login lasted 10 seconds and below viewing further info gives me this:
```
/etc/gdm/presession/Defult: Registering your session with wtmp and utmp
/etc/gdm/presession/Defult: running: /usr/bin/session -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0 Xsevers" -h" -l" :0" "hg"
/etc/gdm/xsession : Beginning Session setup...
mkdtemp: private sokectdir permission denied
```

Please help me resolve this as im using windows till i can log into ubuntu[/QUOTE]
Ah, I think I had this the first time I got the "ten seconds" error message. I was at the university and desperate, because I had homework on the computer I needed to hand in!

Anyway, I went to the Computer Lab where they have all kinds of computer science students working as interns to help students with their computers. A nice fellow who was an expert in Linux told me that the problem was permissions on some folder. He gave me the command line code to change the permissions, and then it worked. Unfortunately, I did not write down the command he gave me, and I'm too new to Linux to know it. I think it was "chmod," but there were other things after it. Thinking hard, it may have been

sudo chmod jjj:jjj (followed by the folder where .ICEauthority is)

In my case, I am user jjj of the group jjj. I know I never created the group "jjj," so that must be a default. You will need to change "jjj:jjj" to make it refer to yourself. 

The line above is probably wrong, but if you try it and read about chmod maybe you can figure it out. Or maybe someone else with more experience will see this and give you better instructions.

---

### Post by Hg80 on 2006-06-21
hay thanks for the help i fixed this problem by Ctrl-Alt-F1 and sudo chmod 775ed a few folders

---

