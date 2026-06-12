---
title: "problema con mga g200"
date: 2009-01-06
forum: Desktop Environments
---

### Post by zilog_z80a on 2009-01-06
cuando usamos el driver mga para la placa de video mga g200 a veces se experimenta una imagen difusa o doble como si estuviera corrido o presentase un fantasma para corregirlo editamos nuestro archivo xorg.conf y adicionamos la siguiente linea en Section "Device"

```

        Option          "OverclockMem"

```

la sección después del cambio debe verse aproximadamente así.

```

Section "Device"
        Identifier      "matrox"
        Driver          "mga"
        BusID           "PCI:1:00:0"
        Option          "OverclockMem"
EndSection

```

reiniciamos el pc y listo!!! eso hace el truco!!!

salu2!!! :D

---

