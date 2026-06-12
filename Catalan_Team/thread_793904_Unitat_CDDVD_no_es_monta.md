---
title: "Unitat CD/DVD no es monta"
date: 2008-05-14
forum: Catalan Team
---

### Post by prostata on 2008-05-14
Des que vaig actualitzar a Ubuntu Hardy no es monta  l'unitat CD/DVD, sempre envia el consabut messatge no es pot montar l'arxiu. 

Aquest és el meu actual fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c1e1381e-dc30-4947-8716-ce856c922321 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f27db275-0f4a-4c52-9339-ecb9a5f381eb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
usbfs /proc/bus/usb usbfs devgid=14,devmode=0660 0 0

De fet la situació és la següenta:
Monto un DVD/CD amb dades i es monta l'unitat
Monto un DVD/CD verge per fer-lo anar amb K3b o Brasero i no es monta

¿qué puc fer?

salutacions

---

### Post by prostata on 2008-05-14
em sembla que tinc una pista; he possat un DVD per gravar amb brasero unes pelis. el DVD era verge, Verbatim DVD-R, els que sempre faig servir. per alguna raó brasero no ha pogut gravar, l'ha expulsat, segur que malgrat tot a gravat alguns bits i per tant el DVD ha quedat "brut"....¿podrìa ser aquesta la causa??

salutacions

---

### Post by orestesmas on 2008-05-14
> **prostata said:**
> em sembla que tinc una pista; he possat un DVD per gravar amb brasero unes pelis. el DVD era verge, Verbatim DVD-R, els que sempre faig servir. per alguna raó brasero no ha pogut gravar, l'ha expulsat, segur que malgrat tot a gravat alguns bits i per tant el DVD ha quedat "brut"....¿podrìa ser aquesta la causa??

salutacions

No ho sé, però el que no has de pretendre és que et munti un DVD verge, perquè no hi ha res (cap sistema de fitxers, vull dir) per muntar.

---

