---
title: "Installing a .run file"
date: 2006-06-24
forum: Desktop Environments
---

### Post by Gorbachev on 2006-06-24
So, I've ran into another wall.

I'm trying to install Wolfenstein: Enemy Territory, file named et-linux-2.55.x86.run

It's great, I just had to make it executable and all i've gotta do is double click it. It checks its integrity, then asks for my password. I enter it, like I do every time I log into Ubuntu...

Authentication failed?!?!

This is seriously making me mad. I am the admin/root whatever of this computer and I can't install my own crap.


What have I done wrong?

---

### Post by adwait on 2006-06-24
Maybe it is trying for root access which is by default disable in ubuntu? Try running it using
```
sudo ./<filename>
```

If that doesn't help, then you may need to enable the root account with
```
sudo passwd
```

Now wen the installations asks you for the password enter the password that you set here.

---

### Post by Gorbachev on 2006-06-24
Aye, thanks a bunch, but now I have another problem.

Is the following file a file within the .run file? Perhaps the download is corrupt and I simply need to redownload it?


> The setup program seems to have failed on x86/glibc-2.1

I'll check package manager.

***edit**: So I ran the setup again, I'll copy here verbatim the message it gives me:

```
/root/.setup5064: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory /tmp/selfgz4946/setup.sh: line 143: 5087 Segmentation fault "$setup" "$@" 2>>$NULL
The setup program seems to have failed on x86/glibc-2.1

See http://zerowing.idsoftware.com/linux/ for troubleshooting.
Press Return to close this window...
```

I suppose my next step whilst awaiting an answer is to find and download "libgtk-1.2.so.0".. so, i'll update this after that.

---

### Post by Gorbachev on 2006-06-25
Answer found here: [http://www.ubuntuforums.org/archive/index.php/t-22413.html](http://www.ubuntuforums.org/archive/index.php/t-22413.html)

Used package manager to install libgtk1.2 and the "common" one below it.

**It works!!**

Thanks for all the help, very great forum.

---

