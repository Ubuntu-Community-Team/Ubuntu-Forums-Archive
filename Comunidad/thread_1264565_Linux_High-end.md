---
title: "Linux High-end"
date: 2009-09-12
forum: Comunidad
---

### Post by xpelaox on 2009-09-12
Hola gente? que tal? Toda la vida use ubuntu, pero hace unas semanas me arme una maquinola nueva y quiero sacarle el jugo al maximo. Ademas me interesa mucho virtualizar. Hasta ahora con vmware 6.5 y ubuntu 9.04 X64 pude emular Win7 sin problemas( Relativamente, pienso que puede dar mucho mas de si), y hasta jugar al monkey island 5 xD

en fin, la maquina es:
Intel core i7 920 ( 4nucleos HT)
6gb ddr3 Tri channel
Asus Rampage ii gene
Ati radeon HD4850 (que me dio un par de problemas, pero se soulciono con los ultimos dirvers)

El tema es: Que Distro de Linux Creen que es la mejor optimizada para manejar los recursos de mi maquina? Algun Kernel particular? (lei sobre kernels "vanilla" pero ni idea, nunca me adentre en temas kernel)
Sobre virtualizacion: Hasta ahora a mi parecer (a pesar de ser pago y demas) es Vmware. Estoy usando Vmware Workstation 6.5, pero lei sobre otras versiones mas "Complejas" como Vmware ESX. Cual seria la mejor? vmware workstation funciona bien, pero tiene un par de limitaciones, por ejemplo, no me deja asignarle mas de 2 nucleos a una maquina guest, y teniendo 8, poder asignarle mas, seria mucho mas util.

En fin, Si leyeron todo, Gracias por su tiempo! Y si me pueden aconsejar, Mejor aun xD

Saludos!

---

### Post by z37a on 2009-09-12
> **xpelaox said:**
> Hola gente? que tal? Toda la vida use ubuntu, pero hace unas semanas me arme una maquinola nueva y quiero sacarle el jugo al maximo. Ademas me interesa mucho virtualizar. Hasta ahora con vmware 6.5 y ubuntu 9.04 X64 pude emular Win7 sin problemas( Relativamente, pienso que puede dar mucho mas de si), y hasta jugar al monkey island 5 xD

en fin, la maquina es:
Intel core i7 920 ( 4nucleos HT)
6gb ddr3 Tri channel
Asus Rampage ii gene
Ati radeon HD4850 (que me dio un par de problemas, pero se soulciono con los ultimos dirvers)

El tema es: Que Distro de Linux Creen que es la mejor optimizada para manejar los recursos de mi maquina? Algun Kernel particular? (lei sobre kernels "vanilla" pero ni idea, nunca me adentre en temas kernel)
Sobre virtualizacion: Hasta ahora a mi parecer (a pesar de ser pago y demas) es Vmware. Estoy usando Vmware Workstation 6.5, pero lei sobre otras versiones mas "Complejas" como Vmware ESX. Cual seria la mejor? vmware workstation funciona bien, pero tiene un par de limitaciones, por ejemplo, no me deja asignarle mas de 2 nucleos a una maquina guest, y teniendo 8, poder asignarle mas, seria mucho mas util.

En fin, Si leyeron todo, Gracias por su tiempo! Y si me pueden aconsejar, Mejor aun xD

Saludos!

En o que se refiere a virtualizacion tenes muchas alternativas, aparte de VMware. En lo personal uso VirtualBox, me parece mas sencillo y potente que VMware, pero eso va en gustos. Tambien debo decirte que todo depende que que quieras virtualizar, el VMWare ESX es para virtualizar servidores, no es un programa si no un SO(creo que basado en RedHat) dedicado a la virtualizacion, donde el paquete base es gratis, peor hay ciertos agregados pagos. Como alternativa a la virtualizacion de Servers tenes KVM y XEN tambien. Pero para virtualizar Desktops lo que te conviene es Vmware workstation, parallels o virtualbox. Aun asi si es que virtualizas a full me parece que la RAM que tenes es poca, las maquinas virtuales consumen grandes cantidades de ram.

Si lo que queres es solo virtualizar desktops entonces te recomiendo Ubuntu(es el que me gusta) con Virtualbox(como dije son gustos).

PD: Tenes VirtualBox OSE tambien, que es la version 100% libre, pero la verdad que a mi gusto prefiero la comun, no sera tan libre pero tiene mas funciones y funciona muy bien.

---

### Post by juancarlospaco on 2009-09-12
KVM o VirtualBox

---

### Post by xpelaox on 2009-09-12
Gracias por la data! yo siempre probe el Virtualbox OSE, y me parecio menos potente que el vmware, no sabia que habia otra version, la voy a probar.

en cuanto a la ram, vos decis que 6gb es poco para tener linux host y algun windows invitado?

---

### Post by marianom on 2009-09-12
> **xpelaox said:**
> Gracias por la data! yo siempre probe el Virtualbox OSE, y me parecio menos potente que el vmware, no sabia que habia otra version, la voy a probar.

en cuanto a la ram, vos decis que 6gb es poco para tener linux host y algun windows invitado?

