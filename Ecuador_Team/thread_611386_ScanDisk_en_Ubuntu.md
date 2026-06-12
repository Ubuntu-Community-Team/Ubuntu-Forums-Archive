---
title: "ScanDisk en Ubuntu"
date: 2007-11-12
forum: Ecuador Team
---

### Post by compuniversal on 2007-11-12
Deseo saber si existe una aplicacion grafica que me permita hacer un Scan al Disco duro, para ver fallas y tambien a otros dispositivos como la memoria y demas componentes. Existe un comando que le hice en el terminal pero me decia que si corria que podia perder datos. Gracias por la ayuda :confused:

---

### Post by hubuntu on 2007-11-16
fsck es el "scandisk" en linux. En Linux en general no se necesita scandisks puesto que (dependiendo de que sistema de archivos se use) los sistemas de archivo son jornalizados, osea están hechos de tal forma que no guardan las cosas por aquí por allá a la maldita sea como FATXXy en cierta forma NTFS hace. 

Para chequeo gráfico.. mmm no creo que es posible debido a que el disco a repararse debe estár en modo de solo lectura. Lewcto escritura podría arruinar el sistema.

En ubuntu el sistema de archivos es ext3 como estándar (se puede escoger otros tb, pero si no se cambia la opción es ext3) y fsck arregla los "males" del disco (de haberlos.)

El sistema hace un chequeo cada 30 días automáticamente.

Espero esto te de una idea del scandisk en linux.

R

---

### Post by por100pre1 on 2007-11-17
También puedes hacer un chequeo de inmediato con este comando en **Terminal**:

```
sudo touch /forcefsck && sudo reboot
```

NOTA: Este comando reinicia tu sistema y realiza un chequeo antes de poder regresar a tu escritorio, **puede tomar algún largo tiempo en realizarse**.

---

### Post by marcela on 2008-04-11
Pueden ayudarme por favor deseo ingresar a las comunidad de chicas Linuxeras de Ecuador.

Please ....

Marce

---

### Post by alfermp on 2008-04-28
Hola Marcela, para registrarte dentro del grupo de Ubuntu Ecuador puedes hacerlo dentro de [www.ubuntu.ec](www.ubuntu.ec) y agregarte tambien a la lista de distribucion. Saludos :guitar:
ecubuntu
[www.ecubuntu.com](www.ecubuntu.com)

---

### Post by piousp on 2008-04-28
Es bueno encontrarse con gente que hable español!:KS

---

