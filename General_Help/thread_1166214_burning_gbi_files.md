---
title: "burning gbi files"
date: 2009-05-21
forum: General Help
---

### Post by Pacopag on 2009-05-21
does anyone know of software that can burn gbi files?

thanks

---

### Post by KhurramM on 2009-05-21
If u wanna burn it on a CD, just use any CD/DVD burner.

If u wanna extract it tools are there:
MagicISO
gBurner

---

### Post by Janoma on 2009-05-22
> **KhurramM said:**
> If u wanna burn it on a CD, just use any CD/DVD burner.

If u wanna extract it tools are there:
MagicISO
gBurner

I don't think you understood the question. MagicISO and gBurner are Windows utilities. What we need is a software to burn .gbi *images* into a disc -- in Ubuntu.

---

### Post by Rany . on 2009-06-09
so any solution for linux yet?

---

### Post by Pacopag on 2009-06-09
I haven't found a solution yet. I had to go to a windows machine to burn it.

---

### Post by camoril on 2009-06-25
under ubuntu ...K3B can burn .GBI files .. i've tried it with a FFVII.gbi Image .. works fine!!

---

### Post by i666an on 2009-07-12
Hello

There is a way to burn/extract .gbi files in linux, just use daa2iso.

The easiest way is to use the windows version under wine.
1 download daa2iso.zip (google)
2 extract to new folder
3 copy the .gbi file to that folder
4 open Konsole and CD to that folder
5 TYPE wine daa2iso.exe name.gbi name.iso

**replace name with the name of the file**

this will extract the .gbi, then you can mount or view the files with eg Acetoneiso2.

Hope this helps

---

### Post by hackbox on 2009-07-16
This works like a charm!  Thanks!

---

### Post by i666an on 2009-07-16
Hello

You are welcome. BTW the same chap wrote uif2iso (uif files), and it works in exactly the same way as daa2iso.

Glad it helped you.

---

### Post by embuntu0 on 2009-08-21
Hi guys,

I am trying to do a similar thing - i have run the process as instructed above but get the following error:

"- open abc.gbi
- create abc.iso

Error: wrong DAA signature (&#65533;&#65533;&#65533;)"

Any ideas?

Thanks

---

### Post by merikilpikonna on 2009-09-02
> **camoril said:**
> under ubuntu ...K3B can burn .GBI files .. i've tried it with a FFVII.gbi Image .. works fine!!
how does it work?
i downloaded it, but it says
"Seems not be a usable image"

is there a way not using wine or windows?

edit:
i am trying to install daa2iso doing the following:
1. downloaded the .zip file
2. extracted the daa2iso.exe and the folder scr to the Desktop
3. type in terminal sudo make install daa2iso.exe
but i get the error
"make: *** No rule to make target `install'.  Stop."

The build-essential package is installed. 
What am I doing wrong?

---

### Post by marius_siuram on 2009-09-13
nops, this is not a piece of linux software (so you cannot make a sudo make install xD). It's a Windows executable, and it can be used as a workaround with wine.

If you do not have wine (not a windows emulator, but a windows emulator...) then "sudo apt-get install wine". You then will be able to execute windows programs, as this daa2iso.exe:
wine daa2iso.exe <arguments>


[Founded this thread throuhg google, gonna test it myself soon ;) ]

---

### Post by uMuppet on 2009-09-19
K3b does NOT work with this.  Other instructions work fine.  Thanks for your help!

---

### Post by joopbraak on 2011-05-22
Just install daa2iso from the repository (Lucid and up).
It can do this.

daa2iso foobar.gbi foobar.iso

Simple as that.

---

