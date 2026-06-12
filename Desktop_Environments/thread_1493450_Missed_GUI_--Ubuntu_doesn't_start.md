---
title: "Missed GUI --Ubuntu doesn't start"
date: 2010-05-25
forum: Desktop Environments
---

### Post by DARKEASC on 2010-05-25
Hello, i'm new on Ubuntu, 
Everything was ok, but i installed a game with wine, and it makes crash the pc, so i had to restart it, when restart the GUI had missed, and It loads plymouth but after that stay with black screen two minuts and restart...

I searched for, and i have found a parcial solution...

Start in recovery mode
When it loads use root terminal and type
 ```
sudo dpkg-reconfigure xserver-xorg && sudo /etc/init.d/gdm start 
```
And it works, Ubuntu loads normally, but when i restart the pc it happends again... 

My video card is Nvidia nforce 430

So, there is a definitive solution ???

PD. Sorry for my english xD

---------------------In Spanish---------------------
Lo que traté de decir, si no me hago entender con el inglés, es lo siguiente...
Estaba usando Ubuntu normalmente hasta que instalé un juego con wine, el cual bloqueo el equipo y tuve que reiniciarlo... cuando reinicie no volvio a cargar el entorno grafico, carga el plymouth y luego se queda la pantalla negra y se reinicia...
Buscando encontré una solución parcial, 

Iniciar en recovery mode
usar el terminal y tipear "sudo dpkg-reconfigure xserver-xorg && sudo /etc/init.d/gdm start"
de esta manera inicia normalmente pero al reiniciar vuelve a suceder lo mismo y cada vez que prendo el pc tengo que hacerlo por recovery...

QUE ALGUIEN ME AYUDE!!! / PLEASE HELP!!!

---

