---
title: "¡¡¡Se me fue el sonido!!!"
date: 2008-07-01
forum: Ecuador Team
---

### Post by rlarenas on 2008-07-01
He ido armando mi Ubuntu con algunos programas. Me interesa la música,:guitar: y por ello bajé el *rosegarden* (edición de música), *tuxguitar* (dibuja tablaturas de guitarra), *kmid* (para el karaoke); y para ver archivos de vídeo y música, el *vlc* (especialmente para ver vídeos tipo mpeg4 y flv, me gusta más que totem....).
:( Todo bien hasta ayer, cuando de repente, "Ubuntu" se me volvió "mudo":confused:. Ni un sólo sonido (ni siquiera el de entrada de Ubuntu). Entro por mis preferencias a "sonidos", y no me reconoce nada. ](*,).
Creo que el error se diò cuando intenté incluir un programa adicional: el *solfedge* (para entrenar el oído, escalas tonos y esas cosas), que vino "en paquete" con el "TiMidity", y me dio error al cargar.:oops:
Cuando intento entrar a rosegarden o tuxguitar, me dice que no encuentra dev/sequencer.  El comando "snd-seq-midi" en el terminal (me lo recomienda el mensaje de entrada a rosegarden) me da error, no encuentra el comando.[-o<
¿Algún fanático de la música y de Linux que me ayude?:-({|=

René Larenas

---

### Post by rlarenas on 2008-07-02
Intenté nuevas "pruebas" que quizá ayuden a entender el problema. Aquí mis "resultados":mad:
* Pulsando en el control de volumen, el mensaje dice: "El control de volumen no encontró ningún elemento y/o dispositivo que controlar. Esto significa que no tiene los complementos correctos de GStreamer instalados o que no tiene una tarjeta de sonido configurada". 
Rosegarden me da el siguiente error:
"La inicialización del secuenciador ha fallado. El subsistema MIDI ha fallado en su inicialización. Usted puede continuar sin el secuenciador, pero sugerimos que cierre Rosegarden, ejecute "modprobe snd-seq-midi" como usuario administrador, y reinicie Rosegarden de nuevo. Si desea utilizar Rosegarden si el secuenciador, ..."
(Por cierto, me da falla el modprobe snd-seq-midi).:mad::mad:
El control de módulos de KDE en "alsa utilities" me da con estatus "not running".
Entrando por Wine, en la configuración, me da error en las pruebas de audio: En "probar sonido" me dice "audio test falled"; y en "panel de control" me dice "Lauching audio control panel not implemented yet".
Al entrar por preferencias de sonido, e intentar e "probar", los mensajes son "falled to connect stream: invalid argument".
Ayuda por favor!!! :guitar:
René

---

### Post by estebandid0 on 2008-07-02
tal vez si vuelves a instalar los codecs y el alsa-mixer

---

### Post by jrg_dnn on 2008-07-14
Hola, 

almejor no se si me repuesta te ayuden en algo, :). Seria bueno que te cambie a ubuntu Studio,fue hecho especialemnete para progfesionales que trabajan con multimedia, ademas tiene el low latency kernel que te permite gravar en real-time, EL probolema que tienes ahora alemojr se debe a los bugs que tiene pulse audio, nose voy a leer un poco aver si enuentro una respuesta pero hasta meintras bajate el ubuntu studio ;)

[http://ubuntustudio.org/downloads](http://ubuntustudio.org/downloads)

---

