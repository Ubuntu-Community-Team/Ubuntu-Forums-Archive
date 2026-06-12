---
title: "How do I open Download Swiftfox: swiftfox-1.5.0.4-pentium3.tar.bz2"
date: 2006-06-03
forum: Desktop Environments
---

### Post by RAV TUX on 2006-06-03
I have downloaded [[IMG]http://getswiftfox.com/images/tar.jpg[/IMG]]("http://getswiftfox.com/builds/releases/swiftfox-1.5.0.4-pentium3.tar.bz2") [swiftfox-1.5.0.4-pentium3.tar.bz2]("http://getswiftfox.com/builds/releases/swiftfox-1.5.0.4-pentium3.tar.bz2") but when I drag and drop it in the terminal it says it is just a directory:

How do I get Swiftfox up and running on Ubuntu 6.06 ?






.

---

### Post by angkor on 2006-06-03
double-click the tar.bz2 to extract the contents. There's a swiftfox-bin in the newly created swiftfox dir. You can run it from the terminal:

```
cd swiftfox
./swiftfox-bin
```

Also read this thread if you like it and want to make it your default browser.
[http://ubuntuforums.org/showthread.php?t=166993&highlight=howto+install+swiftfox](http://ubuntuforums.org/showthread.php?t=166993&highlight=howto+install+swiftfox)

It's written for breezy, but I assume it is the same in dapper.

---

### Post by Stirling on 2006-06-03
[QUOTE=angkor]double-click the tar.bz2 to extract the contents. There's a swiftfox-bin in the newly created swiftfox dir. You can run it from the terminal:

```
cd swiftfox
./swiftfox-bin
```
[/QUOTE]
You should just do ./swiftfox not ./swiftfox-bin

---

### Post by RAV TUX on 2006-06-03
[quote=angkor]double-click the tar.bz2 to extract the contents. There's a swiftfox-bin in the newly created swiftfox dir. You can run it from the terminal:

```
cd swiftfox
./swiftfox-bin
``` 
Also read this thread if you like it and want to make it your default browser.
[http://ubuntuforums.org/showthread.php?t=166993&highlight=howto+install+swiftfox]("http://ubuntuforums.org/showthread.php?t=166993&highlight=howto+install+swiftfox")

It's written for breezy, but I assume it is the same in dapper.[/quote] 
I tried this and this is what I got:

[[IMG]http://img98.imageshack.us/img98/8427/screenshot10zy.th.png[/IMG]]("http://img98.imageshack.us/my.php?image=screenshot10zy.png")

this gave me similar results:

cd swiftfox
./swiftfox


Is there something I did wrong?

---

### Post by aysiu on 2006-06-03
[QUOTE=yozef]I tried this and this is what I got:[/QUOTE] That's because Swiftfox is on your desktop, not in your /home folder. ```
cd ~/Desktop
ls
cd swiftfox
ls
./swiftfox
```

---

### Post by RAV TUX on 2006-06-03
[quote=aysiu]That's because Swiftfox is on your desktop, not in your /home folder. ```
cd ~/Desktop
ls
cd swiftfox
ls
./swiftfox
```[/quote]

Thanks aysiu! it did something:

[[IMG]http://img234.imageshack.us/img234/8544/screenshot6ms.th.png[/IMG]](http://img234.imageshack.us/my.php?image=screenshot6ms.png)

but what do I do afterwards, I tried:

jozef@ubuntujozef:~/Desktop/swiftfox$ ./swiftfox
jozef@ubuntujozef:~/Desktop/swiftfox$
jozef@ubuntujozef:~/Desktop/swiftfox$ cd swiftfox
bash: cd: swiftfox: Not a directory
jozef@ubuntujozef:~/Desktop/swiftfox$ ./swiftfox

Thank you for your help.

---

### Post by RAV TUX on 2006-06-03
[quote=aysiu]That's because Swiftfox is on your desktop, not in your /home folder. ```
cd ~/Desktop
ls
cd swiftfox
ls
./swiftfox
```[/quote]

I tried again and this is how far I have got:

[[IMG]http://img234.imageshack.us/img234/9458/screenshot8or.th.png[/IMG]](http://img234.imageshack.us/my.php?image=screenshot8or.png)

---

### Post by aysiu on 2006-06-03
I believe Swiftfox is just Firefox with some tweaks, so you may not be able to run Swiftfox is Firefox is already open. Try closing Firefox and then running the ```
./swiftfox
``` command.

---

### Post by RAV TUX on 2006-06-04
[quote=aysiu]I believe Swiftfox is just Firefox with some tweaks, so you may not be able to run Swiftfox is Firefox is already open. Try closing Firefox and then running the ```
./swiftfox
``` command.[/quote]

Thanks I'll give it a try.

---

