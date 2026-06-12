---
title: "C++ in linux"
date: 2005-12-13
forum: General Help
---

### Post by HokeyFry on 2005-12-13
ARRGGG!!!

I can't find any good sites on how to program in C++ in linux. Correct me if i am wrong, but my teacher told us that C++ is different on other platforms than on windows. So if thats true, than i cant apply the same headers that i normally do!! Can someone please tell me where I can find a web site that will teach me how to program in c++ on linux?

**NOTE** I do not want to have to spend any money, so a book is out of the question.

---

### Post by psusi on 2005-12-13
C++ is a standard.  That means it is the same everywhere.  Each platform has many non standard libraries availible to you, but as long as you stick to standard C++, it will go anywhere.

---

### Post by taurus on 2005-12-13
If you are taking a class in C++ ("...my teacher told us..."), then shouldn't you also need a programming book in C++!

---

### Post by cstudent on 2005-12-13
The teacher maybe meant that MS Visual C++ is not 100% Ansi/ISO standard C++. But if you know MS Visual C++, you'll be able to program C++ in Linux without much change. If you are looking for an IDE to use in Linux I would suggest Eclipse and the CDT plugin. Eclipse is available through the repositories, but I prefer to download it from [www.eclipse.org](www.eclipse.org) and untar the software to my /opt directory.

---

### Post by HokeyFry on 2005-12-14
i took the class last year. i am in another class now, but it is for java. also, i am in high school, so i dont get to keep the books. after reading your responses I think what he might have meant was that the things we were learning are not compatible to work on linux (i.e. the AP headers). I think I will try to download eclipse and use the c++ plugin you can install.

Thanks for the responses.

---

### Post by void_false on 2005-12-14
> C++ is a standard. That means it is the same everywhere.

Is it standard?

```
#include<iostream.h>
int main()
{cout << "Hello world";}
```

---

### Post by psusi on 2005-12-14
Oh Jesus Christ good god!  They are still teaching with the AP headers?

If I ever meet the people who made those I will bash their skull in.  You should kick your teacher in the balls and tell him to quit using that garbage and teach the real language.  

If you really want to you should be able to use the ap headers on linux, but I couldn't tell you exactly how to install them off the top of my head, but you would really be much better off using the official standard libraries instead of the ap junk.  

And yes, C++ is an ISO standard that was formalized in 1996.  And iostream.h is not a standard header, the standard headers have no .h ending.

---

### Post by cstudent on 2005-12-14
[QUOTE=HokeyFry]i took the class last year. i am in another class now, but it is for java. also, i am in high school, so i dont get to keep the books. after reading your responses I think what he might have meant was that the things we were learning are not compatible to work on linux (i.e. the AP headers). I think I will try to download eclipse and use the c++ plugin you can install.

Thanks for the responses.[/QUOTE]


You can also use Eclipse to program Java too. :)

---

### Post by Dr. Nick on 2005-12-14
Yeah I took it in HS using the AP Headers also. They combined alot of libraries. iostream.h is a combonation of istream and ostream I think. I need to get back into c++ using the standards. Is the cout << standard or is that more AP filth?

---

### Post by void_false on 2005-12-14
[QUOTE=psusi]Oh Jesus Christ good god!  They are still teaching with the AP headers?

If I ever meet the people who made those I will bash their skull in.  You should kick your teacher in the balls and tell him to quit using that garbage and teach the real language.  

If you really want to you should be able to use the ap headers on linux, but I couldn't tell you exactly how to install them off the top of my head, but you would really be much better off using the official standard libraries instead of the ap junk.  

And yes, C++ is an ISO standard that was formalized in 1996.  And iostream.h is not a standard header, the standard headers have no .h ending.[/QUOTE]

Yeah I know. But for some strange reason every book that i've seen uses this approach. :???:

---

### Post by psusi on 2005-12-14
> **Dr. Nick]Yeah I took it in HS using the AP Headers also. They combined alot of libraries. iostream.h is a combonation of istream and ostream I think. I need to get back into c++ using the standards. Is the cout << standard or is that more AP filth?[/QUOTE]

