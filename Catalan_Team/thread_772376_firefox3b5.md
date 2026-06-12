---
title: "firefox3b5"
date: 2008-04-28
forum: Catalan Team
---

### Post by MiquelBLL on 2008-04-28
Hola a tots. Tinc el problema que al nou Firefox no s'em veuen alguns videos. Per exemple els de youtube si s'em veuen pero els de tu.tv no. A algu li ha passat hi ho a pogut arreglar? Gracies

---

### Post by CarlesOriol on 2008-04-28
Pot ser que tinguis insta&#320;lat el gnash (lliure) i aquests llocs usin formats encara no suportats.

Comprova-ho amb el synaptic i si és així sempre pots insta&#320;lar al seu lloc el flashplugin-nonfree.

De fet no es mala idea si ets nou de insta&#320;lar el ubuntu-restricted-extras per facilitar-te la transició a canvi de permetre programes sense font i formats (com el mp3 i dvd) que en d'altres països estan subjectos a patents i royalties i per tant estan restringits en la seva distribució i en conseqüencia en els teus drets.

---

### Post by SiscoGarcia on 2008-04-28
D'això que t'explica el Carles
> estan restringits en la seva distribució i en conseqüencia en els teus drets.
 pots trobar molta informació en anglès [ací]("http://www.drm.info/en"). És el que s'anomena DRM.

---

### Post by MiquelBLL on 2008-04-28
A la versio 7.10 em funcionava mes o meins be, entre el firefox i el swiftfox, alguna vegada en penjaen pero forçaba a tanca i ja esta, ara sem penja tot el sistema. Mirare dinstalar aquest pluguin o si no tornar a la versio 2 i tornarbuscar els pluguins. Moltes gracies. Miquel

---

### Post by lo gambusí on 2008-04-28
A mi lo 3b5 se'm penja prou...:?

---

### Post by borgg on 2008-04-28
a mi se'm penja moltíssim i a més el firefox se'm queda penjat durant alguns segons quan carrego pàgines webs. no se a qui se li va ocorrer ficar una beta d'un programa tan usat en una versió lts (long term suport) :S

---

### Post by SiscoGarcia on 2008-04-28
Doncs jo m'he actualitzat avui i he estat fent anar bastant el firefox sense cap problema.

---

### Post by jodufi on 2008-04-29
Doncs m'apunto al club dels que tenen problemes amb el Firefox.
Es queda penjat durant segons, consumeix un 40% de la CPU alguns minuts...
És la gran pega que li trobo al Hardy, a veure si ho solucionen ràpid.

---

### Post by borgg on 2008-04-29
mmm jo seriosament m'estic plantejant d'instal·lar-me la versió 7.10 que no em donava cap problema, o creieu que amb una instal·lació neta del hardy se'm solucionaran els meus problemes de que l'ordinador es va penjant durant alguns segons?

---

### Post by MiquelBLL on 2008-04-29
A mi la versio 7.10 manaba prou be. Ara a part de lo del Ffx3.5b no em funciona ni el VmWare ni el Virtualbox. Per cer voldria desinsta.lar el WmWare pero no se pas com, el WmWare el vaig instal.lar amb  Automatix pero lhe buscat i em sembla que no ha surtit per la nova versio 8.04. Tambe em passa que al obrir una finestra si poso "visualitzart com a icones" sem veu malament i tinc que fer servir visalitsuar com a llista. Suposo sera un petit bug.

---

### Post by oriolsbd on 2008-04-30
Quant al Virtualbox, en els repositoris d'Ubuntu només hi ha el Virtualbox-OSE, que és la versió lliure. La única diferència amb el Virtualbox és que la versió lliure no té suport USB i em sembla que alguna altra petita cosa. Quant al Virtualbox complet, vaig mirar de baixar-me directament el fitxer .deb que hi havia per a Ubuntu 7.10 (Feisty) i no em va funcionar per a Ubuntu 8.04 (per això no deu ser als repositoris). Espero que ho puguin arreglar aviat. De moment, per la majoria de coses que faig, ja em va bé el Virtualbox-OSE.

Salut!

---

### Post by MiquelBLL on 2008-04-30
ok. Si, ja podia jo intentar fer uncionar l USB...
Respecte al FF3b5, ara no se ma penjat+, el que he fet es instal.lar de nou el swiftfox versio 2 que si funcionan els videos de totes les pagines. Pero no puc instal.lar per exemple el DownloadHelper (al firefox 3b5, si) que es un baixador de videos que va molt be i que recomano. 
Ja posats les millores que he vist del 8.04 es per exemple que ja funciona la conexio amb creative Zen, funciona la webcam integrada, i de moment no he tingut el problema de que al obrir varies finestres em sortien en negre (tinc nvidia i turion 64) Miquel Priorat.

