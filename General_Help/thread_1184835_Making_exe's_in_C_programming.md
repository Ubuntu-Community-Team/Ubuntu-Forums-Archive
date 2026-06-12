---
title: "Making exe's in C programming"
date: 2009-06-11
forum: General Help
---

### Post by rymonroe on 2009-06-11
I just got my new dell with ubuntu and downloaded a complier for c programming. I made a simple hello world program and made an exe. When I execute the file inside the termnal it works just fine, displaying "hello world" inside the termnal. When I close the termnal and click on the icon that was created inside my home directory nothing happens. Is this normal. Is there anyway I can make the program work outside the termnal. Thanks in advance for your help.

---

### Post by cb951303 on 2009-06-11
> **rymonroe said:**
> I just got my new dell with ubuntu and downloaded a complier for c programming. I made a simple hello world program and made an exe. When I execute the file inside the termnal it works just fine, displaying "hello world" inside the termnal. When I close the termnal and click on the icon that was created inside my home directory nothing happens. Is this normal. Is there anyway I can make the program work outside the termnal. Thanks in advance for your help.

you need to learn a GUI library such as GTK or QT if you want to write graphical (non-terminal) applications

---

### Post by Wayne_V on 2009-06-11
I would recommend checking out NetBeans or Eclipse.  Both are available in the standard repositories.

---

### Post by DGortze380 on 2009-06-11
> **rymonroe said:**
> I just got my new dell with ubuntu and downloaded a complier for c programming. I made a simple hello world program and made an exe. When I execute the file inside the termnal it works just fine, displaying "hello world" inside the termnal. When I close the termnal and click on the icon that was created inside my home directory nothing happens. Is this normal. Is there anyway I can make the program work outside the termnal. Thanks in advance for your help.

While writing your program, you likely used the iostream library and the cout command (or printf), both of which print to the standard out (ie. terminal screen).

You need to program a graphical interface if you want a graphical interface to start with the program. I suggest learning the basics first, when you're ready to move to Visual C, I recommend looking into QT.

---

### Post by ActiveFrost on 2009-06-11
Depends on what's your aim - you can't use QT on commercial projects ( that's why I'm learning GTK+ ).

---

### Post by DGortze380 on 2009-06-11
> **ActiveFrost said:**
> Depends on what's your aim - you can't use QT on commercial projects ( that's why I'm learning GTK+ ).

You can, you just have to pay for it. ;)

---

### Post by cmay on 2009-06-11
> **rymonroe said:**
> I just got my new dell with ubuntu and downloaded a complier for c programming. I made a simple hello world program and made an exe. When I execute the file inside the termnal it works just fine, displaying "hello world" inside the termnal. When I close the termnal and click on the icon that was created inside my home directory nothing happens. Is this normal. Is there anyway I can make the program work outside the termnal. Thanks in advance for your help.

you dont make exe in linux. there is no need for extentions in linux. in windows there is but not in nix systems. its more important if the file has the right permissions than the .extention 

as example a shell script can be called script.sh or script and it does not matter in terms of the abiility to be executed. 

when using c you still however should name the sources with the extention .c and .h .
when using perl or python it matters less.

---

### Post by ActiveFrost on 2009-06-11
> **DGortze380 said:**
> You can, you just have to pay for it. ;)

Yeah, but .. $10,000 :o

---

### Post by cb951303 on 2009-06-11
> **ActiveFrost said:**
> Yeah, but .. $10,000 :o

what? isn't QT is LGPL now? it means you can use it commercially as a dynamic library.

---

### Post by ActiveFrost on 2009-06-11
> **cb951303 said:**
> what? isn't QT is LGPL now? it means you can use it commercially as a dynamic library.

