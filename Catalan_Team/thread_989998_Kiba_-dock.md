---
title: "Kiba -dock"
date: 2008-11-22
forum: Catalan Team
---

### Post by lFossil on 2008-11-22
Hola!

He estat buscant per a instal·lar el kiba-dock en l'intrepid ibex i he trobat [aquest blog]("http://wawan-kurniawan.web.id/install-kiba-dock-in-intrepid-ibex/") però a partir del tercer pas no entenc les ordres que dóna, ho dic per si algú sap a què es refereix si em pot ajudar, moltes gràcies per endavant!

---

### Post by sambita on 2008-11-22
I'm not sure what language is that which youre using, i was able to understand it because its very similar to spanish(maybe some italian or french in there too? i dunno).

Im going to post in english, but if you dont understand just let me know and i will post in spanish, if you dont understand spanish then im sorry, but theres nothing i can do. 

Este post está en inglés, pero si no entendés inglés avisame que lo vuelvo a postear en español. Si tampoco sabes español entonces no puedo hacer nada jeje.

If someone sees a mistake here please correct it, as i am no expert and may very well make mistakes.

3. three

    mkdir kiba-dock [COLOR="Red"]- this creates a directory(folder) named kiba-dock[/COLOR]

then

    cd kiba-dock [COLOR="Red"] youre entering the directory[/COLOR]

4. four

[COLOR="Red"]with the svn co command you checkout a version of kiba-dock from the subversion server (maybe someone can explain more about this).[/COLOR]

    svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/) akamaru

then

    svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/) kiba-dock

then

    svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/) kiba-plugins

then

    svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/) kiba-dbus-plugins

5. time to show off :D (Type per line @ once)

    cd akamaru/ [COLOR="Red"]As said before, cd opens a directory[/COLOR]

then

    ./autogen.sh &#8211;prefix=/usr &#8211;exec-prefix=/usr [COLOR="Red"]Executing the autogen shell script located in akamaru directory[/COLOR]

then

    sudo make install [COLOR="Red"] make install will install the binaries and any supporting files into the appropriate locations[/COLOR]

then

    cd ..

then

    cd kiba-dock/

then

    ./autogen.sh [COLOR="Red"]same as with last autogen, explained before, same goes for the make install command[/COLOR]

then

    sudo make install 

then

    cd ..

then

    cd kiba-plugins/

then

    ./autogen.sh

then

    sudo make install 

then

    cd ..

then

    cd kiba-dbus-plugins/

then

    ./autogen.sh

then

    sudo make install

then

    cd ..

6. if all good then type
 
    kiba-dock [COLOR="Red"]this will run kiba-dock[/COLOR]

7. to make autostart, go to System > Preference > Session then Add Name Kiba-Dock and command kiba-dock then save.

[COLOR="Red"]step seven is pretty much self explanatory, if you want it to start automatically when you boot your computer then follow those steps.[/COLOR]

How about uninstall it :D don&#8217;t worry now time for uninstall :

    cd kiba-dock/kiba-dbus-plugins

then

    sudo make uninstall [COLOR="Red"]here you uninstall what you had previously installed on kiba-dock/kiba-dbus-plugins directory. same goes for all the following commands.[/COLOR]

then

    cd ..

then

    cd kiba-dock/kiba-plugins

then

    sudo make uninstall

then

    cd ..

then

    cd kiba-dock/kiba-dock

then

    sudo make uninstall

then

    cd ..

then

    cd kiba-dock/akamaru

then

    sudo make uninstall

DONE.

[COLOR="Red"]Hope it helped!.[/COLOR]

---

### Post by lFossil on 2008-11-22
Well, this language is Catalan own of Catalonia, a comunity of Spain. His capital is Barcelona, you probably know about this city.

I can understand the post but i don't understand some commands like the 4.
What I have to do in this delivery? 
I'm not very good at english but I think that you will understand me.
Thank you!

---

### Post by sambita on 2008-11-22
> **lFossil said:**
> 
What I have to do in this delivery? 

Im not sure what you mean by this. 

About the commands in step 4...

in english:

