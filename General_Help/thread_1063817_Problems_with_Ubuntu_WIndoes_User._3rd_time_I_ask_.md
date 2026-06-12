---
title: "Problems with Ubuntu WIndoes User. 3rd time I ask for help."
date: 2009-02-08
forum: General Help
---

### Post by Bonsanto on 2009-02-08
Well I am a WIndows Xp user who installed Ubuntu in a slave HDD, I did I was so happy, But WHen I tried Ubuntu System I got many problems.

The problems started when I got a problem iitializing Ubuntu, It asked to run chdsrk in Windows to repair something in ubuntu or somthing like that. I did, then went back to Ubuntu, and soemthing like this was showed.

Well a friend was trying to help me with my problems, He couldn't solve. I restarted my pc becouse again Ubuntu crashed. I got the next error.

/lib/init/rw/rootdv Unexpected Inconsistency; run fsck manually
(i.e, without -a or -p option)
fsck died with exit status 4

*An automatic file system check(fsck) of the root filesystem failed
A manual fsck must be perfomed, thn the system restarted.
The fsck should be perfomed in mantainance ode with the root fylesystem mounted in read-only mode.

*The root file system is currently monted in read-only mode
A maintenance will now start
Bosh: no fob control in this shell.

Well I don't know what I did to solve that problem.

But when I went back to Ubuntu, I started having problems again with my HDD comunications, I mean when I try to open my other HDD The system asked for password and password, I typed mine But didn't work. 

[img]http://i529.photobucket.com/albums/dd332/xBonsantox/Moreproblems.jpg[/img]

[img]http://i529.photobucket.com/albums/dd332/xBonsantox/Pantallazo-2.jpg[/img]

Then the system crashed I restarted my Pc an asked again for the same previous code, I did the same and after that I restarted the PC, And the HDD communication problem was solved well that as what I thought After 1 day I went again to Ubuntu and now I can't communicate to one of my HDD, this is what is showed.

[IMG]http://i529.photobucket.com/albums/dd332/xBonsantox/Pantallazo1.png[/IMG]

**My Bigger Probem is the crash of my SYstem**, When I open 4 firefox or 1 game+ Amsn, The system Crashes.

People think that I lie But I don't I have a video when I try to close aplications and I can't.


I forgot My Pc is is a Pentium 4 Hyper Threading. 3.0Ghz. 1Gb Ram.
When I am in WIndows XP My system doesn't crash.

PLease help me or I will have to come back to WIndows.

---

### Post by ugm6hr on 2009-02-08
I'm afraid I can't follow everything you have said.

But, the fact that fsck errored is concerning.

Is it possible there is a hardware fault with the HD Ubuntu is installed on?

Does Ubuntu run well from the LiveCD?

Did you check the LiveCD for errors before installing?

PS: Please try and avoid using inline large screenshots.

---

### Post by Bonsanto on 2009-02-08
I installed it in a HDD i don't use the liveCD.

---

### Post by Taras.M.K on 2009-02-08
Well, I didn't caught your explanations well too.
Firstly you've said, you "I had to run chdsrk or somthing like that in Windows to repair something in ubuntu". What type of filesystem do you use for your Ubuntu? It shouldn't be ntfs of fat32, so nothing from Windows can be rapaired. If even you can see your Ubuntu disk from Windows, you'd better not do any repairings in it.

And your last screenshot says your ntfs partitions was not shut clean. It's Windows partition. The most simple way is to run your Windows and then to shut it down in a normal way. And this message should disappear.

---

### Post by Bonsanto on 2009-02-08
Ntfsc, and In the Ubuntus's HDD I just have the Ubunt's SO and some docs.

---

### Post by ugm6hr on 2009-02-08
Did you install Ubuntu within Windows (using Wubi)?

Please describe exactly how you installed to your HD, since this makes a difference.

---

### Post by Bonsanto on 2009-02-08
I will SS it Wait. :D

Yes I used Wubi, the second option

---

### Post by Bonsanto on 2009-02-08
Please help

---

### Post by jmszr on 2009-02-08
Bonsanto,
           This might help,also there is a Wubi section in these forums and they may well have more specific knowledge dealing with your particular problem:

