---
title: "Make shell script to run like a program from anywhere"
date: 2009-02-19
forum: General Help
---

### Post by nolanpro on 2009-02-19
I'm trying to get a shell script (or bash script) to run in the shell from any directory that I'm in. The actual script is

```
grep -r -H -o -i -l "$1" *
```

I don't want to type that in every time I want to search so it would be great if I could make it execute like "grep" does no mater what directory you are in

Hopefully it will also inherit the directory you are in so it only searches directories under when it happens to be run.

Any help would be very awesome!

---

### Post by mb_webguy on 2009-02-19
```
#! /bin/sh
grep -r -H -o -i -l "$@" *
```

Create that script, name it whatever you want.  For this example, I'll use "grepit".  (Btw, I changed "$1" to "$@" so that it will accept file or directory names containing spaces.)  Now create a directory named "bin" in your home directory ("mkdir ~/bin").  Move the file to this directory ("mv grepit ~/bin/") and make it executable ("chmod u+x ~/bin/grepit").

Now you can use "grepit" like a command.  You won't be able to use this as any other user (including root), however, unless you move it to someplace like /usr/bin or /usr/local/bin ("sudo mv grepit /usr/local/bin") and make it executable for everyone ("sudo chmod a+x /usr/local/bin/grepit").  You should probably also make it owned by root ("sudo chown root:root /usr/local/bin/grepit").

---

### Post by anlag on 2009-02-19
Just a small addendum: I believe that the ~/bin directory is only included in PATH (the list of locations searched for executable files) if it exists at log-on (see comments in ~/.profile). Thus if the new shell script program isn't found immediately after its creation, the OP could simply reboot to make it work - or manually add the directory to PATH, just the one time.

---

### Post by geirha on 2009-02-19
> **nolanpro said:**
> ```
grep -r -H -o -i -l "$1" *
```


If you replace that '*' with a '.', it will also search through hidden files and folders in the directory you're in when you run it.

---

### Post by fragos on 2009-02-19
Run "echo $PATH" in a terminal and you'll see which directories are searched for executable. /usr/local/bin will be in that list. It's created by the system as a place for users to place their own binaries.

---

### Post by Dr Small on 2009-02-19
> **fragos said:**
> Run "echo $PATH" in a terminal and you'll see which directories are searched for executable. /usr/local/bin will be in that list. It's created by the system as a place for users to place their own binaries.
Users are supposed to make their own ~/bin and add it to their $PATH

---

### Post by wowbagger53 on 2009-02-19
How about simply making an alias?

In your .bashrc ...

```
alias mygrep='grep -r -H -o -i -l "$1" *'
```

Leave out the * at the end if you like, and you can then specify the target on the fly. Just a thought.

---

### Post by Tek-E on 2009-02-19
If I understood correctly as to what you are asking all you should need to do is type.
```

sudo mv name_of_bash_script /bin/

```
then all you have to do is type the name of the script and it will run no matter what directory you are in.
If I failed to read what you asked correctly. please forgive me.

---

### Post by CrucifiedEgo on 2009-02-19
> **Tek-E said:**
> If I understood correctly as to what you are asking all you should need to do is type.
```

sudo mv name_of_bash_script /bin/

```
then all you have to do is type the name of the script and it will run no matter what directory you are in.
If I failed to read what you asked correctly. please forgive me.

This is generally not recommended.  /bin/ and /usr/bin/ should be reserved for package manager installed binaries.  /usr/local/bin/ is for system-wide custom binaries.  For the OP's situation, ~/bin is perfect.  If he wanted to make the command available to all users, then he could use /usr/local/bin.

---

### Post by makisupa123 on 2009-02-19
Seems like your 'script' is more of a command (with plenty of switches).  My extremely set-in-his-way former unix admin (of 25 years) boss would tell you that the bash alias that wowbagger53 suggested would be the proper way to do this.  FWIW...

--Mak

---

### Post by Tek-E on 2009-02-19
Okay im a little confused by what you said. Are you saying that the OP should use /bin/ and that my suggestion was correct or are you saying that he should /usr/local/bin and that my thinking was right but my path was wrong?? just a little confused.

---

### Post by apmcd47 on 2009-02-19
> **Tek-E said:**
> Okay im a little confused by what you said. Are you saying that the OP should use /bin/ and that my suggestion was correct or are you saying that he should /usr/local/bin and that my thinking was right but my path was wrong?? just a little confused.

OP's script is personal and should be in ~/bin or an alias as wowbagger53 suggested (my preference, too). /bin and /usr/bin should be left to the system packages and /usr/local/bin for packages compiled locally, but used by multiple users of the system.

Andrew

---

### Post by fragos on 2009-02-19
> **Dr Small said:**
> Users are supposed to make their own ~/bin and add it to their $PATH

That would certainly work but I what I sugesssted is correct as well. There are many ways to accomplish the same task in the Linux world. Too many to call all but one wrong.

---

### Post by nolanpro on 2009-02-19
Thanks guys, it worked right away to put it in ~/bin, i didn't have to modify PATH or anything. I'm going to look into the alias thing if that's the proper way to do this.

THANKS!!!!!

---

### Post by bodhi.zazen on 2009-02-19
> **nolanpro said:**
> Thanks guys, it worked right away to put it in ~/bin, i didn't have to modify PATH or anything. I'm going to look into the alias thing if that's the proper way to do this.

THANKS!!!!!

For "one liners" you want only for a single user (ie yourself) use an alias in ~/.bashrc (or anywhere you like).

For scripts you wish to use for a single user, use ~/bin

For scripts you wish to be available to multiple users, use /usr/local/bin

---