---

### Post by rogespierre on 2008-04-30
a mi em passa que de sobte se'm tanca el navegador, ja estigui visitant una cosa o fent-ne una altra... i fot bastant.
Es perquè es tracta d'una beta? A algú li passa?

---

### Post by borgg on 2008-05-01
Salut Roger!

Et tinc clitxat que ho sàpigues ;)

Doncs a mi el firefox i el só em fan una mica el ruc, aquest cap de setmana provaré de fer una instal·lació neta del hardy i si el rendiment del sistema continua sent baix tornaré a la versió anterior (gusty) que m'anava perfecte. Crec que a partir d'ara primaré l'estavilitat del sistema en decriment a les noves característiques encara que és difícil resistir-se.

Ja us contaré si me'n surto, fins aviat!

---

### Post by rogespierre on 2008-05-01
ei borgg! i doncs, com es que em coneixies?? quin misteri! :D

així doncs, se'm tanca x la inestabilitat del SO? però quan el vagin actualitzant s'arreglaran aquests errors o q? pq si es aixi la proxima vegada no m'actualitzaré el SO el primer dia....

---

### Post by pespin on 2008-05-01
Si voleu morir-vos d'un ensurt instal·leu el firefox 3 al KDE4... mai havia vist una cosa tan lletja! xD

---

### Post by borgg on 2008-05-02
Hola Roger, has provat d'instal·lar-te el firefox 2 per substituir el 3 beta 5?

Ho pots fer a travès del gestor de paquets synaptics.

---

### Post by oriolsbd on 2008-05-05
Hola.

A mi em passava el mateix amb els vídeos i les "penjades" del Firefox 3. El tema dels vídeos ja l'he solucionat. És el que comentava el CarlesOriol. Tenia instal·lat el plugin de flash "swfdec-mozilla". Des de Synaptic, he desinstal·lat aquest paquet i he instal·lat el "flashplugin-nonfree". Ara ja se'm veuen bé els vídeos de tu.tv, els mapes de mappy.com (tampoc no em funcionaven), etc.

A més, des de que he canviat el plugin de Flash, ja no se'm penja el Firefox (tot i que això pot ser casualitat o que encara no s'hagi donat la casuística que provocava les penjades).

Salut!

Oriol.

---

### Post by oriolsbd on 2008-05-06
Hola de nou.

He continuat treballant amb el Firefox, i sí que se'm continuen produïnt les penjades de pocs segons que comentàvem.

Salut!

---

### Post by MiquelBLL on 2008-05-06
....... Tenia instal·lat el plugin de flash "swfdec-mozilla". Des de Synaptic, he desinstal·lat aquest paquet i he instal·lat el "flashplugin-nonfree". Ara ja se'm veuen bé els vídeos de tu.tv, els mapes de mappy.com 



Oriol.


Resulta que tenia instal.lat el swfdec-mozilla i tambe el flashplugin-nonfree he deixat nomes el flashplugin-nonfree i ara so que funcionan els videos de tu.tv. Gracies cornudellaweb.com

---

### Post by oriolsbd on 2008-05-09
Hola de nou.

Fa un parell de dies, en una actualització del sistema, vaig veure que es pujava una nova versió del paquet "xulrunner". No sabia per a què servia el paquet, però tinc la mania de mirar què fan les actualitzacions. Hi posava que el "xulrunner" és una part del Gecko, que és el motor sobre el qual treballa el Firefox. Bé, des de llavors ja no se'm queda penjat el Firefox, o sigui que segurament s'arreglaba el bug.

Si fas una actualització d'Ubuntu (si no l'has fet ja) crec que ja no se t'hauria de penjar.

Salut!

---

### Post by LitusMayol on 2008-05-09
Bones!

Jo també tinc un munt de problemes amb el FF3b5.Se'm colapsa moltíssim, especialment quan tinc pàgines com "*Gmail*", "*Last.fm*" o "*YouTube*".

A UbuntuForums ja ho he preguntat i m'ha sortit aigua dels dos colors. Hi ha aquí li va pitjor que a mi i qui no té cap problema. Jo he optat per:

```
sudo aptitude install firefox-2
```

Utilitzo el FF3b5 tot esperant que en alguna d'aquestes actualitzacions que segueixen les noves versions deixi de tenir problemes. I si em canso massa de que se'm torni en blanc i negre... Apa, faig ús del FF2.