Te sobra!!! Yo uso qemu para virtualizar algún xp, algún debian, centos y opensolaris.

---

### Post by z37a on 2009-09-12
> **xpelaox said:**
> Gracias por la data! yo siempre probe el Virtualbox OSE, y me parecio menos potente que el vmware, no sabia que habia otra version, la voy a probar.

en cuanto a la ram, vos decis que 6gb es poco para tener linux host y algun windows invitado?

Para solo un windows te sobra, ahora si haces como yo que a veces virtualizo un server y 2 clientes andas justo(por eso mi pc tiene 4Gb por ahora pero le pienso agregar otros 4 en estos dias!!!).

Para el virtualbox anda a [http://www.virtualbox.org/](http://www.virtualbox.org/) te recomiendo agregar el repositorio oficial de virtualbox, asi se actualiza y no tenes que bajar a mano el deb cada vez que sale uno nuevo.

Con lo que te comentaron atras KVM es una muy buena opcion tambien, pero la verdad es que KVM esta pensado mas que nada para servidores, con VirtualBox podes virtualizar escritorios y encima te soporta video3d para las maquinas virtuales.

---

### Post by guillermolisi on 2009-09-12
> **z37a said:**
> Pero para virtualizar Desktops lo que te conviene es Vmware workstation, parallels o virtualbox.

Salvo que esto haya cambiado, Parallels es pago (originalmente pensado para virtualizar en entornos Apple).

---

### Post by xpelaox on 2009-09-13
Cheeeeeeeeeeeeeeee, Estoy probando Virtualbox y me sorprendio! Una masa! Le pude asignar 6 nucleos al OS y va como piña, aun estoy viendo bien como implementar Direct3D, pero va como piña!

---

### Post by z37a on 2009-09-13
> **guillermolisi said:**
> Salvo que esto haya cambiado, Parallels es pago (originalmente pensado para virtualizar en entornos Apple).

Si peor esta disponible para Ubuntu y bueno es una alternativa mas, paga pero una alternativa al fin. Tambien VMWare workstation es pago!!!!!

xpelaox, me alegra que te guste el VirtualBox, para mi es el mejor a la hora de virtualizar desktops, hasta te permite utilizar las instrucciones de virtualizacion del micro para mejorar el rendimiento!!! Como dije antes para mi es el mejor lejos en desktop, en server no se cual sera mejor si KVM o XEN, me gustan los dos y son parecidos a grades rasgos(muy muy grandes rasgos jajja).

---

### Post by faktorqm on 2009-09-14
> **xpelaox said:**
> Cheeeeeeeeeeeeeeee, Estoy probando Virtualbox y me sorprendio! Una masa! Le pude asignar 6 nucleos al OS y va como piña, aun estoy viendo bien como implementar Direct3D, pero va como piña!

¿como es que asignas 6 nucleos si tenes 4? :O

---

### Post by Cresho on 2009-09-14
virtualbox sin OSE.  Virtualbox QT

[http://www.virtualbox.org/wiki/Screenshots](http://www.virtualbox.org/wiki/Screenshots)

---

### Post by xpelaox on 2009-09-14
> **faktorqm said:**
> ¿como es que asignas 6 nucleos si tenes 4? :O

Son 4 nucleos HT, El S.O Te toma 8 Nucleos. La misma tecnoclogia de los Pentium 4 HT xD

---

### Post by z37a on 2009-09-14
> **xpelaox said:**
> Son 4 nucleos HT, El S.O Te toma 8 Nucleos. La misma tecnoclogia de los Pentium 4 HT xD

Igualmente tenes algo llamado VCPUs, te crea CPUs virtuales, la verdad nunca lo use, se que se puede, pero no tengo idea si esta implementado en VirtualBox ni como anda!!!!!

---

### Post by Hei Ku on 2009-09-14
> **z37a said:**
> Igualmente tenes algo llamado VCPUs, te crea CPUs virtuales, la verdad nunca lo use, se que se puede, pero no tengo idea si esta implementado en VirtualBox ni como anda!!!!!

A mi me lo hicieron. Tenia una terminal VMWare que me dijeron que tenia 2 cores y 2GB de RAM y andaba como si tuviera medio core y 256MB. :lolflag:

Probablemente esa funcionalidad sea para cuando tenes un servidor que emula un numero interesante de maquinas virtuales y quieras manejarlos por separado. Igual, no deja de ser una mentira, como el entrelazado, o en algun momento los discos virtuales, etc.

---

### Post by xpelaox on 2009-09-15
cheeee VBox Funca mucho mejor, PERO no logro hacer funcionar Direct3d :( y en vmware si pude, un bajon!

Algun tip?

---

### Post by z37a on 2009-09-16
> **xpelaox said:**
> cheeee VBox Funca mucho mejor, PERO no logro hacer funcionar Direct3d :( y en vmware si pude, un bajon!

Algun tip?

Jamas lo intente la verdad, pero segun escuche el tema viene por el directx, al parecer la placa virtual soporta directx9 y no 10 u 11. Habria que ver si no viene pro ese lado.

---

