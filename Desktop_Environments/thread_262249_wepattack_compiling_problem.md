---
title: "wepattack compiling problem"
date: 2006-09-21
forum: Desktop Environments
---

### Post by ZipoTe on 2006-09-21
Hi!!
I have a problem with WEPATTACK. I was triying to compile it but then this error appears:

gcc  -o wepattack wepattack.o rc4.o wepfilter.o log.o\
        modes.o misc.o verify.o keygen.o -lpcap -lz -lcrypto
gcc: log.omodes.o: El fitxer o directori no existeix
make: *** [wepattack] Error 1

I don't know what to do and i have looked out for some information but i didn't found anything.

Can anyone help??

THANK YOU!!

---

### Post by rbalfour on 2006-09-21
log.omodes.o

This is 2 files.

open up the Makefile and look for the line.

gcc -o wepattack wepattack.o rc4.o wepfilter.o log.o\
modes.o misc.o verify.o keygen.o -lpcap -lz -lcrypto

and replace it with this one

gcc -o wepattack wepattack.o rc4.o wepfilter.o log.o \
modes.o misc.o verify.o keygen.o -lpcap -lz -lcrypto


Just did it and it worked.

---

### Post by ZipoTe on 2006-09-23
Ei!!

Thank you for your help!! :D it worked ;) 

Sayonara!!

---

### Post by cmavr8 on 2006-12-28
Here's my error while compiling (make command) WepAttack:

chris@chris-laptop:~/Desktop/wlan/WepAttack-0.1.3/src$ make
gcc -fno-for-scope -c -D__LINUX_WLAN__ -D__I386__ -o wepattack.o wepattack.c
cc1: warning: command line option "-fno-for-scope" is valid for C++/ObjC++ but not for C
wepattack.c:21:18: error: time.h: No such file or directory
wepattack.c:22:22: error: sys/time.h: No such file or directory
wepattack.c:23:23: error: sys/timeb.h: No such file or directory
wepattack.c:24:19: error: stdio.h: No such file or directory
wepattack.c:25:20: error: stdlib.h: No such file or directory
wepattack.c:26:19: error: fcntl.h: No such file or directory
wepattack.c:27:22: error: sys/stat.h: No such file or directory
wepattack.c:28:19: error: errno.h: No such file or directory
wepattack.c:29:20: error: unistd.h: No such file or directory
wepattack.c:30:18: error: zlib.h: No such file or directory
wepattack.c:31:18: error: math.h: No such file or directory
wepattack.c:32:20: error: signal.h: No such file or directory
In file included from wepattack.c:38:
misc.h:27: warning: &#8216;struct timeval&#8217; declared inside parameter list
misc.h:27: warning: its scope is only this definition or declaration, which is probably not what you want
misc.h:42: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
misc.h:47: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
wepattack.c:47: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
wepattack.c: In function &#8216;load_packets&#8217;:
wepattack.c:73: error: &#8216;NULL&#8217; undeclared (first use in this function)
wepattack.c:73: error: (Each undeclared identifier is reported only once
wepattack.c:73: error: for each function it appears in.)
wepattack.c:74: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
wepattack.c:74: error: &#8216;stdout&#8217; undeclared (first use in this function)
wepattack.c:75: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
wepattack.c:81: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
wepattack.c: In function &#8216;all_packets_cracked&#8217;:
wepattack.c:122: error: &#8216;NULL&#8217; undeclared (first use in this function)
wepattack.c: In function &#8216;loop_packets&#8217;:
wepattack.c:137: error: &#8216;NULL&#8217; undeclared (first use in this function)
wepattack.c:141: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
wepattack.c:146: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
wepattack.c:151: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
wepattack.c:156: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
wepattack.c: In function &#8216;sigint&#8217;:
wepattack.c:169: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
wepattack.c: In function &#8216;clean_up&#8217;:
wepattack.c:183: warning: passing argument 1 of &#8216;difftime_us&#8217; from incompatible pointer type
wepattack.c:183: warning: passing argument 2 of &#8216;difftime_us&#8217; from incompatible pointer type
wepattack.c:184: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
wepattack.c:190: error: &#8216;fp&#8217; undeclared (first use in this function)
wepattack.c:194: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;
wepattack.c: In function &#8216;main&#8217;:
wepattack.c:202: error: &#8216;FILE&#8217; undeclared (first use in this function)
wepattack.c:202: error: &#8216;pf&#8217; undeclared (first use in this function)
wepattack.c:206: error: &#8216;NULL&#8217; undeclared (first use in this function)
wepattack.c:210: error: &#8216;fp&#8217; undeclared (first use in this function)
wepattack.c:210: error: &#8216;stdin&#8217; undeclared (first use in this function)
wepattack.c:213: error: &#8216;SIGINT&#8217; undeclared (first use in this function)
wepattack.c:226: error: &#8216;optarg&#8217; undeclared (first use in this function)
wepattack.c:233: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
wepattack.c:255: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
wepattack.c:255: error: &#8216;stdout&#8217; undeclared (first use in this function)
wepattack.c:273: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
wepattack.c:291: warning: incompatible implicit declaration of built-in function &#8216;fprintf&#8217;
wepattack.c:309: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
make: *** [wepattack.o] Error 1


Any ideas?
Thanks..

---

### Post by SimonNewbie on 2007-01-10
i get the same error when i make this as well. It seems to be a known problem - can anyone help/explain what it is?


