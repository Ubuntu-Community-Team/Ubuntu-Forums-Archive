---
title: "Ubuntu Installation Problems in Dell Inpiron N4010"
date: 2011-07-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by skynet1722 on 2011-07-15
Hola, Tengo una notebook dell Inspiron N4010, procesador core I5 con Windows 7 home premium. El disco rigido de 500gb tiene una particion de 15gb que posee una imagen del SO para su restauracion. 

Instale el Ubuntu 11.04 de 64bits. Inicie bien, reinicie la notebook entre en windows sin proplemas, apague la notebook. Luego al encenderla de nuevo me aparecio la pantalla negra y decia "no module name found".

Busque en internet y en algunos foros decian que debia iniciar ubuntu, instalar el Grub y luego entrar en win7 y desinstalar el "Dell Data Safe" por que de alguna manera este programa desinstalaba en grub. Lo hice y no funciono. 

Pero en otro foro decian que el problema es la particion de 15gb oculta, de la imagen del SO win7 la uqe me creaba el problema. 

Pero el problema de esto es que la notebook no venia con un disco de instalacion del windows 7, y me comunique con soporte tecnico de dell y ellos no envian los discos del SO. 

Pero los de soporte tecnico de dell me dijeron que debo realizar una restauracion de fabrica del disco rigido, para eliminar el problema. Asi que voy a tener que sacar 200gb de datos del disco rigido y almacenarlo en alguna otra unidad externa para hacer la restauracion de fabrica.

Pero como hago para instalar el Ubuntu y que no pase de nuevo esto.

(La unica razon por la que no elimino el disco y dejo el ubuntu nada mas, es por que no quiero perder la licencia del SO win7)

Actualmente estoy entrando a mi pc con Hiren Boot 12. Asi puedo elejir iniciar con Windows 7.

Importante: La particion que tenia ubuntu la elimine y le agrege el espacio que me quedo a la particion con windows 7. Asi la notebook quedo en lo que respecta a particiones tal como estaba antes del problema.

Espero sus ideas. Muchisssiiimas gracias

---

### Post by skynet1722 on 2011-07-15
Hi, I have a Dell Inspiron notebook N4010, I5 core processor with Windows 7 home premium. The 500GB hard drive has a 15GB partition that has an OS image to restore. 

Install the 64bit Ubuntu 11.04. Start, restart the notebook into windows without proplem, turn off the notebook. Then on again to me the black screen appeared and said "no module name found". 

Look  online and in some forums said he should start ubuntu, install grub and  then enter win7 and uninstall "Dell Data Safe" that somehow this  program uninstall grub. I did and did not work. 

But in another forum said the problem is the 15GB partition hidden from the OS image I created uqe win7 the problem. 

But  the problem is that the notebook did not come with a Windows  installation disc 7, and I contact dell tech support and they do not  send the OS disks. 

But the Dell technical support told me that I must do a factory restore from hard disk to eliminate the problem. So I'm going to have to get 200GB of data from hard disk and store it in another external drive to the factory reset. 

But how do I install Ubuntu and it does not happen again. 

(The only reason I did not remove the disk and let ubuntu any more, is that I will not lose the license for the OS win7) 

I am currently entering my pc with Hiren Boot 12. So I can CHOOSE to start with Windows 7. 

Important: The ubuntu partition containing the deleted and added space to the partition I stay with Windows 7. Thus the notebook stay in regard to partition as it was before the problem. 

I welcome your ideas. Thanks

---

### Post by tjones00 on 2011-07-16
I have a dell inspiron 14r n4010 myself (i3 with intel HD integrated graphics). I have win7 and Xubuntu 11.04 (32b) installed side by side with no issues. 

I did not have to use any fancy gimmicks to properly install Xubuntu and grub. 

The reason I picked 32b over 64b is stability especially for non LTS releases. This is also the reason I picked Xubuntu (xfce) over standard (the new unity de). 

May I as what video card you have? The issue could be nvidia optimus. 

To me your no module name error is saying "I can't find the video driver" or perhaps it's an issue with the 64b Unity.

---

### Post by bapoumba on 2011-07-16
Threads merged.

---

### Post by varunendra on 2011-07-16
Hi skynet1722, and welcome to the forums!

Backing up your data and restoring the laptop to factory settings is a good idea.

Since you don't have the installation DVD for the installed Win7, creating backup DVDs from within Win7 should be your first step before trying anything else. Make sure these DVDs are working and don't need anything from the hard drive (like the recovery partition, or its contents). Once you have this confirmed, then you can experiment with your hard drive in whatever way you wish.

If you are not sure about the functioning of the recovery DVDs (like myself :)), I'd recommend to create a full disk image of the hard drive using clonezilla while Win7 is restored and there is no extra data on the hard drive.

After having ensured the backup of your Win7, we can proceed to troubleshoot the Ubuntu installation problems without worrying about you losing your licenced windows.

---

