---
title: "[SOLVED] Acrobat Reader 8.11 requires asian font package"
date: 2008-03-27
forum: Desktop Effects &amp; Customization
---

### Post by hosammy on 2008-03-27
I have installed the Acrobat Reader 8.11 through Getautomix. The Acrobat Reader cannot display the Traditional nor Simplified Chinese and requests me to download the relevant font packages. Then I go to [http://www.adobe.com/products/acrobat/acrrasianfontpack.html](http://www.adobe.com/products/acrobat/acrrasianfontpack.html) and download two files, namely:

FontPack81_chs_i486-linux.tar.gz  &  FontPack81_cht_i486-linux.tar.gz

In the web page, it said that the file will teach me how to install these packages after unzipped, however, I cannot find the relevant document to teach me.

Please help to teach me to install these font support plugins.

Furthermore, I have also install the "xpdf" from Synaptic including the Traditional and Simplified Chinese support but still cannot display the correct font.
Please advise ...

---

### Post by polmir on 2008-03-27
After download on disc of fonts.
Unpack it:
```
tar zxvf FontPack81_chs_i486-linux.tar.gz
tar zxvf FontPack81_cht_i486-linux.tar.gz
```
after this go to folders CHSKIT and CHTKIT and run  script INSTALL as sudo/root.

You download and install Adobe Reader for Linux.

---

### Post by hosammy on 2008-03-27
I type: sudo install in the folder after unzip.
It replies that missing the document operating number and asks me to use "install --help" to check the error.

May I know which folder I should install or what parameter I should use.

---

### Post by polmir on 2008-03-28
Before
You download and install Adobe Reader for Linux

---

### Post by hosammy on 2008-03-29
> **polmir said:**
> Before
You download and install Adobe Reader for Linux

I have done it. But for the pdf file requires the asian font package to view it.

---

### Post by hosammy on 2008-03-31
> **polmir said:**
> After download on disc of fonts.
Unpack it:
```
tar zxvf FontPack81_chs_i486-linux.tar.gz
tar zxvf FontPack81_cht_i486-linux.tar.gz
```
after this go to folders CHSKIT and CHTKIT and run  script INSTALL as sudo/root.

You download and install Adobe Reader for Linux.

After unzipped, I placed the simplified Chinese at ..../Temp/CHSKIT/

[COLOR="DarkRed"]sammy@sammy-desktop:~/Temp/CHSKIT$ ls
BINCOM.TAR  INSTALL  LANGCHS.TAR  LANGCOM.TAR  LICREAD.TXT[/COLOR]
[COLOR="DarkOliveGreen"]sammy@sammy-desktop:~/Temp/CHSKIT$ ./configure
bash: ./configure: No such file or directory[/COLOR]
[COLOR="Blue"]sammy@sammy-desktop:~/Temp/CHSKIT$ make
make: *** no designated target and cannot find. Stopped.[/COLOR]
[COLOR="Red"]sammy@sammy-desktop:~/Temp/CHSKIT$ sudo make INSTALL
[sudo] password for sammy:
make: nothing to do for  `INSTALL'&#12290;
sammy@sammy-desktop:~/Temp/CHSKIT$ 
[/COLOR]

The above procedure had referred to [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)


Please advise ...

---

### Post by polmir on 2008-03-31
No. This is not sources package. You run INSTALL script. 
```
sudo apt-get install mc
```
After installation, type in terminal
```
sudo mc
```
open in mc FontPack81_chs_i486-linux.tar.gz
and mark --- INSTALL --- put Enter

[howto mc ](http://www.debian.org/doc/manuals/reference/ch-tutorial.en.html#s-mc)
[mc]("http://www.ibiblio.org/mc/")
[wiki mc]("http://en.wikipedia.org/wiki/Midnight_Commander")

---

### Post by hosammy on 2008-04-01
> **polmir said:**
> 
open in mc FontPack81_chs_i486-linux.tar.gz
and mark --- INSTALL --- put Enter



How can I open the FontPack81_chs_i486-linux.tar.gz ? I cannot find the command in mc??
I cannot find the INSTALL in the menu, please elaborate more???

---

### Post by polmir on 2008-04-01
Use key arrow and enter or click mouse.

---

### Post by hosammy on 2008-04-01
> **polmir said:**
> Use key arrow and enter or click mouse.

After I enter "sudo mc", then enter my password. The mc window comes out.

At the top, there are 5 selections, namely, Left(L),  File(F), Command(C), Option(O) & Right(R)
At the centre of the window, it shows the files and folders,
At the bottom, a root command line appear, under the root command line, there are 9 selections, 1. Help, 2. Menu, 3. View, 4. Edit, 5. Copy, 6. Rename, 7. make Directory, 8. Delete & 9. Exit.

I use the mouse left double click the FontPack81_chs_i486-linux.tar.gz file, it shows:
~/Temp/FontPack81_chs_i486-linux.tar.gz#utar 
at the top just under the top 5 selections and left window show the sub-directory CHSKIT.

I try to right click the FontPack81_chs_i486-linux.tar.gz file, it only shows some menu with the terminal.

I type "INSTALL" at the root command line, the mc window disappear and shows the terminal for 1 second and resume.

Where can I use the "INSTALL"
Please advise ...

---

### Post by polmir on 2008-04-01
Instruction for mc

---

### Post by hosammy on 2008-04-01
> **polmir said:**
> Instruction for mc
???
at the command line, type: man mc     ?

or
see what instruction for mc, please clarify???
Thanks ...

---

### Post by PmDematagoda on 2008-04-01
Without obtaining Adobe Reader from Getautomatix why don't you obtain Adobe Reader from the official [page]("http://www.adobe.com/products/acrobat/readstep2_allversions.html")? Perhaps you may have better luck with it especially since the package at the official download page is a newer version.

---

### Post by polmir on 2008-04-01
I am sorry. My attachment isn't upload.

---

### Post by hosammy on 2008-04-02
> **polmir said:**
> Instruction for mc

After following the detailed instructions, I can install both font packages now.

My problem is solved now.
:lolflag:

---

