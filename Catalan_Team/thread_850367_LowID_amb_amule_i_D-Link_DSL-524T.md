---
title: "LowID amb amule i D-Link DSL-524T"
date: 2008-07-05
forum: Catalan Team
---

### Post by Joanjoc on 2008-07-05
Hola,

Tinc l'ADSL de ya.com i em van proporcionar un router D-Link DSL-524T. Quan configurava els ports de l'emule/amule des de windows i treballava des de windows, cap problema. 

Però quan entro a cal Ubuntu el router perd la configuració dels ports i l'amule em queda amb identificació baixa... Sense ni tan sols entrar a l'administració del router!! Si els torno a configurar des de l'administració del router, em funciona mentre no apago l'ordinador. Quan el torno a engegar amb l'Ubuntu em torna a perdre la configuració del ports :confused: 

Tinc un amic que usa una debian i també té aquest router de ya.com i l'hi passa al mateix... Alguna idea?

---

### Post by CarlesOriol on 2008-07-05
Mira que el UPNP del router estigui desactivat. Això et pot anar molt bé amb programes com el azureus però pot ser que estigui xocant amb alguna cosa.

---

### Post by Joanjoc on 2008-07-05
Ho he mirat i el UPnP no està activat... 

El router està configurat per a proporcionar IP dinàmiques i usa el firmware:  V3.00B01T01.YA-C.20060810

---

### Post by CarlesOriol on 2008-07-05
He cercat informació d'aquest router i no sembla que ningú tingui un problema com el que descrius.

Entenc que parles de que perds la configuració del NAT. oi?
Pots provar amb el "servidor" amb ip fixa fora del rang del dhcp del router que no sigui que al repartir les ips elimini les referències anteriors?

---

### Post by ffp on 2008-07-05
> **Joanjoc said:**
> Ho he mirat i el UPnP no està activat... 

El router està configurat per a proporcionar IP dinàmiques i usa el firmware:  V3.00B01T01.YA-C.20060810

Ull, a veure si al proporcionar IP dinàmiques, la IP del teu PC no coincideix amb la IP que te els ports del amule oberts al router.

Jo tinc el mateix router, i no tinc cap problema amb Ubuntu i amule(id alta )

---

### Post by guillemsola on 2008-07-05
Jo també tinc aquest router i sense problemes. Realment també penso que la ip que tens assignada al finestres no coincideix amb la que deus tenir a l'ubuntu, Confirma-ho. Possiblement a algun dels dos sistemes tens la ip estàtica, de fet si direcciones ports al router els dos sistemes haurien d'estar amb ip estàtica.

Salut!

---

### Post by trinkus on 2008-07-08
Jo tinc un problema semblant amb el 624T. Quan configuro la redireccio de ports tot va be, pero si desconecto el pc o canvio la ip es borra la configuracio de redireccionament. Si mal no recordo aixo tambe em passava temps era temps amb el el sistema innomenable...

---

### Post by patrickfromspain on 2008-07-08
es borra la configuracio de ports del ruter? o simplement ja no concorda amb la teva IP?.

Les coses clares: s'obre un determinat rang de ports per a una IP concreta. Si canvia la IP, ja no aplica aquell rang de ports. Jo tinc claus de casa, pero si intento obrir la porta del vei, no puc.

salut!

---

### Post by trinkus on 2008-07-09
No, la IP del pc sempre es la mateixa perque li tinc fixada pr aquell pc. El que passa que si tu el tanques aleshores no guarda la configuracio del PortForwarding. Resultat: quan el tornes a engegar l'has de tornar a configurar els ports. Funciona pero es una mica pesat... encara que se supsa que si tens l'Amule es que tens l'ordinador engegat força estona (o dies) perque sino no te gaire sentit...

---

### Post by Brunilda on 2008-07-09
Segur que ja ho has consultat, però a la pàgina de [adslzone]("http://www.adslzone.net/d-link524t.html") trobaràs força informació per configurar el router i per obrir els ports. Hi pots trobar un forum més adient al teu problema (també n'hi ha específics per a linux). A mi em va anar força bé i no tinc cap mena de problema ni al parar l'ordinador ni el router, és més, tinc un parell de routers i fer el canvi de l'un a l'altre sense que es desconfiguri res de res.

---

