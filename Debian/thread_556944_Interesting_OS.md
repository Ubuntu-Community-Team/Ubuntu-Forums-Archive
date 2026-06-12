---
title: "Interesting OS"
date: 2007-09-22
forum: Debian
---

### Post by ExSuSEusr on 2007-09-22
I installed Debian Etch on the laptop - been downloading different distros and playing around.

Very good OS, but a pain to work with it seems.  I will say it installed very smoothly - about as smooth as Slackware did.  SuSE wouldn't work (not surprised).  

Getting things working without having to spend hours upon hours searching for How To's is a different story.  However, I like it enough that I think I'll keep it installed for a while!

---

### Post by kerry_s on 2007-09-22
so what are you stuck on?
which 1 did you go for? gnome, kde, xfce4, other

i use xfce4, i have mine upgraded all the way up to sid.

my sources.list->

```
deb http://ftp.debian.org/debian/ etch main contrib non-free 
deb http://ftp.debian.org/debian/ lenny main contrib non-free 
deb http://ftp.debian.org/debian/ sid main contrib non-free 
deb http://www.debian-multimedia.org/ sid main 

# su
# gpg --keyserver subkeys.pgp.net --recv-key 6A423791
# gpg --armor --export  6A423791| apt-key add -
deb http://deb.opera.com/opera/ sid non-free 
deb http://deb.opera.com/opera-beta/ unstable non-free  

deb http://security.debian.org/ etch/updates main contrib non-free 
deb http://security.debian.org/ lenny/updates main contrib non-free 

# deb-src http://ftp.debian.org/debian/ etch main contrib non-free 
# deb-src http://security.debian.org/ etch/updates main contrib non-free 
# deb-src http://ftp.debian.org/debian/ lenny main contrib non-free 
# deb-src http://security.debian.org/ lenny/updates main contrib non-free 
# deb-src http://ftp.debian.org/debian/ sid main contrib non-free 

```

---

### Post by ExSuSEusr on 2007-09-22
Oh, I was just trying something simply like copying a folder from /home to a protected directory like /usr.

I am still used to SuSE where all you gotta do is switch users to root and you can do whatever you need... then switch back to user.

I am still not quite used to not being able simply click and switch from user to root...

Was trying to get the Java jre installed to run frostwire.  I have the repositories set up right - but it still can't find it. 

Otherwise everything is working pretty smoothly.

Oh I use Gnome.

---

### Post by kerry_s on 2007-09-22
did you install synaptic(su & apt-get install synaptic) and add the "contrib non-free"(gksudo gedit /etc/apt/sources.list) to your sources line?
for root access i just make some right click entries, you can do the same with nautilus scripts.

pic->

---

### Post by ExSuSEusr on 2007-09-23
Having problems with the respositories.  I am getting this error message:

> E: Type 'http://ftp.debian-unofficial.org/debian/' is not known on line 12 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.When I run gksudo gedit /etc/apt/sources.list I see:

> # 
deb cdrom:[Debian GNU/Linux 4.0 r1 _Etch_ - Official i386 CD Binary-1 20070819-11:52]/ etch contrib main

deb cdrom:[Debian GNU/Linux 4.0 r1 _Etch_ - Official i386 CD Binary-1 20070819-11:52]/ etch contrib main

deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) etch main
deb-src [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) etch main

deb [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib
deb [http://http.us.debian.org/debian/](http://http.us.debian.org/debian/) sarge main
deb-src [http://security.debian.org/](http://security.debian.org/) etch/updates main contrib
[http://ftp.debian-unofficial.org/debian/](http://ftp.debian-unofficial.org/debian/)
deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) etch main contrib non-free
deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) lenny main contrib non-free
deb [http://ftp.debian.org/debian/](http://ftp.debian.org/debian/) sid main contrib non-free
deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) sid mainYep, I have Synaptic installed.  When I try to *find* any particular program to install - I get the error mentioned above.

I'm digging this distro - but have never used it before - so bear with me! :)

So, I tried to remove line 12 and just get is not known on** line 11** in source list /etc/apt/sources.list instead...

---

### Post by kerry_s on 2007-09-23
whoa, your sources.list is all screwed up. make it look like this->

```
#deb cdrom:[Debian GNU/Linux 4.0 r1 _Etch_ - Official i386 CD Binary-1 20070819-11:52]/ etch contrib main

deb http://ftp.debian.org/debian/ etch main contrib non-free
deb http://security.debian.org/ etch/updates main contrib non-free
deb http://ftp.debian.org/debian/ lenny main contrib non-free
deb http://security.debian.org/ lenny/updates main contrib non-free
deb http://www.debian-multimedia.org/ lenny main 

#deb-src http://ftp.debian.org/debian/ etch main contrib non-free
#deb-src http://security.debian.org/ etch/updates main contrib non-free
#deb-src http://ftp.debian.org/debian/ lenny main contrib non-free
#deb-src http://security.debian.org/ lenny/updates main contrib non-free

```

then in terminal
su
apt-get update

then you should be able to open synaptic.

don't use sid yet, your not ready for sid, sid is the unstable branch of debian. it's where they start working out the bugs, so you can always expect problems with sid. you don't need the deb-src on all the time, there for compiling, which there is no need for.

---

### Post by ExSuSEusr on 2007-09-23
Ahh much much better.

Thanks!

Strange - the original list I posted was unaltered after the initial install.

Oh well, Synaptic working now... running all updates and will deal with Frostwire after.

Thanks...

---

### Post by kerry_s on 2007-09-23
no problem, make sure you grab the java before you install frostwire(dpkg -i name-of.deb).

---

