---
title: "Help, with CHMOD"
date: 2009-04-23
forum: General Help
---

### Post by hankinator on 2009-04-23
I accidently Chmoded BIN, and now I can't access terminal to fix it. help!

I used the command
```
chmod -R 777 bin
```

---

### Post by inobe on 2009-04-23
+r

edit: i don't understand why you cannot access terminal ?

---

### Post by djbushido on 2009-04-23
did you have a file named bin, or were you in /usr?
I can't tell what happened.
Please post where you did this from.
However, you should be able to boot into a recovery mode and to a text-only fix. I believe the command you would want is "chmod -R u=rwx, go=rx bin"

---

### Post by JK3mp on 2009-04-23
Yeah i second the above let us know more specific of what you changed. Should be easily fixable. 
Once in terminal just sudo chmod *** file. *** replaced with the settings for permissions. And file being the file or folder you chmodded.

---

### Post by hankinator on 2009-04-23
Okay, I logged in as Root.

```
cd ..
chmod -R 777 bin
```
I did this in the main / directory.

so it got me to that main directory. I just need to access terminal. How would I get to the boot menu, when ubuntu is starting up?

---

### Post by JK3mp on 2009-04-23
If your really having problems acccessing terminal let us know what error you get when you try. If you can't open on click of menu. Try alt+f2 then type it in there. Just give us more to work with.

---

### Post by JK3mp on 2009-04-23
First off. DO NOT log in as root at anytime. I mean..thats pretty much what the sudo command is for. To temporarily give you root access. Loggin in as root isn't very safe and you could mess some shizz up. And as far as getting to grub why would you need to? What happens when you try to open terminal?
\

EDIT: Boot menu you would just hit enter when its about to load. If it loads instantly check your grub conf file (or lilo if you use it i guess)  and change it to set time b4 loading .

---

### Post by hankinator on 2009-04-23
Terminal Crash's with anything I try to run, um. Whats the command to see the grub loader? It doesn't show the grubb loader for me when it starts.

---

### Post by hankinator on 2009-04-23
Nvm, Im in recovery mode now. Let me try to fix it.

---

### Post by JK3mp on 2009-04-23
Press the esc key upon booting of computer.


--Nevermind this then.

---

### Post by hankinator on 2009-04-23
I'm going to have to reinstall.
Its unable to access the bin directory at all. so well yeah.

---

