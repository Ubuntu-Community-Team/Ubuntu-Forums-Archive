---
title: "Paquet català de texlive inclòs al paquet de castellà [era: Inadmisible]"
date: 2008-01-25
forum: Catalan Team
---

### Post by borgg on 2008-01-25
Salut companys ubuntaires,

Recentement m'he intrduit al món del LaTeX i tal com s'ha suggerit des de la distribució tetex (la qual ja no és mantinguda), m'he instal·lat la distribució de texlive. Per la meva sorpresa he vist que l'idoma català (igual com el gallec, i el castellà de mèxic), estan incloso dins de l'idioma espanyol, en el paquet texlive-lang-spanish.

Quin sentit té això? Perquè a hores d'ara encara no s'ha inclòs el paquet texlive-lang-catalan?

A qui ens hem d'adreçar-hi per canviar aquesta situació?

Deixo aquí algunes referències:

Blog on s'explica la situció (data de l'abril)
[http://orestes.caliu.cat/2007/04/15/tex-i-el-catala/](http://orestes.caliu.cat/2007/04/15/tex-i-el-catala/)

Llista de debian on es discuteix sobre el tema:
[http://orestes.caliu.cat/2007/04/15/tex-i-el-catala/](http://orestes.caliu.cat/2007/04/15/tex-i-el-catala/)

Gràcies per avançat en contestar!

---

### Post by borgg on 2008-01-25
mmm vec que  m'he deixat endur per la ràbia i he ficat un títol bastant poc descriptiu. Algú el podria canviar per un títol com per exemple:
Perquè el paquet català de texlive està inclòs en el paquet de la llengua castellana?

gràcies i disculpeu la meva ignorància!

salut!

---

### Post by orestesmas on 2008-01-26
Hola Borgg,

Benvingut al LaTeX! :-) És increïble com un programari fet fa més de trenta anys segueix avui en dia fent un servei que ja voldrien fer molts "processadors de textos" d'aquests amb tantes finestretes...

Aquesta qüestió que comentes és força enutjosa, i encara no estic segur si l'error ve de upstream (texlive) o de l'empaquetador de debian. Però sospito que és d'aquest últim.

Hi ha un informe d'error enviat per Jordà Polo ([http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=456400](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=456400)), però crec que està mal formulat. Segons ell, si el paquet d'espanyol inclou també el gallec i el català no s'hauria d'anomenar "texlive-lang-spanish" sinó "texlive-lang-spain", però això no té en compte que el català també es parla fora de l'estat espanyol, a andorra, frança i itàlia. Cal crear un paquet "texlive-lang-catalan" i punt.

Conec una gent que s'ho estava mirant, però fa temps que no tinc notícies de com està el tema. Per si de cas, he enviat un informe d'error a Debian. M'assabentaré de la qüestió i procuraré fer-la avançar.

Orestes.

---

### Post by orestesmas on 2008-01-27
Bé, hi ha un [informe d'error anterior]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=456360") on queda clar que l'error prové de *upstream*. Jordà Polo hi està treballant. Cal fer una proposta global sobre com endreçar els paquets d'idioma del (La)TeX a Debian, aleshores la situació es normalitzarà.

---

### Post by borgg on 2008-01-27
Hola Orestes,

M'acabo de llegir els diferents fils del la llista de correu dels bugs de debian i penso exactament com tu. S'ha d'empaquetar seguint el criteri de la llengua i no del país (no li vec gens de sentit en empaquetar segons el país, com ve has dit tu degut a que el català està parlat en 4 estats i tambè idiomes com l'alemany que és parla a més d'un país).

El que no em queda clar és quin tipus de proposta hem de fer, i a qui se l'hi ha d'adreçar?

Salut!

---

### Post by orestesmas on 2008-01-28
> **borgg said:**
> 
El que no em queda clar és quin tipus de proposta hem de fer, i a qui se l'hi ha d'adreçar?


A mi tampoc, de moment. Ja investigaré.

---

### Post by borgg on 2008-01-28
Salut Orestes,

Acabo de rellegir els mails enviats a la llista de bugs de debian, i me n'he adonat que aquest no és un bug de l'empaquetament de debian, sinó aquest bug s'ha de reportar als que mantenen la distribució de latex texlive:

Pel que tambè em sembla entendre, hem d'anar amb una proposta clara i plantejar-la a texlive (tex-live@tug.org).

Per tant jo proposo reportar el bug a texlive de forma consisa:

*Manca el paquet d'idioma específic per la llengua catalana, ja que el criteri usat fins ara és per idiomes i no per estats (veure per exemple llengua alemanya, ja que per exemple, l'alemany no està inclòs al paquet texlive-lang-australia ni al paquet texlive-lang-alemanya sinó que es  troba al paquet texlive-lang-alemanya)*

Aquesta opinió l'extrec després de llegir els comentaris del <Norbert> i del <Frank> a la llista de bugs de debian [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=456360](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=456360).

Què en penseu? Te n'encarregues tu de reportar l'error a tex-live? Ho faig jo sinó? Creus/creieu que és això el que s'ha de fer?

Salut i fins aviat!

---

### Post by orestesmas on 2008-01-28
Penso que **NO** és això el que s'ha de fer. Preciso: no s'ha de fer **només** això. Per si serveix d'aclariment, copio el contingut d'un missatge que m'han enviat els encarregats d'empaquetar el TexLive per Debian, on bàsicament diuen que menys queixar-se i més col·laborar.

> 
It isn't. It's a bug just as lots of others in our packages. But its
importance, compared to the amount of time to fix it properly, makes it
clear that it doesn't make sense to discuss it in the Debian BTS, as
well as that no one among the currently overloaded TeXLive upstream
maintainers will fix it. 

Unless someone comes up with a patch, which doesn't need to be in the
form of code, but must take into account the facts about the TeXlive
distribution (like numbers and sizes of collections). 

So please stop wasting our time. Either come up with a proposal, or stop
whining. 

And please note that the fact that I use the word "whining" has nothing
to do with the bug having a political aspect. I've used similar wording
in the numerous libpaper bugs. Meanwhile we do have a patch, and the
only reason why nobody has implemented it yet are our time
constraints. Like, having to discuss about...

Regards, Frank


Resumint: Cal fer una proposta coherent i seriosa sobre com organitzar els paquets de llengua, però per fer-la cal saber una mica sobre les interioritats del TexLive.

Deixa'm uns dies i podré dir més coses.

---

### Post by borgg on 2008-01-29
Perfecte! Ja diràs el què quan hagis esbrinat una mica del que es tracta, i a veure com et puc ajudar :P

---

