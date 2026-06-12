---
title: "turbo C++ replacement??"
date: 2008-10-25
forum: Education &amp; Science
---

### Post by krusher on 2008-10-25
Hi
I am a computer science student who wish to shift to ubuntu. But I am not sur if i be able to try my C++ programs in ubuntu. I did search around the forum for a c++ compiler and found about gcc and that intel one.
But i didnt get much out of what is written about em.

I just want to know whether there are programs that will work exactly the way my currenr turbo c++ in which i write a program and then it compiles it???

---

### Post by kdcoetzee on 2008-10-25
Well. I am using g++ and vim.

but give [[COLOR="Red"]these[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1577") a try.

I have never tried turbo C++. so I don't know which one is like that one.

---

### Post by krusher on 2008-10-25
what i am looking for is a simple piece of software that will compile my high school programs. M not into editing linux or anything.

So maybe now you can suggest me something???

I mean, since c++ is a common language and all compilers should run the programs in the same way giving same outputs??

---

### Post by kdcoetzee on 2008-10-25
Well I did.

that link shows all the IDE's I know of. and that I think you are looking for.

[http://ubuntuforums.org/showthread.php?t=1577]("http://ubuntuforums.org/showthread.php?t=1577")

and of those that I used I liked. 
[http://anjuta.sourceforge.net/]("http://anjuta.sourceforge.net/")

and yes your C++ program should work fine on Linux if you didn't use any windows specified libraries.

---

### Post by kdcoetzee on 2008-10-25
And just for the record. vim and g++ are simple. it just looks intimidating.

write your code in vim or your favourite text editor.And save as filename.ccp
Or use your programs that you already wrote.

then ```
 g++ filename.ccp -0 output_filename 
```

then in the terminal just run it with.

```
 ./output_filename 
```

Hope any of this helped.

---

### Post by krusher on 2008-10-26
hi
I did install G++ but don't see it in the apllication list. Hence I made that other post. 
Ok so I write the program in text editor then type those 2 things in terminal. Don't we have 1 single piece of software in which I can type the program n there itself run it?? I heard there r program that let us run windows prpgrams!! Can I use one of them to run my turbo c++

---

### Post by pwillard on 2008-11-06
If you NEED turbo C++ code to run, you could install WINE then TurboC++ and try your luck. (It should work)

Another convoluted path would be to try CodeBlocks

[http://prdownload.berlios.de/codeblocks/codeblocks_8.02-0ubuntu1.deb.tar.gz](http://prdownload.berlios.de/codeblocks/codeblocks_8.02-0ubuntu1.deb.tar.gz)

And then follow that up with DEVPAK installer so you can use plugins created for DEV-C++ (windows) that were created to provide TurboC++ compatability/migration.

With CodeBlocks installed you may be able to just convert your code directly if it's not very complex.

---

### Post by meson2439 on 2008-11-15
You won't find gcc/g++ in the applications list. To use g++ after a proper installation you need to open the Terminal which you can find under accessories. Here is a list of stuff to do next:

1)change to the directory you want using the terminal of course. You can do this by typing 'cd ~/Documents/' if you want access the Documents folder. For furter information type 'man cd'. 

2)edit or create a file by typing 'gedit myfiles.cpp'. myfiles.cpp can of course be replaced by any filename you have in mind.

3)After finish, save the file and quit. ctrl+Q also does the same thing. 

4)to compile type 'g++ -Wall -o myexecutables myfiles.c'. myexecutables can be replaced by any name you want including myfiles itself excluding the extension. 

5)To execute type './myexecutables'

6)Do not ask about exe files. We don't have them. You can identify the executables, by typing 'ls'. The green colored files are the executables. Another way to identify is that the executables have no extensions to them.

7)For more information read [http://www.icce.rug.nl/documents/cplusplus/]("http://www.icce.rug.nl/documents/cplusplus/") and read about how to use the terminal in the beginners forums.

---

### Post by akniss on 2008-11-15
You might also check out emacs.  Once you open a .cpp file, it will bring up a C++ menu on the tool bar for some editing options, and there is the ability to compile under the Tools menu.  I think its easier to learn than vim... but each individual has his or her preferences.
[http://www.cs.bu.edu/teaching/tool/emacs/programming/](http://www.cs.bu.edu/teaching/tool/emacs/programming/)

---

