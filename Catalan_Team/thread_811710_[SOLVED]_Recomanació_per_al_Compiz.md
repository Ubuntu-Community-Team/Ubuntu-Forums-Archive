---
title: "[SOLVED] Recomanació per al Compiz"
date: 2008-05-29
forum: Catalan Team
---

### Post by LitusMayol on 2008-05-29
Bones familia!

Voldria poder gestionar els efectes de l'escriptori. Instal·lo el **Compiz**? O té alguna contraindicació greu?


En cas de que l'instal·li, instal·lo tots aquests paquets:
```
compiz                         compiz-extra
compiz-bcop                    compiz-fusion-bcop
compiz-compcomm-plugins-main   compiz-fusion-plugins-extra
compizconfig-backend-gconf     compiz-fusion-plugins-main
compizconfig-backend-kconfig   compiz-gnome
compizconfig-settings-manager  compiz-gtk
compiz-core                    compiz-kde
compiz-dev                     compiz-plugins
```

(vaja, el *compiz-kde* no l'instal·laré... xD Em refereixo als altres:lolflag:)


Merci

---

### Post by lluisanunez on 2008-05-29
Què tens? Gutsy? Hardy? Gnome? 
Però, què veus si vas al menú Sistema > Preferències > Efectes d'escriptori?
En teoria ja els hauries de tenir preinsta&#320;lats, almenys amb Gutsy va així. Els paquets que jo tinc insta&#320;lats són:
compiz
compizconfig-settings-manager
compiz-core
compiz-gnome
compiz-fusion-plugins-main
compiz-fusion-plugins-extra
compiz-plugins
I no conec cap contraindicació, excepte que la teva tarja gràfica no tingui acceleració 3D. Ara estic en un portàtil amb cutre-Intel, 512 Mb de RAM i cap problema.

---

### Post by LitusMayol on 2008-05-29
Tinc Hardy!

Aquest paquets són els que tinc (xD perdó no ho havia mira't):
```

compiz                       compiz-fusion-plugins-main
compizconfig-backend-gconf   compiz-gnome
compiz-core                  compiz-plugins
compiz-fusion-plugins-extra  

```

Per tan queden aquests:
```
                        
compiz-bcop                    
compiz-compcomm-plugins-main   
compizconfig-settings-manager 
compiz-dev                    
compiz-gtk
compiz-extra 
compiz-fusion-bcop
```


> **lluisanunez said:**
> Què tens? Gutsy? Hardy? Gnome? 
Però, què veus si vas al menú Sistema > Preferències > Efectes d'escriptori?


Aquest és el problema no veig  "*Efectes d'Escriptori*", però em sembla que és perquè no tinc instal·lat "*compizconfig-settings-manager*". Probo d'instal·lar-lo i a veure què...

---

### Post by LitusMayol on 2008-05-29
En efecte... no sé perquè però no tenia aquest paquet instal·lat. Ja està ara ja tinc la opcio de "Configuració avançada dels efectes d'escriptori",

merci de totes maneres **lluisanunez**!

---

### Post by RainCT on 2008-05-29
> **LitusMayol said:**
> Aquest és el problema no veig  "*Efectes d'Escriptori*"

És: Sistema -> Preferències -> Aparença, i allà hi ha la pestanya «Efectes d'escriptori». Però efectivament el compizconfig-settings-manager va millor.

---

### Post by oriolsbd on 2008-05-29
Carles, no fa gaire que hi ha el nou paquet "simple-ccsm", que està als repositoris d'Ubuntu. També serveix per a configurar el compiz. És molt més senzill d'utilitzar que el "Configuració avançada dels efectes d'escriptori", encara que també té menys opcions. Ho dic per si el vols provar. Si l'instal·les et deixa una nova opció a "Sistema\Preferències", però ara mateix no estic en Ubuntu, de manera que no puc veure com es diu.

Salut!

---

### Post by LitusMayol on 2008-05-30
> **oriolsbd said:**
> Carles, no fa gaire que hi ha el nou paquet "simple-ccsm", que està als repositoris d'Ubuntu. També serveix per a configurar el compiz. És molt més senzill d'utilitzar que el "Configuració avançada dels efectes d'escriptori", encara que també té menys opcions. Ho dic per si el vols provar. Si l'instal·les et deixa una nova opció a "Sistema\Preferències", però ara mateix no estic en Ubuntu, de manera que no puc veure com es diu.

Salut!


Fantàstic!
Tan fàcil com fer "*sudo aptitude install simple-ccsm*" i ja està. A *Sistema*>*Preferències*>*Simple CompizConfig Settings Maneger*.

És molt més simple! Cert. Però a mi em va perfecte! És exactament el que buscava: configuració, simple i ràpida dels efectes més usuals! (no vull posar-me a escriure amb foc, o que plogui al meu ordinador)

Merci **oriosbd**! ;)

---

