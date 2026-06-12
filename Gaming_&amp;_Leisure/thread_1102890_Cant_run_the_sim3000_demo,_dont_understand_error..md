---
title: "Cant run the sim3000 demo, dont understand error."
date: 2009-03-22
forum: Gaming &amp; Leisure
---

### Post by WOOHOOHOO on 2009-03-22
Hi guys,

I wanted to try the free demo of sim3000 Unlimited (linux). I downloaded it legally from [http://www.fileshack.com/file.x/778/SimCity+3000+Unlimited+Demo+(Linux](http://www.fileshack.com/file.x/778/SimCity+3000+Unlimited+Demo+(Linux)).

It downloads one file after unzipping, called 'sc3u-demo-x86.run'. The instructions to install were just to unpack, set permissions, and click the .run file. On doing this, it opens a terminal and starts to install. It creates a folder in my home folder with called 'sc3u_demo' and then crashes, saying the following:

[COLOR="Navy"]"jamie@jamie-laptop:~$ sh sc3u-demo-x86.run
Creating directory sc3u_demo
mkdir: cannot create directory `sc3u_demo': File exists
sc3u-demo-x86.run: line 119: Cannot create target directory: command not found
sc3u-demo-x86.run: line 120: you should perhaps try option -target OtherDirectory: command not found"[/COLOR]


Can anyone tell me what to do please?

I run Ubuntu 8.04.

---

### Post by ELD on 2009-03-22
The problem seems to be this
"mkdir: cannot create directory `sc3u_demo': File exists"

The installer is trying to make "sc3u_demo" folder by the looks of it and it already exists.

---

### Post by WOOHOOHOO on 2009-03-22
> **ELD said:**
> The problem seems to be this
"mkdir: cannot create directory `sc3u_demo': File exists"

The installer is trying to make "sc3u_demo" folder by the looks of it and it already exists.

See, there was no folder. When i click the run file, it creates the folder at that point, and then says it cant continue as folder arealy exists, even though it made it itself. mmmm.

---

### Post by ELD on 2009-03-22
Where did you get the download from exactly? It may be a bug in the installer which would need to be reported.

---

### Post by WOOHOOHOO on 2009-03-23
i got the file from [www.fileshack.com/file.x/778/SimCity+3000+Unlimited+Demo+(Linux](www.fileshack.com/file.x/778/SimCity+3000+Unlimited+Demo+(Linux)). 

it was a link from another site (cant find it exactly) but it seemed an offical site.
Should i email fileshack?

J.

---

### Post by fixitdude on 2009-03-23
I would watch out for scripts that don't come directly from the company that makes that game. You never know what they may be doing.

However, the installer may be a simple shell script and so you can modify it if you are careful.

You need to read the errors line by line very carefully and slowly when trying to figure out what is wrong.

If the directories it needs exist already it may be the simple solution for you to just comment out the mkdir lines in the shell script.

And you really should open a terminal and run this thing from there instead of just clicking on it, that way you know where it's running from and that it has the proper working directory.

To go on and on and explain further, when you just click on something and run it it probably executes in the base directory for your user, and if you look there you will probably find that folder is there instead of where you think it should be.

Plus, the guy who created the shell script should have read the man page and used the "-p" option so it doesn't throw an error.

---

### Post by Perfect Storm on 2009-03-23
I agree with fixitdude. Be very careful, who knows if there's backdoors.

---

### Post by ELD on 2009-03-23
I will probably give the file a go in a day or two and see what happens to see if i can help at all.

---

### Post by WOOHOOHOO on 2009-03-25
that would be useful, let me know if you try please.

I tried to run through the terminal also, and the same thing happened.

---

