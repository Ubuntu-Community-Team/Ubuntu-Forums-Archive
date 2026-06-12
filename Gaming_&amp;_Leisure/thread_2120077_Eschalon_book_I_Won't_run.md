---
title: "Eschalon book I Won't run"
date: 2013-02-25
forum: Gaming &amp; Leisure
---

### Post by remo88 on 2013-02-25
Hello all,
I am not sure if this is the right place but it seems like it.
I am trying to play the game "Eschalon book I" (As the title suggested :P. It has a linux native client but for some reason the game won't run. According to the terminal, when I am trying to run the game it says that the shared file or folder libfreetype.so.6 is missing. I check the /usr/lib directory and I didn't find anything like that file there.

I was wondering what is that file, where can I get it? I tried to Google it but didn't find anything conclusive. I would appreciate any help. I am new you linux and I am using the latest Lubuntu (due to it's low system demands)  

Thanks in advance.

---

### Post by Perfect Storm on 2013-02-25
Install libfreetype6 should do the trick.

---

### Post by remo88 on 2013-02-25
Ok.. I am getting the following error:

install: missing destination file operand after `libfree.so.6'
Try `install --help' for more information.

does the same with the libfreetype6

What now?

I also used the package downloader to download the libfreetype 6 but still doesn't help. Does anybody know where the package downloader download the file? maybe I need to move them manually to /usr/lib folder?

please Help

---

### Post by Perfect Storm on 2013-02-25
Are you running 64-bit version of Ubuntu?

---

### Post by remo88 on 2013-02-26
Yes. Now I am facing a new problem, I have found the "Symbolic link" of the file and copied it to my usr/lib library. But I am still getting the same error "no such directory" I am really lost here lol :)

Anyways, I also found the same symbolic file in the folder x86_64-linux-gnu and copied it to my usr/lib folder but still getting the same error.

Please help :)

Edit: Ok new error. I have found the file that the symbolic link leads to and copied it too to /usr/lib folder. Not when I try to run the game I get the following error:
 error while loading shared libraries: libfreetype.so.6: wrong ELF class: ELFCLASS64
I assume the game requires 32bit version of these files but where do I find them? and how do I use them?

---

### Post by Perfect Storm on 2013-02-26
You can't use a 64-bit lib for a 32-bit app. delete the symblink. 

You need to install 32-bit libs to the system, make sure you deleted thte symblink first, then;

```
sudo apt-get install ia32-libs
```

---

### Post by remo88 on 2013-02-26
Do I delete it from the /lib folder or from the x86_64-linux-gnu? or both?
also delete the file the symblink points to?

---

### Post by Perfect Storm on 2013-02-26
Delete the symblink you made and the libs you copied to the different places.
But do not delete original files/symblinks etc.

---

### Post by remo88 on 2013-02-26
Ok something new now:

X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  25
  Current serial number in output stream:  26

---

### Post by Perfect Storm on 2013-02-26
Seems it needs 3D rendering. Which video card do you have (sounds like intel?)?

---

### Post by remo88 on 2013-02-26
Yeah. I am using an AMD internal card.. I have a mini pc.
Anyhow, I fixed this problem using the original drivers via the software sources. Though I do have a question. How can I know if the drivers the lubuntu uses are the correct one?

---

### Post by Perfect Storm on 2013-02-26
> **remo88 said:**
> Yeah. I am using an AMD internal card.. I have a mini pc.
Anyhow, I fixed this problem using the original drivers via the software sources. Though I do have a question. How can I know if the drivers the lubuntu uses are the correct one?

Well, if the resolution, 3D gaming (depending on the card) and performance is okay. Then it's properly the correct driver, and if it aren't you properly see weird behaving or it won't boot into your desktop. ;)
Otherwise your card manufacture have a list which driver supports X,Y,Z card.

Ubuntu comes with open source driver default, they can't put the restricted driver into ubuntu by default as they don't have the rights etc. etc.

---