rooney@rooney-laptop:~/wep/WepAttack-0.1.3/src$ make
gcc -fno-for-scope -c -D__LINUX_WLAN__ -D__I386__ -o wepfilter.o wepfilter.c
cc1: warning: command line option "-fno-for-scope" is valid for C++/ObjC++ but not for C
wepfilter.c:21:18: error: pcap.h: No such file or directory
wepfilter.c:117: warning: ‘struct pcap_pkthdr’ declared inside parameter list
wepfilter.c:117: warning: its scope is only this definition or declaration, which is probably not what you want
wepfilter.c: In function ‘my_callback’:
wepfilter.c:121: error: dereferencing pointer to incomplete type
wepfilter.c:127: error: dereferencing pointer to incomplete type
wepfilter.c:127: error: dereferencing pointer to incomplete type
wepfilter.c:129: error: dereferencing pointer to incomplete type
wepfilter.c:129: error: dereferencing pointer to incomplete type
wepfilter.c: In function ‘get_packets’:
wepfilter.c:236: error: ‘PCAP_ERRBUF_SIZE’ undeclared (first use in this function)
wepfilter.c:236: error: (Each undeclared identifier is reported only once
wepfilter.c:236: error: for each function it appears in.)
wepfilter.c:237: error: ‘pcap_t’ undeclared (first use in this function)
wepfilter.c:237: error: ‘descr’ undeclared (first use in this function)
wepfilter.c:239: error: storage size of ‘hdr’ isn’t known
make: *** [wepfilter.o] Error 1

---

### Post by ZipoTe on 2007-01-10
well, if i'm not wrong,what i see is that you are missing "pcap.h" library. check it ^^

---

### Post by cmavr8 on 2007-01-11
But I do have libpcap0.8...
Isn't that the library "missing"?

Thanks for the reply ZipoTe!

---

### Post by ZipoTe on 2007-01-11
Ei cmavr8, mi answer was for SimonNewbie :p

Your code is:

> wepattack.c:21:18: error: time.h: No such file or directory
wepattack.c:22:22: error: sys/time.h: No such file or directory
wepattack.c:23:23: error: sys/timeb.h: No such file or directory
wepattack.c:24:19: error: stdio.h: No such file or directory
wepattack.c:25:20: error: stdlib.h: No such file or directory
wepattack.c:26:19: error: fcntl.h: No such file or directory
wepattack.c:27:22: error: sys/stat.h: No such file or directory
wepattack.c:28:19: error: errno.h: No such file or directory
wepattack.c:29:20: error: unistd.h: No such file or directory
wepattack.c:30:18: error: zlib.h: No such file or directory
wepattack.c:31:18: error: math.h: No such file or directory
wepattack.c:32:20: error: signal.h: No such file or directory


This all are librarys so if you don't install them you won't be able to run wepattack ;)

---

### Post by cmavr8 on 2007-01-11
Thank you for pointing that out, but where do I find those libraries? 

For instance, time.h can't be found in synaptics...

---

### Post by ZipoTe on 2007-01-12
Hi man

here you are some of them:
[http://www.koders.com/c/fid4AC4696027788117FCD3F8546A5964603F87BE8A.aspx]("http://www.koders.com/c/fid4AC4696027788117FCD3F8546A5964603F87BE8A.aspx")

---

### Post by cmavr8 on 2007-01-12
Thanks for the link. I downloaded the ones I needed, but before putting them in their positions I tried "make" once again, to make sure they were still needed.

Strange results:
chris@chris-laptop:~/Desktop/wa/src$ make
gcc -fno-for-scope -c -D__LINUX_WLAN__ -D__I386__ -o wepattack.o wepattack.c
cc1: warning: command line option "-fno-for-scope" is valid for C++/ObjC++ but not for C
wepattack.c: In function &#8216;loop_packets&#8217;:
wepattack.c:141: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
wepattack.c:146: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
wepattack.c:151: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
wepattack.c:156: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
gcc -fno-for-scope -c -D__LINUX_WLAN__ -D__I386__ -o rc4.o rc4.c
cc1: warning: command line option "-fno-for-scope" is valid for C++/ObjC++ but not for C
gcc -fno-for-scope -c -D__LINUX_WLAN__ -D__I386__ -o wepfilter.o wepfilter.c
cc1: warning: command line option "-fno-for-scope" is valid for C++/ObjC++ but not for C
wepfilter.c:21:18: error: pcap.h: No such file or directory
wepfilter.c:117: warning: &#8216;struct pcap_pkthdr&#8217; declared inside parameter list
wepfilter.c:117: warning: its scope is only this definition or declaration, which is probably not what you want
wepfilter.c: In function &#8216;my_callback&#8217;:
wepfilter.c:121: error: dereferencing pointer to incomplete type
wepfilter.c:127: error: dereferencing pointer to incomplete type
wepfilter.c:127: error: dereferencing pointer to incomplete type
wepfilter.c:129: error: dereferencing pointer to incomplete type
wepfilter.c:129: error: dereferencing pointer to incomplete type
wepfilter.c: In function &#8216;get_packets&#8217;:
wepfilter.c:236: error: &#8216;PCAP_ERRBUF_SIZE&#8217; undeclared (first use in this function)
wepfilter.c:236: error: (Each undeclared identifier is reported only once
wepfilter.c:236: error: for each function it appears in.)
wepfilter.c:237: error: &#8216;pcap_t&#8217; undeclared (first use in this function)
wepfilter.c:237: error: &#8216;descr&#8217; undeclared (first use in this function)
wepfilter.c:239: error: storage size of &#8216;hdr&#8217; isn&#8217;t known
make: *** [wepfilter.o] Error 1

---

