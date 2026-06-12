---
title: "U5.10 Not Installing on MS Virtual Machine"
date: 2005-11-13
forum: Desktop Environments
---

### Post by mageworx on 2005-11-13
:confused: I am a new bee... I am trying to install the Ubuntu 5.10 on a MS Virtual machine, it stops after the initial startup of the installation process.
This is where it hangs:
=====================================
ocksize                                                                        
[4294671.360000] EISA: Probing bus 0 at eisa.0                                 
[4294671.363000] EISA: Detected 0 cards.                                       
[4294671.367000] NET: Registered protocol family 2                             
[4294671.378000] input: AT Translated Set 2 keyboard on isa0060/serio0         
[4294671.380000] invalid operand: 0000 [#1]                                    
[4294671.380000] Modules linked in:                                            
[4294671.380000] CPU:    0                                                     
[4294671.380000] EIP:    0060:[<c0101127>]    Not tainted VLI                  
[4294671.380000] EFLAGS: 00000286   (2.6.12-9-386)                             
[4294671.380000] EIP is at mwait_idle+0x23/0x40                                
[4294671.380000] eax: c0322008   ebx: c0322000   ecx: 00000000   edx: 00000000 
[4294671.380000] esi: 00039100   edi: c035e120   ebp: 003b2007   esp: c0323fec 
[4294671.380000] ds: 007b   es: 007b   ss: 0068                                
[4294671.380000] Process swapper (pid: 0, threadinfo=c0322000 task=c0299b80)   
[4294671.380000] Stack: 00020800 c01010a1 c0324665 c035f820 c010019f           
[4294671.380000] Call Trace:                                                   
[4294671.380000]  [<c01010a1>] cpu_idle+0x2d/0x42                              
[4294671.380000]  [<c0324665>] start_kernel+0x176/0x178                        
[4294671.380000] Code: 01 89 04 24 75 cc 58 c3 53 fb ba 00 e0 ff ff 21 e2 8b 42
08 a8 08 75 2e 0f ba 6a 08 10 31 c9 bb 00 e0 ff ff 21 e3 89 ca 8d 43 08 <0f> 01
c8 8b 43 08 a8 08 75 0c 89 c8 0f 01 c9 8b 43 08 a8 08 74                       
[4294671.380000]  <0>Kernel panic - not syncing: Attempted to kill the idle task
!                                                                              
========================================================

Anyone here who can help and guide me with this.
I dont want to dedicate the whole machine to Ubu, dont want to run the Live CD as I want to really explore the OS and move over from MS once I am satisfied.

I have Win XP also installed on the Virtual machine, that I can run without any issues.
My Machine:
Win 2000
RAM: 1024 MB
E2.8GHz Processor.
The partition on the HD for the Virtual Linux is 16 G

Any one with thoughts suggestions, please e-mail at [email]mageworx@gmail.com[/email]

Thanks 
KK:confused:

---

### Post by exkalibur on 2005-11-15
It won't install if you're using the MS virtual PC software.......only for windows operating systems....

Regards

---

### Post by eas on 2005-11-26
I don't know what exkalibur is talking about.  I've run Hoary on Virtual PC 2004 for a few months and just did a fresh install using Breezy badger.

If I understand right, you are using a raw partition for your linux hard disk?  I've not tried that technique, but you might see if you have the same problem with a virtual disk (which is what I'm using)

---

