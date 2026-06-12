---
title: "Need help to create an .sh or .bin file"
date: 2009-03-29
forum: General Help
---

### Post by ajmujaa on 2009-03-29
Hi all,

I have develop Java a program which could be run on both windows and unix/linux operating systems. I could create a .exe file for windows platform. Is there anybody know how to create .bin or .sh for using the .jar file to unix/linux based operating systems.

Please hope a reply from you guys as soon as possible,

Thanks in advance

---

### Post by cwsnyder on 2009-03-29
It would seem to me that the best way to release it for Ubuntu would be in the form of the .jar file.
A .sh file would be not in Java, but in the shell language, and the .bin form would not have dependencies satisfied.  You really should create a .deb file if you do not want to release the source under GPL, but then you should put a notice that the program is not FOSS, and what license you wish to release the executable under.

---

### Post by 3Miro on 2009-03-29
.bin files are Binary files, I don't think this is what you want. How do you run the jar file, I am assuming something along the lines of: java HelloWorld.jar?

In general, you can do the following, given a command
```

java HelloWord.jar

```
you can create a script file say HelloWorld.sh
```
pico HelloWorld.sh
```
Then put the following in it:
```
java HelloWord.jar
```
save the file, then set the permissions:
```
chmod 700 HelloWorld.sh
```

You can evoke it by:
```
./HelloWorld.sh
```
and that would execute the commands that you had in. I have such scripts that would cd into a folder and run a specific command with some parameters by just typing ./something_short.

---

### Post by wallydallas on 2009-05-26
very well written advice.  Thanks!

---

