---
title: "gvSIG i Linux Ubuntu"
date: 2008-07-17
forum: Catalan Team
---

### Post by kilian_cuerda on 2008-07-17
Hola companys, vos escric aquest missatge perquè estic tenint problemes amb un programa que necessite molt per a treballar, el gvSIG, a ubuntu. En general tot va bé, però al tractar d'obrir fitxers ECW (ràsters georreferenciats), no els obre i dona aquest missatge d'error: 

Error no detectat per l'usuari java.lang.NullPointerException: null ****com.iver.cit.gvsig.AddLayer.loadFileLayers(Unknown Source) ****com.iver.cit.gvsig.AddLayer.addLayers(Unknown Source) ****com.iver.cit.gvsig.AddLayer.execute(Unknown Source) ****com.iver.andami.plugins.ExtensionDecorator.execute(Unknown Source) ****com.iver.andami.ui.mdiFrame.MDIFrame.actionPerformed(Unknown Source) ****javax.swing.AbstractButton.fireActionPerformed(Unknown Source) ****javax.swing.AbstractButton$Handler.actionPerformed(Unknown Source) ****javax.swing.DefaultButtonModel.fireActionPerformed(Unknown Source) ****javax.swing.DefaultButtonModel.setPressed(Unknown Source) ****javax.swing.plaf.basic.BasicButtonListener.mouseReleased(Unknown Source) ****java.awt.AWTEventMulticaster.mouseReleased(Unknown Source) ****java.awt.AWTEventMulticaster.mouseReleased(Unknown Source) ****java.awt.Component.processMouseEvent(Unknown Source) ****javax.swing.JComponent.processMouseEvent(Unknown Source) ****java.awt.Component.processEvent(Unknown Source) ****java.awt.Container.processEvent(Unknown Source) ****java.awt.Component.dispatchEventImpl(Unknown Source) ****java.awt.Container.dispatchEventImpl(Unknown Source) ****java.awt.Component.dispatchEvent(Unknown Source) ****java.awt.LightweightDispatcher.retargetMouseEvent(Unknown Source) ****java.awt.LightweightDispatcher.processMouseEvent(Unknown Source) ****java.awt.LightweightDispatcher.dispatchEvent(Unknown Source) ****java.awt.Container.dispatchEventImpl(Unknown Source) ****java.awt.Window.dispatchEventImpl(Unknown Source) ****java.awt.Component.dispatchEvent(Unknown Source) ****java.awt.EventQueue.dispatchEvent(Unknown Source) ****com.iver.andami.ui.AndamiEventQueue.dispatchEvent(Unknown Source) ****java.awt.EventDispatchThread.pumpOneEventForHierarchy(Unknown Source) ****java.awt.EventDispatchThread.pumpEventsForHierarchy(Unknown Source) ****java.awt.EventDispatchThread.pumpEvents(Unknown Source) ****java.awt.EventDispatchThread.pumpEvents(Unknown Source) ****java.awt.EventDispatchThread.run(Unknown Source)

Evidentment, pareix un problema de java, i al synaptic he tractat de vore que hi havia que puguera resoldre-ho per si faltava alguna cosa per instal·lar, que podria ser, perquè en el windows xp que tinc a la partició si que obre els ecw, però no sé massa bé qué hauria d'instal·lar. 

He trobat en internet això: 
[http://runas.cap.gva.es/pipermail/gvsig_desarrolladores/2008-February/001714.html](http://runas.cap.gva.es/pipermail/gvsig_desarrolladores/2008-February/001714.html)

però no acabe d'entendre molt bé el que hauria de fer i a més a més, pareix ser que el linux del que es parla és fedora i no ubuntu.

Potser seria més adient penjar això al fòrum d'usuaris de gvSIG, però m'ha paregut interessant penjar-ho ací per, de pas, obrir el tema i en la mesura del possible, l'interés per gvSIG: és una potent ferramenta d'anàlisi geogràfica amb múltiples aplicacions, ja siga geografia, arqueologia (el meu cas), geologia, planificació, urbanisme, etc., i si pegueu una ullada a la web [www.gvsig.gva.es](www.gvsig.gva.es) que és on es pot descarregar, és d'interés l'apartat de les ponències de les últimes jornades que es feren. Ací es pot veure cóm, per exemple, s'està emprant en un projecte de cooperació al desenvolupament a Tanzània, amb un projecte de traducció al swahili inclós, cosa que aniria prou en la línia de la filosofia d'ubuntu. 

Una qüestió de gran interés seria que puguera anar, en les pròximes versions de l'ubuntu, el gvSIG, com ja va al synaptic el GRASS, ferramenta també potent en alguns aspectes, però d'ús més complicat, i en anglés. gvSIG, a banda d'estar produït a casa nostra, pot estar íntegrament en català, a banda de en altres llengües.

Moltes gràcies per anticipat per la vostra ajuda.

---

### Post by papapep on 2008-07-17
Hola Kilian,

Gràcies per la teva explicació sobre el gvSIG. Interessant.

Sobre el teu problema caldria saber el següent:

 - Versió d'Ubuntu instal·lada.
 - Versió de kernel funcionant.
 - Versió de jdk o jre de Java instal·lat, si és del repositori, si és directament de Sun, etc.
 - Versió del gvSIG que estàs fent servir.

 I qualsevol altra cosa que se t'acudeixi que pugui ajudar a centrar el problema i reduir variables ;-)

(no crec que aquí trobis gaires usuaris d'aquest aplicatiu, ja ho tens clar tu mateix, però les mateixes dades et faran falta per a qualsevol altre lloc on efectuïs la consulta).

---

### Post by kilian_cuerda on 2008-07-21
Gràcies, papapep, se m'havien passat eixos detalls:

Ubuntu Hardy Heron 8.04
Kernel 2.6.24-19-generic
Sun Java Runtime Environment 6 (del repositori)
gvSIG 1.1.2

---