Try The Following Solution: 1) Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu (Wubi) in.Click Properties.
Select the "Tools" tab and click "check now" under error checking( On Vista, You might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After The checking is done, restart the pc by using the start menu(Do not hard reboot) and try using ubuntu now.

You also might try installing Wubi to your master drive (defragment your Windows drive first).

---

### Post by Bonsanto on 2009-02-08
I reinstalled Ubuntu and I still having the restart problem, maybe is a hardware? My processor? I don't know HELP!

---

### Post by sune_cph on 2009-02-08
Have you tried booting from the ubuntu cd directly (as to avoid harddrive access)? You are aware that Ubuntu loads directly from the install cd so that you can test for any hardware issues without actually installing ubuntu?

You can test your system RAM using the memtest option in the boot loader - it will probably fail if you have cpu/ram malfunctions.

/Sune

---

### Post by Bonsanto on 2009-02-08
Can you be more explicit please, exact tell me what to do step by steps, please.

---

### Post by sune_cph on 2009-02-08
1) The bios boot order must be set to start from your CD-ROM drive.

2) When booting from the ubuntu cd, you should get this picture: [http://ubuntu.linuxin.dk/pictures/ubuntu0.png](http://ubuntu.linuxin.dk/pictures/ubuntu0.png)

3) Select "Start or Install Ubuntu" (to run Ubuntu from the cd) or "Memory Test" to test your RAM.

Hope this helps!

---

### Post by ugm6hr on 2009-02-08
> **sune_cph said:**
> Have you tried booting from the ubuntu cd directly (as to avoid harddrive access)? You are aware that Ubuntu loads directly from the install cd so that you can test for any hardware issues without actually installing ubuntu?

Explicit instructions:
1. Put the Ubuntu CD in CD drive.
2. Restart computer.
3. Enter "System BIOS" by pressibg the key advised at the very first screen you see after restart (i.e. BEFORE Windows screen) - often F2 or F12 or Delete key.
4. Go through BIOS options to select "boot from CD".
5. Save and Exit BIOS.

