---
title: "Some Java Crap"
date: 2005-12-08
forum: General Help
---

### Post by SomethingTohide on 2005-12-08
So I have a java bot for a game, and it works fine in windows, and they have a linux version. So I get it on here, and then I downloaded and installed JDK and JRE the newest ones, and I compiled all of it. It compiles correctly, but when I run it I get this error.


Exception in thread "main" java.lang.ClassNotFoundException: java.lang.StringBuilder not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./,file:./,file:./OUTPUT/,file:./OUTPUT/unrenamed.jar,file:./,file:./BotClasses/], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at Bot.log(java.lang.String) (Unknown Source)
   at Bot.Bot() (Unknown Source)
   at Bot.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)

---

### Post by RAOF on 2005-12-08
Your Sun JDK/JRE isn't set-up correctly - the program is trying to use the free, gnu java runtime which, as you have found, is missing important things :)

To fix this, I'd suggest running ```
sudo update-alternatives --config java
``` and selecting the java runtime by with "sun" in the name.

---

### Post by kb3hkg on 2005-12-09
search online and you can find the Sun jdk debian package for ubuntu instead of gnu, this has worked much better for me, but I don't remember where I found the package.

---

### Post by SomethingTohide on 2005-12-09
[QUOTE=RAOF]Your Sun JDK/JRE isn't set-up correctly - the program is trying to use the free, gnu java runtime which, as you have found, is missing important things :)

To fix this, I'd suggest running ```
sudo update-alternatives --config java
``` and selecting the java runtime by with "sun" in the name.[/QUOTE]



I can use this to run the bot, but when I compile I get massive errors.

---

### Post by aclaunch on 2005-12-09
There is a section in the Ubuntu guide that covers Java (specifically Sun Java):
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-java](http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-java). I don't know about your bot but Java works fine on my machine with this.

Good Luck,
Alan

---

### Post by SomethingTohide on 2005-12-09
Ok I'll just have to switch back and forth I guess. When I ran this on windows I'd have 7-8 of them going, but now I can only run 3 or it lags on Ubuntu :(

---

