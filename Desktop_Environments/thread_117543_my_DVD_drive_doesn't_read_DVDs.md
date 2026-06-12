---
title: "my DVD drive doesn't read DVDs"
date: 2006-01-15
forum: Desktop Environments
---

### Post by Bou on 2006-01-15
Hi, I'm having lots of problems with my DVD drive. I don't normally even use DVDs, so this is kind of new to me. But, though I can watch DVD movies in Totem without a single problem, nautilus can't manage data DVD. Sometimes it doesn't mount them, sometimes they just freeze while copying files or even just while trying to create thumbnails... I'm trying to copy a movie to my hard drive right now, and it's telling me it will take 5 hours no less.

Now I stopped it and tried to eject the disc, but I got this message instead:

umount: /media/cdrom0: dispositivo ocupado
umount: /media/cdrom0: dispositivo ocupado
eject: el desmontaje de `/media/cdrom0' ha fallado

And the drive is doing all kind of noises. I don't think it's a hardware proble, because DVD movies work fine... might it be caused by DMA being turned on, or something like that?

Thanks a lot.

---

### Post by jasmuz on 2006-01-15
Saludos Bou,

Personalmente no uso Totem para decodificar mis DVD's sino Xine.
Encuentro sumamente extra&#241;o que Nautilus de est&#233; dando problemas, con la data del DVD. 

Errores para desmontar, generalmente es porque alguna parte del sistema aun est&#225; usando ese medio, cuando te suceda has esto:

sudo umount -l /media/cdrom0 (o como se llame tu unidad)
sudo eject

El ruido viene de la aceleracion y desaceleracion del disco en un brutal intento de lectura, rara vez est&#225; asociado con el hecho de que tengas el DMA activado...sino mas bien a problemas de lectura.

Pronto estar&#233; estudiando en Val&#233;ncia, mandame un mensaje para que charlemos.

---

