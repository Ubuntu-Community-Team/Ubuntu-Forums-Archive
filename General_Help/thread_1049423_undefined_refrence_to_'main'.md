---
title: "undefined refrence to 'main'"
date: 2009-01-24
forum: General Help
---

### Post by mschick on 2009-01-24
Hello all,

I am new to using GNUstep to compile Obective-C programs.  I ran threw the documentation from gnustep.org on how to compile Objective-C programs....i create a prog1.m file, a GNUmakefile, and setup my gnustep env but when i run the make file i get the following error:

Making all for tool prog1...
 Linking tool prog1 ...
/usr/lib/gcc/i486-linux-gnu/4.2.1/../../../../lib/crt1.o: In function `_start':
(.text+0x18): undefined reference to `main'
collect2: ld returned 1 exit status
make[1]: *** [shared_obj/prog1] Error 1
make: *** [prog1.all.tool.variables] Error 2

Here is my code:

//First Objective-C Program

#import <Foundation/Foundation.h>

int main(int argc, const char * argv[])
{
        NSAutoreleasePool * pool = [[NSAutoreleasePool alloc] init];
        NSLog (@"Programming is fun!!!!");

        [pool drain];
        return(0);
}


Ive been searching on google for a while now and figured I turn to the forums for an answer.... what am i doing wrong?

Thanks in advance!

---

### Post by mschick on 2009-01-24
Is there anyone that can help me on this issue?  I still can't get It to work...

---

### Post by snova on 2009-01-24
First, you should use [noparse][CODE][/noparse] tags around the error message, it makes it easier to read.

Also, the error message means that the source file containing main() isn't being linked. What's the Makefile look like?

---

### Post by mschick on 2009-01-24
That was it...I had made an error in my GNUmakefile...once i fixed it I wasnt getting the "undefined reference to 'main'" error.  Now when I run the make file i get the following:

```
Making all for tool prog1...
 Compiling file prog1.m ...
 Linking tool prog1 ...
./shared_obj/prog1.o: In function `main':
/home/mschick/Progs/prog1.m:6: undefined reference to `NSLog'
./shared_obj/prog1.o:(.data.rel+0x0): undefined reference to `__objc_class_name_NSAutoreleasePool'
collect2: ld returned 1 exit status
make[1]: *** [shared_obj/prog1] Error 1
make: *** [prog1.all.tool.variables] Error 2
```


My makefile looks like this:

```
include $(GNUSTEP_MAKEFILES)/common.make

TOOL_NAME = prog1 
prog1_OBJC_FILES = prog1.m

include $(GNUSTEP_MAKEFILES)/tool.make

```

Im not sure exactly what other libs i need?

---

### Post by vandorjw on 2009-01-24
your problem lies here

> 
/home/mschick/Progs/prog1.m:6: undefined reference to `NSLog'


I have never programed in objective-C before, so I don't really know what the problem is.

I'll try and re-create your error, and then see how to fix it.

cheers - cc7gir

ps: Is this your first time programing?
edit: On second thought, never-mind. I don't think Objective-C and I are going to get along with each other very well.

This is what it spit out for me, (without a compiler, or any libraries)
```

...$ make
makefile:1: /common.make: No such file or directory
makefile:6: /tool.make: No such file or directory
make: *** No rule to make target `/tool.make'.  Stop.

```

---

### Post by mschick on 2009-01-24
Thanks anyways and no this is not my first time programming but it is my first time programming in Objective-C and it is not going so well lol.....anyone else got any ideas?

---

### Post by mschick on 2009-01-25
Still having issues with this....can anyone help?

Thanks!

---

### Post by mschick on 2009-01-25
Still need help with this...anyone?

---

### Post by Gauthic on 2009-06-11
I can verify this 'bug' as well.

**cc7gir**: You don't have your GNUSTEP_MAKEFILES environment variable set.
In 9.04 I have it set to /usr/share/GNUstep/Makefiles

Cheers and good luck.

---

### Post by Gauthic on 2009-06-11
It appears that the OpenStep libraries doesn't include the NSLog class that Apple, Inc. has with XCode (where NSLog is a very common Hello World type of introduction). 

I did a quick search through the /usr/share/GNUstep directory and there were many references to standard NextStep classes, but not one to NSLog.

I'd try another example using NSString or whatnot (or get a Mac and install XCode if you want guaranteed tutorial code compatibility )

---

### Post by Gauthic on 2009-06-11
Sorry about the mutliple replies....I'm kinda a stickler of not having an open-ended questions without some sort of resolution.

I did find a reference for NSLog in /usr/include/GNUstep/Foundation/NSDebug.h

And I found some information of how to compile directly with gcc instead of using the GNUmakefile examples above

** From [http://blog.lyxite.com/2008/01/compile-objective-c-programs-using-gcc.html](http://blog.lyxite.com/2008/01/compile-objective-c-programs-using-gcc.html)**

Assuming your file is named main.m
```

[FONT=courier new]$ gcc -o main main.m -I /usr/include/GNUstep/ -L /usr/lib/GNUstep/ \
-lgnustep-base -fconstant-string-class=NSConstantString

$ ./main[/FONT]

```It would sound as if the objc.make or the common.make in $(GNUSTEP_MAKEFILES) isn't quite referencing everything needed.

---

### Post by DaCrayZeeOne on 2010-03-04
In case anyone is still struggling with this you need to run this command before running make:

```

export GNUSTEP_MAKEFILES="/usr/share/GNUstep/Makefiles/"

```

Personally, I added this line to my ~/.profile file so it would be run automatically.

---

