---
title: "Consulta por desarrollo de software Vs. Regulaciones gubernamentales (AFIP)"
date: 2012-10-07
forum: Comunidad
---

### Post by pabloatilio on 2012-10-07
Muchachos, una consulta : 

Primero les hago una pequeña introducción :

Estoy trabajando para una pequeña pyme, con 3 sucursales en la ciudad. 

Tienen un sistema parecido al Tango (pero muy limitado y obsoleto) y con eso facturan, hacen control de stock ,ctas. ctes, etc. Mi trabajo consiste en utilizar los datos que genera el sistema descripto anteriormente, para alimentar de información un sistema secundario que les he desarrollado en PHP, para consultas de todo tipo, análisis de datos, etc. No estoy trabajando en la empresa, solamente les hice hace un tiempo éste sistema auxiliar, que de vez en cuando se le agrega alguna cosita. Entonces, mi pregunta es :

Consulta : 

¿ Si me sale la oportunidad de hacerles algún día un sistema completo que reemplaze el que tienen; migrando a linux y con alguna solución del tipo : postgreSQL ,  JAVA , PHP ,  etc; es decir CERO Microsoft, ¿puedo llegar a tener problemas si vienen los de la AFIP a querer meter controladores fiscales de algún tipo, o que me pidan algún aplicativo que utilice estándares cerrados o privativos, o alguna cosa que no pueda ser resuelta con software libre y mis empleadores me quieran colgar ? ¿ Se me puede llegar a exigir, o ya están exigiendo desde el gobierno algo que me obligue a meter a windows como parte del ecosistema y me impida llevar adelante mi idea ?

Gracias por sus respuestas, saludos.

Pablo

---

### Post by guillermolisi on 2012-10-09
Hay aplicaciones similares a la tenes en mente que son SL y Open Source, caso Libertya, que considera toda la problematica fiscal de varios paises, Argentina y sus controladores fiscales inclusive.

---

### Post by pabloatilio on 2012-10-10
Gracias Guillermo por tu respuesta. Estuve viendo la propuesta que me dejaste. Sin embargo para este caso en particular, lo que me interesa es saber en qué cosas debería fijarme con respecto a las tecnologías que usa o exige la Afip, porque el objetivo central es hacer un desarrollo propio.

Apenas comiezo a ver el tema, así que disculpen la falta de rigurosidad. Aparentemente, una de las cuestiones más conflictivas son los drivers de todos los aparatejos homologados por Afip que para variar, en la mayoría de los casos vienen solamente para windows. Una vez solucionado el tema drivers; para poder interactuar con estos equipos parecería que hay unas clases de Java y unas librerías de C , que a priori serían la única forma de conectarlos en linux: el resto es para visualbasic, foxpro, etc. 

Si no llega información al respecto de parte del resto de los compañeros del foro; en cuanto disponga de tiempo suficiente, hago una investigación completa del asunto y les dejo un informe de los resultados aquí mismo. Gracias. Saludos.

Pablo

---

### Post by guillermolisi on 2012-10-11
Por suerte, en el mundo del FLOSS tenes las cinco libertades del SL con lo cual podes hacer uso de por lo menos una de ellas, estudiar el codigo fuente, y tomar de alli el conocimiento aplicado para tu proyecto.

AFIP no exige formalmente una tecnologia en particular. Podes usar un controlador fiscal que se comunique neumaticamente con la PC y si el resultado final esta dentro de la reglamentacion obligatoria vigente, no les importa como implementaste ese sistema (es mas, ni se enteran de semejante invento porque no les interesa como lo haces sino que resultado obtenes).

---

