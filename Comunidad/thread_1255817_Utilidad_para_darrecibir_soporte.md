---
title: "Utilidad para dar/recibir soporte"
date: 2009-09-01
forum: Comunidad
---

### Post by sergiom99 on 2009-09-01
Miren que bueno lo que armaron en el LoCo chileno [1].

Se podrá armar o implementar algo parecido?

Saludos.
-Sergio

[1] [http://ubuntuforums.org/showthread.php?t=1211568](http://ubuntuforums.org/showthread.php?t=1211568)

---

### Post by juancarlospaco on 2009-09-01
Que idea original, esta buena...
:)

---

### Post by mama21mama on 2009-09-02
Alguien lo probo de que se trata?

Saludos

---

### Post by marianom on 2009-09-02
Hay [otro thread]("http://ubuntuforums.org/showthread.php?p=7889246") dando vueltas en este mismo foro donde la gente del LoCo chileno nos invita a participar.

---

### Post by sergiom99 on 2009-09-03
> **marianom said:**
> Hay [otro thread]("http://ubuntuforums.org/showthread.php?p=7889246") dando vueltas en este mismo foro donde la gente del LoCo chileno nos invita a participar.

Este vino primero, pero si algun mod puede, mejor unirlos.

---

### Post by Mauro22 on 2009-09-03
> **mama21mama said:**
> Alguien lo probo de que se trata?

Saludos

Se trata de generar un "reporte" con la salida de varios comandos,de las categorias "Audio, Particiones, redes, Video Wifi" listo para pegar en el foro, ( incluye los tags code y /code )

Ejemplo:

Salida de Audio:

```

Escritorio:    GNOME

```


```

$lsb_release -a
Distributor ID:	Ubuntu
Description:	Ubuntu karmic (development branch)
Release:	9.10
Codename:	karmic

```


```

$aplay -l
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: ALC268 Analog [ALC268 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0

```


```

$lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```


```

$asoundconf list

```


```

$cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8900000 irq 21

```


```

$lsmod | grep -i snd
snd_hda_codec_realtek   203232  1 
snd_hda_intel          26600  2 
snd_hda_codec          69276  2 snd_hda_codec_realtek,snd_hda_intel
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75264  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm

```


```

$lsof /dev/snd/controlC0 /dev/snd/pcmC0D0c /dev/snd/pcmC0D0p /dev/snd/pcmC0D1p /dev/snd/pcmC0D2c /dev/snd/seq /dev/snd/timer
COMMAND    PID     USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
pulseaudi 3383 blackice   24u   CHR  116,7      0t0 4841 /dev/snd/controlC0
pulseaudi 3383 blackice   31u   CHR  116,7      0t0 4841 /dev/snd/controlC0

```

---

### Post by mama21mama on 2009-09-03
jaja pense que era una aplicación para postear texto plano para crear post.
Bueno tanto no me equivoque por que podes generar un reporte y luego lo subis.

Saludos

---

### Post by sergiom99 on 2009-09-04
Es excelente para implementar la costumbre de arrancar un post pidiendo ayuda informando de tu configuracion, en vez del clásico "se me rompio el sonido/wifi/video/HDD/etc. ayudenme. STOP" y que tengamos que adivinar qué es lo que estas tratando de sacar andando.

---

### Post by juancarlospaco on 2009-09-04
En Karmic, que la instalacion tiene unos lindisimos SlideShow,
en uno de ellos dice para obtener ayuda avanzada usar UbuntuForums.org
Muy buen detalle.

[I]Se comenta que mas adelante el UbuntuOne tendra ScreenSharing en tiempo real,
capas es mas facil ayudar a alguien asi.[/I]

---