Per si li serveix a algú. ;)

---

### Post by jaume69 on 2008-05-11
Per si algú vol instal.lar la extensió de [COLOR="Blue"][COLOR="Black"]**Del.icio.us**[/COLOR][/COLOR] a Firefox 3.0b5,ho pot fer en [[COLOR="Red"]aquesta[/COLOR]]("http://blog.delicious.com/blog/2008/04/firefox-3-delicious-and-you.html") pàg.blog de Del.icio.us.

:popcorn:

---

### Post by lpargemi on 2008-05-12
Hola

> **LitusMayol said:**
> Bones!
```
sudo aptitude install firefox-2
```
Per si li serveix a algú. ;)

A mi el firefox 3 no em deixa recuperar la contrasenya mestra. Em diu que no és bona (què sabrà ell si és bona o no...)

De moment he optat per la versió 2. Això si, no aconsegueixo que els menús surtin en català. (caldrà provar més)

I vinga engegar. I vinga parar. Això em comença a recordar l'etapa amb W$, que ja creia superada. 

No som res

Lluís

---

### Post by papapep on 2008-05-12
> I vinga engegar. I vinga parar. Això em comença a recordar l'etapa amb W$, que ja creia superada. 

Vosaltres ja sou plenament conscients del que significa una "versió Beta"??? Li esteu demanant estabilitat a una versió que ja anuncia que no està en aquesta fase. Per a això teniu la versió 2 que funciona correctament.

---

### Post by Aljullu on 2008-05-12
> **papapep said:**
> Vosaltres ja sou plenament conscients del que significa una "versió Beta"??? Li esteu demanant estabilitat a una versió que ja anuncia que no està en aquesta fase. Per a això teniu la versió 2 que funciona correctament.
El problema és que ve instal·lat per defecte en una LTS, s'han begut l'enteniment!

---

### Post by CarlesOriol on 2008-05-12
> **Aljullu said:**
> El problema és que ve instal·lat per defecte en una LTS, s'han begut l'enteniment!

Estic totalment d'acord amb tu. Una versió beta no es posa predeterminadament en una release i molt menys en una lts.

No feia cap falta i si s'hagués posat com a opcional la majoria l'haguéssim seleccionat però ja sota la nostra responsabilitat.

Per cert. Heu provat d'eliminar (o canviar de nom) la carpeta .mozilla?

---

### Post by LitusMayol on 2008-05-12
> **CarlesOriol said:**
> Estic totalment d'acord amb tu. Una versió beta no es posa predeterminadament en una release i molt menys en una lts.

No feia cap falta i si s'hagués posat com a opcional la majoria l'haguéssim seleccionat però ja sota la nostra responsabilitat.

Per cert. Heu provat d'eliminar (o canviar de nom) la carpeta .mozilla?

Uiii... això no sé què vol dir! Algú em pot explicar que és lo del Long Time S... xD i com influeix? merci..

---