iostream.h is not AP, it is the pre standard version of <iostream>.  Before C++ was officially standardized C++ compilers typically had an iostream.h header.  The standard made a few changes from the commonly used non standard iostream.h, including wrapping everything in the std:: namespace.  The .h ending was removed when the standard was ratified, but many compilers retain the old .h headers for backward compatibility with pre standard code.  

Yes, cout is in the standard, but it's in the std:: namespace so you either have to reference it as std::cout, or throw in a using namespace std said:**
> Yeah I know. But for some strange reason every book that i've seen uses this approach. :???:

You must be reading some very old/bad books ;)

Check out #C++ on the Effnet IRC network.. they can point you to some good books.

---

### Post by RAOF on 2005-12-14
A correct hello world looks something more like this:
```
#include <iostream>

int main(int argc, char **argv) {
 std::cout<<"Hello world\n";
 return 0;
}

```
"Standard" is such a rubbery term, isn't it ;)

---

### Post by Kevinator on 2005-12-14
ROAF's example would also be correct without the arguments to main() and/or without the 'return 0;'. That's about all you can eliminate and still have a well-defined standard C++ program.

---

### Post by RAOF on 2005-12-14
Well, you can yeah.  But it's poor form to not return something from a function declared as returning "int".  And main is defined as returning int :)

Remember: portable code relies upon you not assuming the compiler won't interpret your code in the most retarded way possible.  Because someone's compiler will ;)

---

### Post by Kevinator on 2005-12-14
Reaching the end of the main() function without returning anything is equivalent to returning 0. This is a special case that only applies to main(). See 3.6.1/5.

Stylistically it's probably not desirable, since it isn't particularly clear what is happening, but it does have a specific, well-defined and valid meaning.

---

### Post by RAOF on 2005-12-14
Well, you live and learn.  I knew it was valid in all the compilers I've seen, but not that the standard mandates it.

---

### Post by Dr. Nick on 2005-12-14
[quote=psusi]iostream.h is not AP, it is the pre standard version of <iostream>.  Before C++ was officially standardized C++ compilers typically had an iostream.h header.  The standard made a few changes from the commonly used non standard iostream.h, including wrapping everything in the std:: namespace.  The .h ending was removed when the standard was ratified, but many compilers retain the old .h headers for backward compatibility with pre standard code.  
[/quote]

Thanks for clearing that up, I had seen some places declare both a istream and ostream so I made the assumption iostream was just the AP combination since I learned on AP headers some years ago.

About the hello World code isnt void_main() just as good as return 0?

This thread has got me ready to jump back into programming once I finish off my Final Exams, I am quite a bit rusty :)

---

### Post by psusi on 2005-12-14
Both the C and C++ standards define main to return an int, so void main() is not valid.  

[QUOTE=Dr. Nick]Thanks for clearing that up, I had seen some places declare both a istream and ostream so I made the assumption iostream was just the AP combination since I learned on AP headers some years ago.

About the hello World code isnt void_main() just as good as return 0?

This thread has got me ready to jump back into programming once I finish off my Final Exams, I am quite a bit rusty :)[/QUOTE]

---

### Post by Gianni Exile on 2005-12-15
[QUOTE=psusi]iostream.h is not AP, it is the pre standard version of <iostream>.  Before C++ was officially standardized C++ compilers typically had an iostream.h header. [/QUOTE]

What are AP headers?  

I've used C++ for 15 years, started on Borland's compiler, and since on many many other platforms, for many companies.  Never heard of "AP headers".

Can't recall what book I learned from, some lousy pulp book and columns in DDJ.  

I use the online books by Bruce Eckel for reference.

---

### Post by Gianni Exile on 2005-12-15
What kind of sick abomination of a C compiler doesn't accept "void main()"? Insanity. That's just political correctness gone wild. C++ okay, perhaps in some weird case, but C? What kind of linkage would it provide??

---

### Post by psusi on 2005-12-15
[QUOTE=Gianni Exile]What are AP headers?  

I've used C++ for 15 years, started on Borland's compiler, and since on many many other platforms, for many companies.  Never heard of "AP headers".

