---
title: "Vinagre, Vino e o depósito de claves na beta de Lucid Linx"
date: 2010-04-14
forum: Galician LoCo Team
---

### Post by leillo1975 on 2010-04-14
Hola

En primeiro lugar saudar a todos pois é a primeira vez que posteo neste subforo. Non sabía nin que existía.

Comentovos un problema que teño que non sei si é un bug ou que é así. No primeiro lugar comentar que ca 9.10 non me pasaba.

O caso é que teño instalada a última beta de Lucid actualizada o dia de hoxe en varios equipos. O equipo no que estou normalmente usoó para conectarme via VNC con Vinagre o resto de equipos.

Os equipos servidores de Vino (que mal sona) teñoos como equipos de consulta e tratase de 3 equipos modestos iguais que se usan para ofimatica e internet.

Cando me conecto dende o meu equipo con Vinagre non consigo ve-lo escritorio remoto, e o ir a este me atopome cunha fiestra que me sinala que debo por o contrasinal de sesión para poder continuar. Unha vez feito isto podo ver iste equipo dende o meu ordenador sin problemas.

Os 3 equipos modestos teñen autologin, po-lo que arrancan e chegan directamente o escritorio sin ter que mete-lo contrasinal no logon.

¿Existe alguna forma de evitar que salga este mensaje?


EDITO

Atopei a solucion (copiado de "[me olvido de todo]("http://meolvidotodo.com.ar/2009/07/evitar-que-te-pregunta-cada-vez-la.html")")

Para que te pregunte cada vez que ingreses la clave del keyring en Ubuntu 9.04
Le quita seguridad, pero prefiero que sea mas practico; sino cada vez que inicio ubuntu el network manager me pregunta la clave para iniciar el wireless... muy molesto.

1. Ir a Aplicaciones/Accesorios/Contraseñas y claves de cifrado
2. Una vez abierto “Contraseñas y claves de cifrado” da clic en la pestaña Contraseñas
3. Selecciona “default” y da clic con el botón derecho del ratón, en el menú contextual selecciona Cambiar la contraseña
4. Te saldrá la ventana “Cambiar la contraseña del depósito”, en la cual debes introducir tu Contraseña antigua, y deja en blanco los campos de Contraseña y Confirmar contraseña, clic en Cambiar
5. Te saldrá la advertencia “¿Almacenar sus contraseñas sin cifrarlas?”, da clic en Usar depósito inseguro
6. Ahora puedes cerrar “Contraseñas y claves de cifrado” y una vez reinicies el equipo no te pedirá de nuevo la contraseña

---

### Post by pikamoku on 2010-04-14
pois ben vido a este curruncho ;D

e gracias por compartir a solución ó teu problema

---

