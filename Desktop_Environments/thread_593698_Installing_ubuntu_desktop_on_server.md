---
title: "Installing ubuntu desktop on server"
date: 2007-10-27
forum: Desktop Environments
---

### Post by madmagic on 2007-10-27
Ok i just got ubuntu server 7.10, now im basicly wanting to turn it into a remote logon, so i need to find out how to put a desktop on it. any help would be nice :)

Edit:
I have tried sudo apt-get install ubuntu-desktop
i get a error saying
E: Couldn't find package ubuntu-desktop

---

### Post by taurus on 2007-10-27
```
**sudo apt-get update**
sudo apt-get install ubuntu-desktop gdm
```
Otherwise, post your /etc/apt/sources.list here.

```
cat /etc/apt/soures.list
```

---

### Post by madmagic on 2007-10-27
k so doing the sudo apt-get still doesnt work, same error.
now when i try to get the sources i get a 
cat: /ect/apt/sources.list: No such file or directory
error.

Edit:
When i do sudo apt-get update i get a error saying
err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security release.gpg
 Tempoary failure resolving 'security.ubuntu.com'

aswell i get afwe more errors -_-

---

### Post by taurus on 2007-10-27
> **madmagic said:**
> k so doing the sudo apt-get still doesnt work, same error.
now when i try to get the sources i get a 
cat: /ect/apt/sources.list: No such file or directory
error.

Edit:
When i do sudo apt-get update i get a error saying
err **[COLOR="Blue"][http://security.ubuntu.com](http://security.ubuntu.com) dapper-security release.gpg[/COLOR]**
 Tempoary failure resolving 'security.ubuntu.com'

aswell i get afwe more errors -_-

Didn't you say you are running Gutsy?  Does is Dapper doing in there?

You need to check your typing because it is

```
cat /**[COLOR="Blue"][SIZE="4"]etc[/SIZE][/COLOR]**/apt/sources.list
```

---

### Post by madmagic on 2007-10-27
i thought i wasm but it says im running dapper -_- ok so what now?

PS. I wont reply for about an hour, i need to go out.

---

### Post by taurus on 2007-10-27
Post the output of this command!

```
cat /etc/apt/sources.list
```

---

### Post by madmagic on 2007-10-27
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-seurity main resricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-seurity main resricted
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by taurus on 2007-10-27
> **madmagic said:**
> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-seurity main resricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-seurity main resricted
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

That's all there is for /etc/apt/sources.list!  And you said you just install Gutsy, 7.10, on your machine?  There is some major problem going on here.

---

### Post by madmagic on 2007-10-27
theres more but i didnt think it would be needed, the rest of it is just sayinh iys been tested blah blah blah backports will not receive any review and stuff like that. im farly new to this so cut me some slack -_-:confused:

---

### Post by taurus on 2007-10-27
I am trying to help you to figure out what's wrong or why you can't install Gnome so if you don't want to include the whole file, then that's fine.  It's all up to you.

---

### Post by madmagic on 2007-10-27
k this is what i see on my screen,
## team, and may not be under a free licence. Please satisfy yourself as to your gihts to use the software. Also please not that under software in universe WILL NOT receive any review or updates from the Ubuntu security Team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

Uncomment the following two lines to add software from the 'backports' repository.
N.B. software from this repository may not have been tested as extensively as that contained in the main release, although it includes newer versions of some applications which may provide useful features. Also please note that sofware in backports WILL NOT reveive any review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-seurity main resricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-seurity main resricted
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe 



PS: Im also using linux kernal 386 becuase of my old computer.

---

### Post by madmagic on 2007-10-27
~bump

---

