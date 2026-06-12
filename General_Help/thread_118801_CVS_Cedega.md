---
title: "CVS Cedega"
date: 2006-01-17
forum: General Help
---

### Post by Pulshion on 2006-01-17
Im trying to install cvscedega and when i try to install it i get

```
Checking out CVS ... May take a while




--------- Error log - file /home/dmitriy/.WineCVS/sources/cvscedega/ErrorLog : ---------
/home/dmitriy/.WineCVS/Functions/RunWineCVS: line 736: cvs: command not found


Error in CVS checkout

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

```

Please Help
Thank you

---

### Post by RAOF on 2006-01-17
You haven't got all of the required packages to use the WineCVS script.  In particular, you don't have cvs.  You'll probably also have all sorts of other missing dependencies.

Fortunately, the [CVSCedega howto]("http://www.linux-gamers.net/modules/wfsection/article.php?articleid=45") has all the deps you need.  Particularly look at the "Debian" bit:

You need to run 
```
sudo apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev libsdl1.2-dev libsdl-ttf2.0-dev libsdl-net1.2-dev libsdl-gfx1.2-dev msttcorefonts libfontconfig1-dev
```

---

### Post by Pulshion on 2006-01-17
I got cedega working but when i go to install Steam, it goes to 100% of installation and then it says "Could not execute the externam program C:/Program Files/Steam/steam.exe"

This is how i started the isntall
```
dmitriy@linux:~$ /home/dmitriy/bin/cvscedega /home/dmitriy/Desktop/SteamInstall.exe

```

---

### Post by Pulshion on 2006-01-18
bump

---

### Post by RAOF on 2006-01-19
This might be better asked again in the "Ubuntu Gaming" subforum.  That's where all the people who can actually help you hang out ;)  I've never managed to install a game successfully with wine/cedega (but that's on a x86-64 system, so I'm in trouble from the start ;) )

---

### Post by ubu-for on 2006-06-03
[QUOTE=RAOF]
You need to run 
```
sudo apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev libsdl1.2-dev libsdl-ttf2.0-dev libsdl-net1.2-dev libsdl-gfx1.2-dev msttcorefonts libfontconfig1-dev
```[/QUOTE]

Error: "x-window-system-dev" not found!

How can I fix it?

---

### Post by ubu-for on 2006-06-04
Now I've installed WineCVS without "x-window-system-dev".

But everytime I try to start cvscedega, I get this error message:

```

bash: cvscedega: command not found

```

---

### Post by ubu-for on 2006-06-04
[QUOTE=ubu-for]
But everytime I try to start cvscedega, I get this error message:

```

bash: cvscedega: command not found

```
[/QUOTE]

Solution: "the cvscedega executable is in your ~/bin directory, just put it in your usr/local/bin directory or /usr/bin whatever."

---

### Post by 00arthuryu on 2007-04-08
i'm also trying to install cvscedega
```

--------- Error log - file /root/.WineCVS/sources/cvscedega/ErrorLog : ---------
/root/.WineCVS/Functions/DefaultProfile: line 628: ./configure: No such file or directory


Error in Configure

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

```
please help :(  thank you in advance :)

---

### Post by vlees91 on 2007-04-15
got the same....

---

### Post by rocketman768 on 2007-06-05
> **00arthuryu said:**
> i'm also trying to install cvscedega
```

--------- Error log - file /root/.WineCVS/sources/cvscedega/ErrorLog : ---------
/root/.WineCVS/Functions/DefaultProfile: line 628: ./configure: No such file or directory


Error in Configure

Try fixing the error based on the output above, and
run the script again, without paramaters (Eg: WineCVS.sh)

```
please help :(  thank you in advance :)

Yes. What is this?

---

### Post by rocketman768 on 2007-06-06
So, as an answer to the missing the configure file, I had to manually run "sudo bash ~/.WineCVS/sources/cvscedega/winex/setup.sh". This also requires you to have the autoconf package installed.

---

### Post by promet on 2008-01-20
NOTE:

On my system "setup.sh" is actually located in:

~/.WineCVS/sources/cvscedega/winex/setup.sh

and running:
```

sudo bash ~/.WineCVS/sources/cvscedega/winex/setup.sh
```

did allow me to complete my install, thanks for that tip!

---