QT Licensing ( [http://www.qtsoftware.com/products/licensing](http://www.qtsoftware.com/products/licensing) ) :
> You must purchase a Qt Commercial License from Qt Software or from one of its authorized resellers before you start developing commercial software.
> The Qt Commercial License is the correct license to use for the development of proprietary and/or commercial software with Qt where you do not want to share any source code.

---

### Post by Chronon on 2009-06-11
You must use that license only if you are unwilling to comply with LGPL v2.1.

Otherwise you can choose this:
> Qt GNU LGPL v. 2.1 Version
This version is available for development of proprietary and commercial applications in accordance with the terms and conditions of the GNU Lesser General Public License version 2.1. 

Support services are available separately for purchase.

Benefit to Qt
The benefit to Qt is that any changes made to Qt must be made available under the terms of this license.

---

### Post by Mirge on 2009-06-11
Couple questions, not hi-jacking the thread.. :)

Why Qt over GTKmm (C++ will be used)?
Are Qt applications built on Kubuntu 9.04 portable to Windows XP/Vista?
If so, is it a painfully tedious process or not quite that bad?
Finally, I've been playing with Qt Creator... is this the IDE I should use? Any recommended tutorials or better, books??

Thanks :)

---

### Post by kuja on 2009-06-11
> **Mirge said:**
> Couple questions, not hi-jacking the thread.. :)

Why Qt over GTKmm (C++ will be used)?
Are Qt applications built on Kubuntu 9.04 portable to Windows XP/Vista?
If so, is it a painfully tedious process or not quite that bad?
Finally, I've been playing with Qt Creator... is this the IDE I should use? Any recommended tutorials or better, books??

Thanks :)
Yes, for example, look at KDE. :popcorn:

---

### Post by Mirge on 2009-06-11
> **kuja said:**
> Yes, for example, look at KDE. :popcorn:
I don't get it? Which one were you answering? lol

---

### Post by kuja on 2009-06-11
> **Mirge said:**
> I don't get it? Which one were you answering? lol

> Are Qt applications built on Kubuntu 9.04 portable to Windows XP/Vista? This one.

---

### Post by Sinkingships7 on 2009-06-11
To run the program "without" the terminal, add the following line to your program right before your return statement:
```

std::cin.get();

```
Now when you double click on the exe, the terminal will stay open.

I'm guessing this is what you meant. I'm also assuming Windows, since you said exe. You probably mean a Linux binary, in which case you're still going to need the code I gave you.

---

### Post by noerrorsfound on 2009-06-11
> **cmay said:**
> you dont make exe in linux. there is no need for extentions in linux. in windows there is but not in nix systems. its more important if the file has the right permissions than the .extention
I believe in this case it's just being used as a shortened form of the word "executable" which can refer to a compiled program on any system (AKA *binary*).

---

### Post by DGortze380 on 2009-06-11
> **Mirge said:**
> Couple questions, not hi-jacking the thread.. :)

Why Qt over GTKmm (C++ will be used)?
Are Qt applications built on Kubuntu 9.04 portable to Windows XP/Vista?
If so, is it a painfully tedious process or not quite that bad?
Finally, I've been playing with Qt Creator... is this the IDE I should use? Any recommended tutorials or better, books??

Thanks :)

QT because it's easily portable.
Nothing wrong with GTK, I just prefer QT.

---

### Post by Mirge on 2009-06-11
I'm actually quite surprised that so far people have suggested Qt... but I'm sure as soon as I say "OK, I've decided to use Qt", more will respond with "ahhh you should use GTK!!" (or FLTK, wxWidgets, insert your other favorite here)... hehe.

---

### Post by kuja on 2009-06-11
> **Mirge said:**
> Finally, I've been playing with Qt Creator... is this the IDE I should use? Any recommended tutorials or better, books??

Thanks :)

QtDesigner is nice too, give it a try. Same goes for KDevelop.

---

### Post by Mirge on 2009-06-11
OMG firefox is going to drive me absolutely nuts if it doesn't stop with the "Looking up <domain>..." hang-ups...

I'll check out QtDesigner, hadn't actually heard or seen that before. Looking now, if Firefox lets me.

---

### Post by cb951303 on 2009-06-12
> **ActiveFrost said:**
> QT Licensing ( [http://www.qtsoftware.com/products/licensing](http://www.qtsoftware.com/products/licensing) ) :

if you won't modify QT source and link it statically you are free to use QT commercially without giving away your source. That's what LGPL is and it covers 99% of the commercial developers because no one cares about statically linking (it's too big for QT) and modifying it is unnecessary for most people. 

In fact I think you can just release the modified QT part's source only and get away without releasing the source of your whole program if you really really need to modify QT.

---

