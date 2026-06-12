---
title: "How do I install GCC?"
date: 2006-06-29
forum: Desktop Environments
---

### Post by Lster on 2006-06-29
Had a few minor problems with 6.06 but all fine now, except I need a C++ compiler! I can't find GCC in Synaptic. What can I do?

Thanks all

---

### Post by 23meg on 2006-06-29
Install the package build-essential.

---

### Post by th3james on 2006-06-29
GCC should be in synaptic, have you enabled all the extra respositries?

you'll find that under settings in synaptic

---

### Post by Lster on 2006-06-29
Thanks all - that's got me further. Now, though, it says something about not find librarie's! I have installed linux-headers and build-essential but it still cannot manage.

---

### Post by niels_r on 2006-06-29
Isn't gcc already on your system? Just open a terminal and type 'gcc -dumpversion'. Does this give any output? In my case it gives 4.0.3.

If it's not on your system: Just open Synaptic and click 'Advanced'. Search for 'gcc' and it should appear in the list. I don't think extra repositories are needed.

---

### Post by 23meg on 2006-06-29
[QUOTE=Lster]Thanks all - that's got me further. Now, though, it says something about not find librarie's! I have installed linux-headers and build-essential but it still cannot manage.[/QUOTE]
You need to have the build dependencies of whatever you're trying to compile installed. Noone can help you without knowing what you're trying to compile and the errors you're getting.

---

### Post by Lster on 2006-06-29
I can get gcc up, but can't compile:

#include <stdio.h>

int main(){
	printf("Hello world!");

	return 0;
}

I get the following error:

/tmp/ccZJFc0c.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

I don't know what to install or how...:confused:

---

### Post by Lster on 2006-06-29
Sry, computer turned part of the error message to a smiley face!

/tmp/ccZJFc0c.o: (.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status

---

