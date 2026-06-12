---
title: "Objective C linking problems using GNUStep"
date: 2009-02-01
forum: General Help
---

### Post by mschick on 2009-02-01
I am new to using GNUSTep and using Objective C.  I have done my research and setup the GNUStep environment to allow for Objective C compiling.  I have created the following code:

```
#import <Foundation/Foundation.h>

int main(int argc, const char * argv[])
{
        NSAutoreleasePool * pool = [[NSAutoreleasePool alloc] init];
        NSLog(@"Programming is fun!!!!");

        [pool release];
        return 0;
}

``` 

and have created the following GNUmakefile:

```
include $(GNUSTEP_MAKEFILES)/common.make

TOOL_NAME = prog1 
prog1_OBJC_FILES = prog1.m 

include $(GNUSTEP_MAKEFILES)/tool.make

``` 

Now when i run the following command:

```
make -messages=yes
```

The program compiles without error but i get a linking error:

```
Making all for tool prog1...
gcc prog1.m -c \
              -MMD -MP -DGNU_RUNTIME=1 -DGNUSTEP_BASE_LIBRARY=1 -D_REENTRANT -fPIC -DGSWARN -DGSDIAGNOSE -g -O2 -fno-strict-aliasing -fgnu-runtime -I. -I/home/mschick/GNUstep/Library/Headers -I/usr/local/lib/GNUstep/Local/Library/Headers -I/usr/local/lib/GNUstep/Network/Library/Headers -I/usr/lib/GNUstep/System/Library/Headers \
               -o shared_obj/prog1.o
gcc  -rdynamic       -fgnu-runtime -o shared_obj/prog1 \
                ./shared_obj/prog1.o \
                 -L/home/mschick/GNUstep/Library/Libraries -L/usr/local/lib/GNUstep/Local/Library/Libraries -L/usr/local/lib/GNUstep/Network/Library/Libraries -L/usr/lib/GNUstep/System/Library/Libraries -lpthread -lobjc -lm 
[COLOR="Red"]./shared_obj/prog1.o: In function `main':
/home/mschick/Progs/prog1.m:6: undefined reference to `NSLog'
./shared_obj/prog1.o:(.data.rel+0x0): undefined reference to `__objc_class_name_NSAutoreleasePool'
collect2: ld returned 1 exit status
make[1]: *** [shared_obj/prog1] Error 1
make: *** [prog1.all.tool.variables] Error 2[/COLOR]

```

What is going on here? I am stuck and need help.  What am i doing wrong?

Thanks

---

### Post by mschick on 2009-02-01
bump

---