[http://en.wikipedia.org/wiki/Subversion_(software)]("http://en.wikipedia.org/wiki/Subversion_(software)")

[http://en.wikipedia.org/wiki/Version_control]("http://en.wikipedia.org/wiki/Version_control")

in spanish:

[http://es.wikipedia.org/wiki/Subversion]("http://es.wikipedia.org/wiki/Subversion")

[http://es.wikipedia.org/wiki/Control_de_versiones]("http://es.wikipedia.org/wiki/Control_de_versiones")


As i understand it, what youre doing with the svn co(checkout) command is to obtain one of the version in the repositories

---

### Post by papapep on 2008-11-22
Si us plau, per fils en altres idiomes aneu als altres fòrums. Aquí només en català.
Please, to maintain conversations in other languages than catalan you've got to do it in other ubuntu forums, not in these. Here just in catalan.

---

### Post by lFossil on 2008-11-22
Jo ho havia posat en català!

Si alguna persona catalano parlant em pot ajudar...

---

### Post by papapep on 2008-11-22
El tercer pas de l'enllaç que has posat és una simple creació d'un directori. T'aconsello llegir documentació sobre ordres de terminal abans de ficar-te en temes com aquest, sinó t'ofegaràs a cada pas...t'ho dic com a consell, sense cap mena de mal rotllo :-)

Un bon lloc per començar és [aquest]("https://wiki.ubuntu.com/CatalanTeam/Recursos/Int%C3%A8rpretComandes"). Et garantitzo que el seu estudi serà una gran inversió, en cap cas una pèrdua de temps.

---

### Post by oriolsbd on 2008-11-22
Hola, jo vaig provar el Kiba-dock, i com a curiositat està bé, però el vaig trobar una mica "marejant" per a l'ús habitual.

Si el vols instal·lar, endavant, però et recomano que provis l'Avant Window Navigator (awn). A mi m'agrada molt. Una altra opció molt bona és el Cairo-Dock (és el preferit d'altres companys d'aquest fòrum).

Qualsevol dels dos et seran més fàcils d'instal·lar que el Kiba-dock.

---

### Post by lFossil on 2008-11-23
Gràcies per la recomanació, he seguit el teu consell i he instal·lat el AWN, l'he instal·lat en un no-res [d'aquest enllaç]("http://tuxazteca.wordpress.com/2008/10/30/instalar-la-ultima-version-de-awn-avant-window-navigator-en-ubuntu-810-intrepid-ibex/"). Moltes gràcies!

---

### Post by open-pitu on 2008-11-25
Personalment sóc un fanàtic dels dock, és una eina que em va molt bé i la trobo molt útil i pràctica. Fa temps, quan encara no anàvem amb accelaració gràfica 3d corria gDesklets i ja hi havia una primera aproximació més enllà d'un menú estatic una mica més ample i centrat.

Amb l'aparació de compiz va aparéixer Kiba-Dock i va tenir un boom però per a mi va quedar lluny de les espectatives que havia generat. Tenia moltes opcions configurables però no era útil per l'usuari (és una opinió personal d'una persona que des de fa 4 o 5 anys que funciono amb Linux).

A continuació vaig conéixer Avant Window Navigator. En el primer moment el vaig trobar espectacular, amb moltes opcions, i encara més importants que la quantitat, la majoria d'elles útils. Temes diferents i personalitzables... Un bon programa.

De fa uns 2 mesos o així però que ja no vaig amb AWN. He fet una nova descoberta, el Cairo Dock. Per a mi la millor alternativa actual a la barra de mac per Linux. Té molts de temes, tot funciona (AWN té bastantes coses no desenvolupades) va ràpid i és molt còmode. A sobre tens temes molt atractius de sèrie. Qui no el conegui que l'instal·li i el provi, va molt bé.

Aquí us deixo un how-to de com instal·lar-lo:
[http://open-pitu.webcindario.com/open/index.php?di=75](http://open-pitu.webcindario.com/open/index.php?di=75)

Si sabeu docks que valguin la pena comenteu-ho que els provarem!

---

### Post by lFossil on 2008-11-28
Sí, jo ja el tenia el cairo-dock al 8.04, abans que tingués que reinstal·lar de nou, és el més similar al del Mac OsX i va molt bé, però volia canviar i de moment l'AWN magrada molt.
L'he volgut canviar perquè tenia un problema amb el compiz, i cada volta que engegava l'ordinador tenia que iniciar el compiz per a que funcionés i deprés el compiz, això era molt engorrós cada volta la veritat, però de moment em rutlla molt bé!

---