### Post by CarlesOriol on 2008-05-12
[https://wiki.ubuntu.com/JosepS%C3%A0nchez/documentaci%C3%B3/Versions_Ubuntu](https://wiki.ubuntu.com/JosepS%C3%A0nchez/documentaci%C3%B3/Versions_Ubuntu)

---

### Post by LitusMayol on 2008-05-12
> **CarlesOriol said:**
> [https://wiki.ubuntu.com/JosepS%C3%A0nchez/documentaci%C3%B3/Versions_Ubuntu](https://wiki.ubuntu.com/JosepS%C3%A0nchez/documentaci%C3%B3/Versions_Ubuntu)

Merci! XD quina eficiència!

---

### Post by CarlesOriol on 2008-05-12
Eps... he fet uns canvis al wiki del Josep que no estava al dia

---

### Post by papapep on 2008-05-12
Teniu tots plegats molta raó en que una versió estable, i menys una LTS, no era mereixedora de ficar una versió beta de navegador com a l'opció per defecte. Dit això, el meu argument segueix totalment vigent: no podeu demanar el que no se li pot demanar a una versió beta. :-D

---

### Post by Tomàs M. on 2008-05-12
Per si us voleu instal·lar Tab Mix Plus (jo no sé viure sense :-P) i no us fa res que no sigui al lloc oficial de Mozilla (que tampoc és cap garantia absoluta: [http://www.hispasec.com/unaaldia/3484](http://www.hispasec.com/unaaldia/3484) ): [http://tmp.garyr.net/tab_mix_plus-dev-build.xpi](http://tmp.garyr.net/tab_mix_plus-dev-build.xpi)

---

### Post by lpargemi on 2008-05-12
> **papapep said:**
> Vosaltres ja sou plenament conscients del que significa una "versió Beta"??? Li esteu demanant estabilitat a una versió que ja anuncia que no està en aquesta fase. Per a això teniu la versió 2 que funciona correctament.

Tu mateix ho dius més avall: No calia que vingués per defecte en una versió suposadament estable.

Jo no l'hagués triat. No en sé prou com per patir aquestes històries. Ara mateix estic treballant de nou amb la versió 2 [si a més els menús els tornés a poder fer anar en català ja seria la pera]

Salut

Lluís

---

### Post by jaume69 on 2008-05-13
Jo vaig veure a [_Kriptópolis_]("http://www.kriptopolis.org/sal-de-frutas") que deien que **Firefox 3.0b5** cumplia bé els estandars web,que no sigui això,per què l'hagin posat per defecte.
:confused:

---

### Post by RainCT on 2008-05-14
Sí que és veritat que suporta els estàndards molt millor que abans (si ho recordo bé passa l'Acid Test 2), però no és aquest el motiu pel que l'han posat per defecte.

La raó principal (com a mínim de les que han anunciat, que no dic que no hi hagin influït també raons de màrqueting) és que d'aquí a uns mesos el Firefox 2 deixarà de ser suportat per Mozilla, i Ubuntu no és capaç d'ocupar-se per si sol de crear les actualitzacions de seguretat necessàries (o com a mínim no tan ràpidament com seria convenient).

---

### Post by jaume69 on 2008-05-14
Se pillen molt els d´Ubuntu..,podien haver deixat al menys la versió Firefox-2(que ja hi és)però que se li poguessin instal.lar extensions.
Jo no puc.
Pot ser no els hi quevia en el CD Live.¿?

:popcorn:

---

### Post by oriolsbd on 2008-05-15
Hola, Jaume.

En el Firefox2 no li pots instal·lar extensions? Suposo que et refereixes a les que veus a través del Synaptic. Si vas a [http://addons/mozilla.org](http://addons/mozilla.org) hi tens totes les extensions (moltes més que les que hi ha als repositoris) i gairebé totes t'haurien de funcionar amb Firefox2.

Salut!

---

### Post by jaume69 on 2008-05-15
No,no em deixa instal.lar,només puc instal.lar-ne al **Firefox 3.0b5** les que son compatibles.

:guitar:

---

### Post by papapep on 2008-05-15
Què et porta a dir que "no pots instal·lar"?, ensenya'ns què fas i el missatge o acció que et porta a aquesta conclusió.

---

### Post by papapep on 2008-05-15
Què et porta a dir que "no pots instal·lar"?, ensenya'ns què fas i el missatge o acció que et porta a aquesta conclusió.

Per cert, considerant que és un problema del Firefox 2, estaria bé que obrissis un fil específic pel tema.

---

### Post by jaume69 on 2008-05-15
[QUOTE="Papapep"]Què et porta a dir que "no pots instal·lar"?, ensenya'ns què fas i el missatge o acció que et porta a aquesta conclusió.[/QUOTE]
A la consola de Firefox 2 diu:```
Error: oldInstallLocation has no properties
Fitxer font: file:///home/jaume/firefox/components/nsExtensionManager.js
Línia: 3054

No chrome package registered for chrome://button/skin/button.png .
```

[QUOTE="Papapep"]Per cert, considerant que és un problema del Firefox 2, estaria bé que obrissis un fil específic pel tema.[/QUOTE]
Ja ni ha [_un_]("http://ubuntuforums.org/showthread.php?t=771091"),no és exactament el mateix però...(Firefox 2 Web,Firefox 2 Synàptic)

Aquell fil ja es podria posar com a resolt,però no sé si ja es pot. ¿?

:popcorn:

---

### Post by orestesmas on 2008-05-17
Tant VirtualBox com VMware deixen de funcionar quan canvies el nucli (cosa habitual en actualitzar), perquè aquestes aplicacions necessiten usar uns drivers que han de ser compilats contra una versió específica del nucli.

Tanmateix, els paquets .DEB que venen en Ubuntu acostumen a portar els drivers necessaris precompilats per la versió del nucli que toca, i si no és així sempre es pot recompilar:

Per VirtualBox:
```

sudo /etc/init.d/vboxdrv setup

```

Per VMWare:
```

sudo vmware-config.pl

```

Però el VMWare és més punyetero i críptic, a banda que per ser programari privatiu i per altres motius, jo el desaconsello.

---

