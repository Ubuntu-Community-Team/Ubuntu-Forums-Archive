---
title: "No sound in quake 3 HELP"
date: 2008-10-24
forum: Gaming &amp; Leisure
---

### Post by jcer93705 on 2008-10-24
Hi i have quake 3 installed, it run but without sound. I useto know
the command. It would enable the sound. This command was located at 
gentoo website or forum. Anyways I copy this and now i'm going to paste
the error

------- sound initialization -------
Could not mmap dma buffer PROT_WRITE|PROT_READ
trying mmap PROT_WRITE (with associated better compatibility / less performance code)
/dev/dsp: Input/output error
Could not mmap /dev/dsp
------------------------------------
Sound memory manager started
Loading vm file vm/ui.qvm.
VM file ui compiled to 594408 bytes of code
ui loaded in 1963008 bytes on the hunk
35 arenas parsed
32 bots parsed
--- Common Initialization Complete ---
Opening IP socket: localhost:27960
Hostname: ubuntu.ubuntu-domain
Alias: ubuntu
IP: 127.0.1.1
Started tty console (use +set ttycon 0 to disable)
^5PunkBuster Client: PunkBuster Client (v0.993 | A0) **DISABLED**
^3PunkBuster Server: PunkBuster Server (v0.993 | A0 C0.0) **DISABLED**
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Shutdown tty console


Can someone help me??

---

### Post by Azure.Rise on 2008-10-25
Try this:
echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

---

### Post by Rotarychainsaw on 2008-10-29
how bout 

padsp quake3

---