Can't recall what book I learned from, some lousy pulp book and columns in DDJ.  

I use the online books by Bruce Eckel for reference.[/QUOTE]

The AP board, who designs advanced placement classes and tests for highschool students, created their own sort of standard library to teach students C++ with, in place of the standard C++ libraries.  They are basically a sick, twisted, neutered clone of the STL.  

For instance, instead of using the std::string template, they have their own apstring class.  

By the way... Borland's compiler eh?  The one that had the silly installer that looked like the dashboard of a race car?  Heh... I uninstalled that one right away, after seeing that silly installer, then noticing that the IDE was a 16 bit app when it was supposedly a 32 bit compiler.  

[QUOTE=Gianni Exile]What kind of sick abomination of a C compiler doesn't accept "void main()"? Insanity. That's just political correctness gone wild. C++ okay, perhaps in some weird case, but C? What kind of linkage would it provide??[/QUOTE]

Any compiler that complies with the standard.  The standard mandates that the default entrypoint of a program be named main, and that it return an int, and take an int and two arrays of strings ( char arrays ) as parameters. 

Most compilers ignore that requirement and allow you to define main however you like, but when you don't return a proper value from main, some value is still returned, only it will be garbage ( on most intel platforms, it will just be whatever random value happened to be sitting in EAX at the point of return ).

It is good practice to return 0 when there is no error in your program so the calling program knows you did what you were supposed to.

---

### Post by Gianni Exile on 2005-12-16
[QUOTE=psusi]The AP board, who designs advanced placement classes and tests for highschool students, created their own sort of standard library to teach students C++ with, in place of the standard C++ libraries.  They are basically a sick, twisted, neutered clone of the STL.   For instance, instead of using the std::string template, they have their own apstring class.  
[/quote]
Thanks, explains a lot.  I'm a hs dropout... although I went to uni instead.

> By the way... Borland's compiler eh?  The one that had the silly installer that looked like the dashboard of a race car?  Heh... I uninstalled that one right away, after seeing that silly installer, then noticing that the IDE was a 16 bit app when it was supposedly a 32 bit compiler.
That was a looong time back, the installer was textmode...  I do remember my enthusiasm of picking tobacco all summer in Ontario so I could buy the Borland C++ 3.0 compiler.  Shortly thereafter, I discover Watcom, and used I think it was called "Tran's pmode extender" so I could run simulations.  Then came Gnu C++, and from there it's a bit of a blur.

> Any compiler that complies with the standard.  The standard mandates that the default entrypoint of a program be named main, and that it return an int, and take an int and two arrays of strings ( char arrays ) as parameters. 

Most compilers ignore that requirement and allow you to define main however you like, but when you don't return a proper value from main, some value is still returned, only it will be garbage ( on most intel platforms, it will just be whatever random value happened to be sitting in EAX at the point of return ).  It is good practice to return 0 when there is no error in your program so the calling program knows you did what you were supposed to.

Yup, always return 0, sure.  Point is, if the runtime libs call main(), and the compiled function with that name isn't resolved, you've got some serious problem with your C compiler.

Thanks again!
-GE.

---

### Post by RAOF on 2005-12-16
[QUOTE=Gianni Exile]...
Yup, always return 0, sure.  Point is, if the runtime libs call main(), and the compiled function with that name isn't resolved, you've got some serious problem with your C compiler.

Thanks again!
-GE.[/QUOTE]
Yeah, but the compiler is well within its rights to fail to compile your standard-breaking code :)

---

### Post by Gianni Exile on 2005-12-18
[QUOTE=RAOF]Yeah, but the compiler is well within its rights to fail to compile your standard-breaking code :)[/QUOTE] More heresy! It's the linker's job to resolve public symbol bindings! 

If I want 'void main()', and the compiler refuses, I say it is a tyrannical dictator who has overstepped its authority. I'll never submit!! 

'And that compiler, of the people, by the people, for the people, shall not perish from the earth!!' 

Tell those bureaucrats at ANSI/ISO to put THAT in their pipes and smoke it! 

-GE. :p

---

