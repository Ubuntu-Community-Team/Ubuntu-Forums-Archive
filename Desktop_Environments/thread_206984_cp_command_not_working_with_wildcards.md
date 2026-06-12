---
title: "cp command not working with wildcards"
date: 2006-06-30
forum: Desktop Environments
---

### Post by mooreted on 2006-06-30
For some reason, if I cd into a directory then enter "cp *.mpg /movies" I get an error: invalid option".

Why is the cp command not letting me do wildcards?

---

### Post by WW on 2006-07-01
A shot in the dark: do any of the .mpg file names begin with a dash? E.g. "-movie-.mpg", or something like that.

---

### Post by mooreted on 2006-07-01
No. When I boot into OSX the cp command works fine. I used the same command on the same directory with the same files in OSX and everything copied.

Could it be a problem caused by copying from an HFS+ partition to an EXT3 partition?

---

### Post by leech on 2006-07-01
You could try *mpg (without the . in it) and see if that works.  Kind of an odd thing, though I don't know how HFS handles wild cards, I know Linux doesn't do it the same as Dos with the *.* being needed, usually you can just use *mpg and anything ending in mpg will be copied.

Leech

---

### Post by mooreted on 2006-07-01
Thanks. I tried that too and got the same error. I have been using Unix OS's for years and never had this happen. It's very strange. All I can think of is that the error is wrong. It's actually a permission problem of some sort. Though Nautilus didn't have any problem copying the files and I did make the folder world-writable.

I just don't know.

As far as OSX, it uses the same command-set as any other Unix distro. It has some of it's own unique commands, but it's still Unix.

---

### Post by jimbob on 2006-07-01
Works for me.  Check this procedure:

root@SDA1:/home/jaspmatt# touch ab.mpg
root@SDA1:/home/jaspmatt# touch xy.mpg
root@SDA1:/home/jaspmatt# touch ij.mpg
root@SDA1:/home/jaspmatt# cd /
root@SDA1:/# mkdir testdir
root@SDA1:/# chmod 666 testdir
root@SDA1:/# cd testdir
root@SDA1:/testdir# cp /home/jaspmatt/*.mpg .
root@SDA1:/testdir# ls
ab.mpg  ij.mpg  xy.mpg
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by mooreted on 2006-07-01
I just used the cp command as in "cp *jpg temp" natively on the Ubuntu partition and it worked as it's supposed to. It must be an issue with the HFS partition.

Thanks for the help.

---

### Post by mooreted on 2006-07-01
I just discovered that ls doesn't work on the HFS partition either. I enter "ls *jpg" and get "invalid option". This is really strange. Well, it's something to investigate.

---

### Post by mooreted on 2006-07-01
Ah Ha! I can cd into other directories on the HFS partition and the cp and ls commands work fine. It is something specific to that directory.

A clue Watson!

---

### Post by mooreted on 2006-07-01
[QUOTE=WW]A shot in the dark: do any of the .mpg file names begin with a dash? E.g. "-movie-.mpg", or something like that.[/QUOTE]


You were right. I found a file like -filename.mpg. Renamed and it's working. cp must thing the - was a parameter.

Thanks for the help. I really appreciate it.

---

