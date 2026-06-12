---
title: "[SOLVED] Problemas de sonido con Ubuntu 7.10 (Gutsy Gibbon)"
date: 2008-05-25
forum: Centroamerica Team
---

### Post by eivar on 2008-05-25
Hola a todos, bueno escribo para comentar el problema que he tenido con Ubuntu y el sonido.

Es una instalación "LIMPIA", ya no tanto porque como hace rato lo instalé tiene varios programas adicionales.

Hace un tiempo que notaba que en ocasiones me quedaba sin sonido y tenía que reiniciar, buscando por foros encontré algunas soluciones pero la de mejor resultados fue la del siguiente enlace: [COLOR=Sienna][http://ubuntuforums.org/showthread.php?t=575653](http://ubuntuforums.org/showthread.php?t=575653) [/COLOR]donde, en el post #4, [Razzoo]("http://ubuntuforums.org/member.php?u=163180") da algunos comandos para reinstalar los drivers alsa, eso solucionó el problema de que el sonido se "perdía" de pronto [COLOR=Sienna]¡ya no tengo que reiniciar![/COLOR]

Ahora bien yo uso **Amarok** y **SMPlayer** para música y vídeos respectivamente pero noté que el SMPlayer y el propio MPlayer (que estaban configurados para usar alsa) no tenían sonido al igual que **Rithmbox** (reproductor incluido en Ubuntu) después de mucho intentar la solución para mi caso es instalar esound y xine.

```
sudo aptitude install amarok-xine 
``````
sudo aptitude install esound 
```Usando Xine como motor para Amarok y esd para el sonido en SMPlayer.

Saludos y espero sea de ayuda para alguien

---

