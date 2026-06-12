---
title: "Cross-compiler arm-linux-gcc assembler error"
date: 2009-04-30
forum: General Help
---

### Post by mbr5002 on 2009-04-30
Hello, my name is Matt and I am a graduate student who is new to Linux.
 
I am trying to cross-compile a simple C code in order to be executed on an Arcom Viper PXA255 RISC based PC/104 Single Board Computer. I have tried multiple C codes, but now I am just trying to get the simplest possible code to compile:
 
int main()
{
return 0;
}
 
I have installed the cross compiler directly from the software supplied by Arcom in their Viper Development kit. I am using Ubuntu 8.04 the Hardy Heron. I try the following line of code to compile, which was given in the Arcom manual:
 
$ arm-linux-gcc -o testcode -Wall -g -O2 testcode.c
 
And I get the following error:
 
Assembler messages:
Fatal error: Invalid -march= option: `armv4t'
 
I have not been able to make any sense out of this error, because `armv4t' IS a valid -march option for the compiler. The only real idea that I have come up with is that there may be some sort of version incompatibility either with the version of Ubuntu that I have or with the version of Linux Standard Base (LSB). The Arcom manual states that it must be compatible with LSB version 1.3. I have not figured out how to check what version I do have (does anyone know how?), but I am assuming it is newer than 1.3. Is LSB fully backwards compatible?
 
Any other ideas of what could be wrong or how to fix it would be great! Thank you!
 
Sincerely,
Matt

---

### Post by RajeshCB on 2009-05-26
Hi Matt ,

     Hope your Cross-compiler arm-linux .. error would have been solved by now. I just happened  to see your post on this forum . I too have been working on this Arcom - Viper PXA255 processor board .

But unfortunately I am unable to locate the CD (Viper Development Kit CD) :( I have an assignment to be finished asap but :( 

Do you have any idea as to where I can get the contents of the Development CD kit.

I am not able to figure out the exact version numbers of the GCC Compiler , binutils etc too so that atleast I can build my own cross - compiler.

Would be really great if you could help me out on ths.

Note :
If I am guessing it correctely , are these the commands that  you have been looking for  :
1) #> uname -a  : This gives the version number of the kernel thats currently installed.
2) #> **file** a.out : This gives the type of the ELF file and describes about the Endianess , GNU Linux version etc.

Thanks Matt in advance fior you time and help !

Best regards ,
Rajesh CB

---