For more detail: [http://www.psychocats.net/ubuntu/dualboot](http://www.psychocats.net/ubuntu/dualboot) (just follow 1st 4 paragraphs of Starting the Installation - and select "Try Ubuntu without any change to your computer".

---

### Post by Bonsanto on 2009-02-08
I have 2 memory rams of 512.
I got 200 errors. But just one was on red. Should I quit it?

Note: Is hard to me find Memory rams to My pc, My Pc is old It uses 333Mhz :'(
And in my country is weird find those in my country :(

I don't get this WIndow OMG.

---

### Post by Osamabingandhi on 2009-02-08
You did the memoryscan from the ubuntu cd? If you did and got 200 error probably one memory is broken, try to take one out and redo the memorytest. Hopefully only one is broken. Don't know if that was what you did...

---

### Post by Bonsanto on 2009-02-08
Yes I did the memory scan, I will quit one.

---

### Post by ugm6hr on 2009-02-08
> **Bonsanto said:**
> I don't get this WIndow OMG.

This problem is nothing to do with Windows (or Ubuntu).

You have a hardware fault.

---

### Post by Bonsanto on 2009-02-08
Now I have this problem.
When I try to run the updates of Ubuntu it says "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." But when I type the thing in the terminal It says
 dpkg: `ldconfig' not found in the PATH.
dpkg: 1 program(s) waiting not found in the PATH.
 The PATH of root has to contain usually /usr/local/sbin, /usr/sbin y /sbin.

---

### Post by jmszr on 2009-02-08
Bonsanto,
            In the terminal:```
sudo dpkg --configure -a
```

---

### Post by sune_cph on 2009-02-09
If you have errors in Memtest86+ you *must* replace the bad ram (or remove it) -  it does not make sense to continue using/installing Ubuntu if you have memory corruption issues, even if this is not the source of your problems.

/Sune

> **Bonsanto said:**
> I have 2 memory rams of 512.
I got 200 errors. But just one was on red. Should I quit it?

Note: Is hard to me find Memory rams to My pc, My Pc is old It uses 333Mhz :'(
And in my country is weird find those in my country :(

I don't get this WIndow OMG.

---

### Post by Bonsanto on 2009-02-09
I did It. Now Ubuntu doesn't crash, But I got problems I can't update or install anything (Note I am translating from Spanish to English))

"An error has success; please, execute the packets manager form th terminal to see which is the problem".

The error message was: 'Error BrokenCount > 0' Normaly this means that you installed packets damaged "

Now I go to terminal and execute  "apt-get check" and this appear:

master@ubuntu:~$ sudo apt-get check
Reading list of packets... DOne
Making the dependency's tree
Reading the Status Info... DOne
Maybe you want to execute`apt-get -f install' to fix it.
The next packs has inculpate dependency:
libc6-dev: Depende: libc6 (= 2.8~20080505-0ubuntu8) but 2.8~20080505-0ubuntu7 is installed
E: Dependents inculpates.Try using -f.

I execute "apt-get -f install" and this is showed:

master@ubuntu:~$ sudo apt-get -f install
Reading list of packets... DOne
Making the dependency's tree
Reading Status Info... DOne
Fixing dependencys... DOne
Next extras packets will be installed :
libc6 libc6-i686
Suggested packets:
glibc-doc
Next packets will be installed:
libc6 libc6-i686
2 updated, 0 will be installed, 0 to delete y 236 no updated.
4 no installed del todo o eliminados.
You need to download 0B/5650kB de archivos.
You will use 0B of HDD aditional after unpack it.
¿Wanna continue [Y/n]?

I typed Y.

Preconfigurando paquetes ...
dpkg: `ldconfig' no encontrado en el PATH.
dpkg: 1 programa(s) esperado(s) no encontrados en el PATH.
El PATH de root debe contener usualmente /usr/local/sbin, /usr/sbin y /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)

Le volví a dar "apt-get check"

Salió lo mismo de más arriba.

Ejecuto "apt-get -f install" y sale esto:

master@ubuntu:~$ sudo apt-get -f install
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Corrigiendo dependencias... Listo
Se instalarán los siguientes paquetes extras:
libc6 libc6-i686
Paquetes sugeridos:
glibc-doc
Se actualizarán los siguientes paquetes:
libc6 libc6-i686
2 actualizados, 0 se instalarán, 0 para eliminar y 236 no actualizados.
4 no instalados del todo o eliminados.
Se necesita descargar 0B/5650kB de archivos.
Se utilizarán 0B de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]?

Respondí SI nuevamente. Salió esto

Des:1 [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) intrepid-updates/main libc6 2.8~20080505-0ubuntu8 [4364kB]
Des:2 [http://ve.archive.ubuntu.com](http://ve.archive.ubuntu.com) intrepid-updates/main libc6-i686 2.8~20080505-0ubuntu8 [1286kB]
Descargados 5650kB en 1min12s (78,1kB/s)
Preconfigurando paquetes ...
dpkg: `ldconfig' no encontrado en el PATH.
dpkg: 1 programa(s) esperado(s) no encontrados en el PATH.
El PATH de root debe contener usualmente /usr/local/sbin, /usr/sbin y /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)

Me voy al Synaptic Y aparece esto:

"Tiene 1 paquete roto en su sistema

Use el filtro «Rotos» para encontrarlo."

Le doy a editar Reparar archivos rotos, Le doy aplicar Se carga una barrar y aparece esto

Preconfigurando paquetes ...
dpkg: `ldconfig' no encontrado en el PATH.
dpkg: 1 programa(s) esperado(s) no encontrados en el PATH.
El PATH de root debe contener usualmente /usr/local/sbin, /usr/sbin y /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by sune_cph on 2009-02-09
Sorry but I dont understand spanish so I have no idea what these errors mean - perhaps there is a spanish-languaged ubuntu forum you could ask for help?

Anyway, did you try booting directly from the ubuntu livecd?

/Sune

---

### Post by Bonsanto on 2009-02-09
I burned my CDlive But, It doens't boot when I use it, I have to install it first in Windows :(

---

### Post by ugm6hr on 2009-02-10
As per my earlier advice: I think you should resolve your hardware problems (i.e. RAM) before persevering with this.  It will be impossible to work out whether your problems are hardware or software related until you fix your hardware.

---

### Post by Nunu on 2009-02-10
Hardware issue. Most likely with one of the memory modules.

---

### Post by Bonsanto on 2009-02-10
Guys I bought a new Memory ram I did the mem anaysis I don't have errors with it, I reinstalled Ubuntu But I still having the Crash PROBLEM HELP!!!!!!!!!

---

