---
title: "Problema con monitores multiples en Ubuntu 18.04"
date: 2018-10-04
forum: Centroamerica Team
---

### Post by benjirub on 2018-10-04
Buenas a todos, antes de nada os pongo en contexto. Mi equipo es un portátil HP 6735, procesador Intel Core2Duo, gráficos intel. 
Llevo cierto tiempo utilizando sin problema el propio  monitor del portátil y uno externo bajo Ubuntu 16.04. Me es de mucha  utilidad ya que una de las cosas principales que hago en mi equipo es  realizar algunas gestiones de contabilidad de mi empresa y me viene muy  bien poder ver en un lado el correo electrónico -muchas facturas se  reciben a través de él- y en el otro monitor tener el programa de  contabilidad y así no tener que estar saltando de ventana contínuamente,  es mucho más fluido.  
El problema se ha presentado cuando formateé  recientemente el equipo e instalé Ubuntu 18.04, desde entonces me es  imposible utilizar los dos monitores, o bien uso el externo, o bien uso  el del portátil, pero si intento extender a los dos monitores, en el  momento que aplico la cofiguración -o ahora mismo, en el momento en el  que conecto el monitor externo- se quedan ambos monitores en negro y  solo se ve el cursor. Además el externo parpadea, es como si fuera a  mostrar imagen pero se vuelve a quedar negro, solo se aprecia un cambio  en la retroiluminación.... Si en ese momento desconecto el monitor  externo, en ocasiones vuelve la imagen al monitor integrado, pero la  mayoría debo cerrar el portátil para que se cierre sesion y al abrir la  tapa vuelve a funcionar. 
He probado a actualizar cualquier cosa referente a los  gráficos intel y también cambié el servidor gráfico wayland por xorg  editando "/etc/gdm3/custom.conf" por si el problema viniera de ahí pero  no ha habido suerte. La verdad es que no se que hacer, en 16.04 nunca he  tenido problemas, no se si es un problema de gnome, si es un problema  de gestion de la gráfica o qué puede estar pasando...

---

### Post by benjirub on 2018-10-04
He probado a actualizar gnome y volver a wayland pero sigo exactamente igual... pantalla integrada en negro, solo con el raton y pantalla secundaria encendiéndose y apagandose sin llegar a mostrar imagen ni extendiéndose el escritorio, ya que la flecha del ratón no llega a desaparecer al intentar llevarla al otro monitor, se queda en el principal

---

### Post by WHK on 2019-01-18
Hola, lo mas probable es que ya no exista soporte para tu hardware porque ya es obsoleto, no se me ocurre otra respuesta ya que Ubuntu es característico por estar siempre al día en temas de compatibilidad con hardware nuevo y el uso de controladores privativos. En mi caso tengo un desktop con una nvidia 1060gt y el driver libre funciona muy bien, los juegos corren muy fluidos, en el desktop de mi trabajo tengo la misma tarjeta gráfica, uso drivers privativos y tengo 3 monitores y todo anda muy bien, también tengo un macbook air y usa ubuntu y no fue necesario instalar ningún driver adicional y todo anda muy bien. Has probado cambiar del driver libre al privativo o al reves? que aparece en la pantalla de drivers en el gestor de paquetes?

---

