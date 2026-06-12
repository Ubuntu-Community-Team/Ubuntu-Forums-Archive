---
title: "[SOLVED] Mantenir data i hora de les fotos en descarregar-les via Ubuntu"
date: 2008-08-13
forum: Catalan Team
---

### Post by xavi on 2008-08-13
Hola a tothom:

Des de fa temps que tinc aquest problema (petit, però engorrós). 

A l'hora de descarregar les fotos de la càmera digital al disc dur des de GNU/Linux (actualment Ubuntu Hardy) es canvia la data i hora de l'arxiu de la càmera (en tarja SD formatada amb FAT 16 des de la pròpia càmera) al del moment de fer la descàrrega al disc dur (sigui a partició ext3 o fat32, que he provat). Copio a ma via Nautilus. 

En canvi, si arrenco l'ordinador amb window$, en descarregar les fotos copiant-les de forma similar (Total Commander, o explorador de window$), al mateix disc fat32 que feia des de GNU/Linux,  els arxius se'm copien amb la data i hora original. Però és un pal haver de reiniciar cada vegada per això, i haver de passar-me a programari propietari per mantenir de forma fàcil les dates i hores originals dels arxius de les fotos.

Alguna pista?

Xavi

P.D: Per si no existeix solució fàcil, porto uns dies barallant-me amb el gthumb i f-spot + algun programa per reanomenar les fotos a partir de la data i hora EXIF (el resultat és molt bó, però voldria evitar cada vegada que copii les fotos a l'ordinador haver de fer tot el ritual de reanomenar-les de nou...). Per reanomenar les fotos amb la informació del dia i hora de la càmara quan les va gravar (data i hora EXIF), **pyRenamer** és sorprenentment bó i eficient (per si algú l'interessa fer l'arreglo semi-manualment).

---

### Post by xavi on 2008-08-15
Bé, més sobre aquest tema, a mesura que vaig esbrinant alguna cosa més. I ho poso aquí per que quan torneu de vacances, si a algú li passa això mateix que a mi, no es trobi igual de mosca i intrigat amb el tema...

Segons he pogut llegir en [un altre fòrum]("http://support.bibblelabs.com/webboard/viewtopic.php?t=10791&sid=0a3db042318878eab3311d0fe807687b"),  sembla que hi ha un bug en Ubuntu Hardy (tot i que jo diria que això em passa des de fa anys amb els ubuntu's) que fa que el Nautilus canvii la data i hora en copiar arxius d'un altre lloc al disc dur, però altres aplicacions com gnome-commander (o la simple consola) no:

> I'm not sure if this helps or is relevant, but there is a bug in Ubuntu 8.04 (Hardy) - or rather an 'issue' because it is actually the default Linux behaviour which was modified on previous releases...

If you use Nautilus to copy a file to or from another drive or partition, the timestamp is altered to the current date/time. This is a nuisance.

The best workaround is to use gnome commander for files transfers (install from synaptic). That preserves the timestamp, as does grsync.

Alternatively you can copy from the terminal using the cp -p switch.

Acabo de tornar a copiar algunes fotos originals de l'última vegada, des de la tarja de la càmera al disc dur amb **gnome-commander** i fantàstic!!!!!
 S'han mantingut la data i hora original!!!!

Oups, i he provat amb el **Krusader** (com el gnome-commander però del KDE i fins i tot una mica més potent) i també. Així que primer problema solucionat.

De totes formes, tenia una altra qüestió que comento també per si algú li passa posteriorment. Resulta que algunes de les fotos que vaig fer dies enrera, han quedat gravades amb l'**EXIF DateTimeOriginal** amb dues hores abans de l'hora real en que van ser preses (el paràmetre **EXIF DateTimeDigitized** sembla mantenir-se correcte).

Vaig jugar amb l'f-spot, gthumb i picasa en un o altre moment amb aquella col·lecció de fotos, així que suposo que ha estat algun d'aquests programes, que ha fet alguna modificació de l'hora EXIF original d'algunes d'elles (no recordo del cert què vaig fer amb quines i amb quines no per que vaig revisar molts centenars de fotos). Però no s'hauria d'haver modificat el paràmetre  EXIF DateTimeOriginal, entenc jo, sinó nomoés la data i hora de l'arxiu, o el parametre DateTime a seques.

Pel que diuen en el [fòrum aquell]("http://support.bibblelabs.com/webboard/viewtopic.php?t=10791&sid=0a3db042318878eab3311d0fe807687b"), l'f-spot de l'ubuntu 8.04 podria tenir algun bug relacionat amb aquest canvi estrany d'aquest paràmetre.

Bé, la qüestió és que pel que he vist, el **PyRenamer** permet fer servir només el paràmetre DateTimeOriginal (que tinc erroni en algunes fotos) però no el DateTimeDigitized (que es manté correcte en totes les meves fotos, pel que sembla). Així que he provat amb el **gnome-commander** (amb el reanomenat múltiple) o el **krusader** (amb el krename enllaçat, en aquest darrer cas), i en ambdós casos, sembla que es pot reanomenar els arxius incloent el paràmetre **EXIF DateTimeDigitized**, així que ja tinc la forma d'arreglar l'estropici d'aquestes fotos modificades també...

Així del gnome-commander ha estat una sorpresa agradable (i al getdeb ja tenen la versió 1.2.7 que incorpora ssh/sftp, etc.). Interessant...

Bé, sento el rotllo, però he pensat que potser altre gent es podria trobar més endavant (o tot just després d'aquest estiu) algun problema similar, i he pensat que les hores que he invertit per esbrinar més sobre el problema i possibles solucions podrien ajudar a altre gent...

Salut, i bones fotos (amb programari lliure ;-)

P.D. Al final vaig emprar per fer les col·leccions de fotos el f-spot (per lo de les etiquetes visuals i fàcils d'exportar després). Ara he llegit en altres llocs que el digikam està molt aconseguit, i pots la propera vegada el provo... i m'acabo decidint per quin programa base emprar per revisar i gestionar àlbums i col·leccions de fotos

---

