---
title: "Native game development"
date: 2018-12-09
forum: Gaming &amp; Leisure
---

### Post by tiakuh on 2018-12-09
Hello all,

I want to thank you for the time you are giving to me, reading and commenting this thread. I googled this before coming here, but I still think the infomation is very confusing.
It's my first post in this forum.

My question is, what makes a 'native' linux gaming really considered native?
My last question would be, if I use unreal engine with blueprint and c++, would it be considered a native linux game?

I'm trying to develop my first game, and I want to focus on native linux gaming experience.

I'm pretty newbie into linux dev scene, but I'm working as a developer professionaly for one year now. Besides that I'm in my first year of university and learning C and C++;
Since I don't work with this languages daily, but I have a love for linux, I would like to start my own exploring project.

Thank you! ;)

---

### Post by TheFu on 2018-12-09
Welcome to the forums.

Google found this definition: 
> An executable program coded in the machine language of the hardware platform it is running in. A native application has been compiled into the machine language of that CPU.

Everyone probably has slightly different answers for "what is native code" in practice.

To me, it means there isn't any translation layer converting whatever language the programmer used, compiled, linked, and what the OS can run without any added tools like WINE or Mono or JRE or whatever that "Electron" solution is.  Fo me, I add in that any required libraries shouldn't be bloated.  My definitions is probably the strictest.

Others would say if you don't need either an emulator (QEMU) or translation layer like WINE, then it is native.  If the same program will run, unchanged, as linked, on any other platform, it isn't native.  For example, if a program works on Linux on both AMD64 and on ARM without recompiling and relinking, then it isn't native. Same OS, different CPUs.

C/C++ fit all definitions of "native code".  I'd guess that Rust would too.  C# doesn't fit for me, because it requires Mono which I won't have on my system, but it does meet the 2nd, relaxed definition. I won't use any non-server applications with Java. Java desktop applications are hogs. Just look at Eclipse or Netbeans use of resources.

An argument that Ruby, Python, Perl are "native" could be made for a non-heavy graphics game. None of them come close to compiled C/C++ in the hands of an expert when it comes to performance and they run unchanged on x64 and ARM Linux systems.

C/C++ will let you shoot yourself in the hand, foot, head and heart if you don't have a good grasp AND techniques to manage pointers.  Wild pointers in any running programs are bad, but in the hands of an expert, they can make extremely fast and efficient code.

If you are doing C/C++, hopefully you've learned that the desktop is you IDE, not some huge tool.  When I'm coding C++, I have 3 terminals open and a browser, but I haven't coded anything non-trivial in years.  

* editor <--- vim (check out videos by expert vim users)
* gmake (I think newer people/projects are using cmake)
* debugger 
* browser is for documentation

My mouse sets the window underneath active without any click and does not pull active windows to the top. Learned this at a lab of hardcore C programmers a few decades ago.

Others will have their definitions.  I bet a book someone has one too. ;)

---

