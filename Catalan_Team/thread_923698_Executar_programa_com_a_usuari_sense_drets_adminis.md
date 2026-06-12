---
title: "Executar programa com a usuari sense drets administratius"
date: 2008-09-18
forum: Catalan Team
---

### Post by tanreb20 on 2008-09-18
El titol no és el més adient pero crec que servira..

Necessito saber com fer aque un programa que per executar-lo necessito tenir poders de sueper vaca(root, sudo, gksu) i fer que el usuari normal pugui utilitzar-lo.

Ex:

No se xq el meu Google Earth nomé sem mostra els mapes en cas que fagi:

```
gksu googleearth
```

Hi ha alguna manera de dirli el programa q ja val?

Pero com aquets molts d'altres, x exemple el ndisswrapper, el puc fer anar amb usuari? sense posar la contraseny? com?

---

### Post by RainCT on 2008-09-19
> **tanreb20 said:**
> Necessito saber com fer aque un programa que per executar-lo necessito tenir poders de sueper vaca(root, sudo, gksu)

Això de «super vaca» és un ou de pasqua que tenen l'apt-get i l'aptitude (fes «apt-get moo» per veure'l :P). Tot i que he de reconèixer que la frase té la seva gracia, millor digues «privilegis d'administració» o alguna cosa per l'estil ;).


> No se xq el meu Google Earth nomé sem mostra els mapes en cas que fagi:

```
gksu googleearth
```

Hi ha alguna manera de dirli el programa q ja val?

Això depèn de com hagis insta&#320;lat el programa. Si amb el Google Earth ho has fet manualment (sense agafar un paquet) i et demana permisos d'administració suposo que és perquè no té els permisos adequats; prova a fer-li un "sudo chmod 755 googlearth" a l'executable.

---

### Post by tanreb20 on 2008-09-19
Ueno.... els ous de pasqua ja mel coneixia, era x diro d alguna manera!

---

