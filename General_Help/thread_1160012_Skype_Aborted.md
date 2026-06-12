---
title: "Skype: Aborted"
date: 2009-05-15
forum: General Help
---

### Post by TB2 on 2009-05-15
So, I installed Ubuntu for my girlfriend, thinking that it sure has the reputation of being a beginner friendly and well maintained distro. Now I know the ubuntu folks can't do much about the fact that skype is a pretty bad piece of software, but hopefully, you might still be able to help me.

**Porblem:**
When I launch skype (installed from medibuntu), a window briefly appears and then immediately crashes. The only output in the terminal is "Aborted".

```
lucullus@schatzkiste:~$ skype
Aborted
lucullus@schatzkiste:~$ 
```
[B]
Alread tried:[/B]
- Purging and reinstall
- Installing from skype repo
- Installing from skype homepage as package
- Deleting ~/.Skype

All without succes. It also seems like I can't make a backtrace (why??):
```
lucullus@schatzkiste:~$ gdb /usr/bin/skype
GNU gdb 6.8-debian
...bla bla bla...
This GDB was configured as "i486-linux-gnu"...
"/usr/bin/skype": not in executable format: File format not recognized
(gdb) 
```

If I create ~/.Skype/Logs then the binary log files are being created when launching.

Other than what I already tried I couldn't find any solutions. If someone has a skype .deb older than 2.0.0.72 could you please upload it somewhere so that I can try it out.

I really need skype to work on this machine. Can you please help me?

---

### Post by Lampi on 2009-05-15
> This GDB was configured as "i486-linux-gnu"...
"/usr/bin/skype": not in executable format: File format not recognized
(gdb)
makes me wonder if this binary for some weird reason is missing tripple r-x permissions. You could check that with
```
ls -la /usr/bin/skype
```
should at least look like this: -rwxr-xr-x 1 root root

but then again ... I don't think it's possible this gets mixed up from a clean install

---

### Post by TB2 on 2009-05-15
```
lucullus@schatzkiste:~$ ls -la /usr/bin/skype
-rwxr-xr-x 1 root root 77 2008-10-19 17:52 /usr/bin/skype
lucullus@schatzkiste:~$ ls -la /usr/bin/skype.real 
-rwxr-xr-x 1 root root 13859316 2008-10-19 17:52 /usr/bin/skype.real
lucullus@schatzkiste:~$
```
Looks fine.

---

### Post by tripolitan on 2009-05-15
Try this Ubuntu binary here:

[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)

There is also a lot of skype for Linux-specific topics in this forum:

[http://forum.skype.com/index.php?showforum=18](http://forum.skype.com/index.php?showforum=18)

---

### Post by TB2 on 2009-05-15
Are you kidding me? I appreciate your effort, but this is utterly useless advice:
> **tripolitan said:**
> Try this Ubuntu binary here:
[http://www.skype.com/download/skype/linux/choose/](http://www.skype.com/download/skype/linux/choose/)In my initial post I stated:
> **TB2]Alread tried:[/B]
- Installing from skype homepage as package
[/QUOTE]
and
[QUOTE=tripolitan said:**
> There is also a lot of skype for Linux-specific topics in this forum:
[http://forum.skype.com/index.php?showforum=18](http://forum.skype.com/index.php?showforum=18)
Oh wow, a link to the linux subforum on the skype homepage? I would never have thought of looking over there...

---

### Post by Kimm on 2009-05-17
> **TB2 said:**
> Are you kidding me? I appreciate your effort, but this is utterly useless advice:
In my initial post I stated:

and

Oh wow, a link to the linux subforum on the skype homepage? I would never have thought of looking over there...

Well, fixed it (and here is a quote from my own thread):

[QUOTE=Kimm]
Fixed it :)

Well, I fixed it. It was a UVC driver issue (which is the mother of all webcam related issued apparently).

I solved it by following the instructions on how to compile my own driver here: [https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC)[/QUOTE]

---

### Post by David7 on 2011-05-26
easy solition: check the userrights! 

/home/youruser/.Skype 

may be you started skype as root 
or maybe its a problem of the skype package that it doesnt set the **userrights** correct....
if userrights are correct then** mv shared.xml shared.xml.bak** start skype again but** not as root **should work!

---

### Post by soyatti on 2011-05-30
> **David7 said:**
> 
if userrights are correct then** mv shared.xml shared.xml.bak** start skype again but** not as root **should work!

thanks **David7**!
**mv shared.xml shared.xml.bak** cured my skype :)

[same on skype website]("http://heartbeat.skype.com/2011/05/problems_signing_into_skype_an.html")

i believe this is not related to drivers because on the same ubuntu installation skype worked under one account and was failing under another.

---

### Post by mastablasta on 2011-05-30
apparently it's a skype error that manifested in other OS as well (OS X and Windows). However it should be repaired by now with updates. if not removing the menitoned file will also solve it.

---

### Post by Russell John on 2011-06-02
> **David7 said:**
> if userrights are correct then** mv shared.xml shared.xml.bak** start skype again but** not as root **should work!
Thanks a bunch! I was unable to use Skype for a week now, thought that it was a bug and was waiting for a patch! Didn't realise that it's a local issue.

---

