---
title: "trouble starting .bin files"
date: 2006-06-10
forum: Desktop Environments
---

### Post by digimars on 2006-06-10
I keep getting errors like these when I try to run .bin files:

```

kenny@Archimedes:~/Desktop$ ./TorqueGameEngineSDK-1.4.2-RC1.bin
bash: ./TorqueGameEngineSDK-1.4.2-RC1.bin: Permission denied

kenny@Archimedes:~/Desktop$ sudo TorqueGameEngineSDK-1.4.2-RC1.bin
sudo: TorqueGameEngineSDK-1.4.2-RC1.bin: command not found

```

This is an installation file (I believe) for the Torque Game Engine that is located on my desktop.  I've tried at their forums to no avail.  So I figured that it is just a basic noobie Linux problem of not knowing how to install this file.

---

### Post by zugu on 2006-06-10
Try putting using the sh command as this:

```

sh TorqueGameEngineSDK-1.4.2-RC1.bin

```
or
```

sudo sh TorqueGameEngineSDK-1.4.2-RC1.bin

```

---

### Post by digimars on 2006-06-10
[QUOTE=zugu]Try putting using the sh command as this:

```

sh TorqueGameEngineSDK-1.4.2-RC1.bin

```
or
```

sudo sh TorqueGameEngineSDK-1.4.2-RC1.bin

```[/QUOTE]


Thanks for the reply, but this is what I get:

```

kenny@Archimedes:~/Desktop$ sh TorqueGameEngineSDK-1.4.2-RC1.bin
TorqueGameEngineSDK-1.4.2-RC1.bin: TorqueGameEngineSDK-1.4.2-RC1.bin: cannot execute binary file
kenny@Archimedes:~/Desktop$ sudo sh TorqueGameEngineSDK-1.4.2-RC1.bin
TorqueGameEngineSDK-1.4.2-RC1.bin: TorqueGameEngineSDK-1.4.2-RC1.bin: cannot execute binary file

```

---

### Post by zugu on 2006-06-10
This is another issue. If you downloaded the file, it may be that it became corrupt during the transfer. That's why CRC checks are for. Don't know how you acquired the file (browser? bit-torrent?). if you got it from bit-torrent, try getting it again, but don't forget to activate the "Verify files after download" or similar option in your client.
If you got the file through a browser, empty the browser's cache and try downloading it again.

Then run the file again and see what happens.

Later edit: if you're using the 64 bit Ubuntu version, this might be an issue of additional software you need to install on your system and / or further configuring and tweaking your system. Unfortunately, my knowledge of the 64 bit Ubuntu version is limited, so maybe someone else could help you.

---

### Post by bruce89 on 2006-06-10
Are the files executable?

---

### Post by digimars on 2006-06-10
According to the command line, it is an executable file.

OK, redownloaded the file.  Tried to execute from the desktop:

```

kenny@Archimedes:~/Desktop$ ./*.bin
bash: ./TorqueGameEngineSDK-1.4.2-RC1.bin: Permission denied

kenny@Archimedes:~/Desktop$ sh ./*.bin
./TorqueGameEngineSDK-1.4.2-RC1.bin: ./TorqueGameEngineSDK-1.4.2-RC1.bin: cannot execute binary file


```

How can I do this without being root?

---

### Post by peertje on 2006-06-10
[COLOR=#EE5500]I had the same problem. By searching around in this forum I discovered that the file didn't have any execution rights, did you check that?
After chmodding the file, sudo ./filename.bin worked for me ;) [/COLOR]

---

### Post by digimars on 2006-06-10
> **peertje][COLOR=#EE5500]I had the same problem. By searching around in this forum I discovered that the file didn't have any execution rights, did you check that?
After chmodding the file, sudo ./filename.bin worked for me  said:**
> 


Thanks!  That's what it took, I just right clicked on the file and saw that "Execute" was not checked, checked it and all is well now.  I'm still a basic Linux noob, so there are a lot of things like this that I didn't know about.

---

