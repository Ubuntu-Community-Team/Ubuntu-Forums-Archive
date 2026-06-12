---
title: "No llegeix/escriu targetes SD"
date: 2007-12-25
forum: Catalan Team
---

### Post by pserra on 2007-12-25
Hola companys,
primer de tot, BON NADAL,
acabo d'actualitzar a Gutsy, i esperava que amb l'actualització  possiblement el meu lector de targetes SD del meu portàtil és despertaria i a la pràctica ha estat que NO.
La part del comando lspci:

02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
**02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)**

Alguna suggèrencia?
 que he de fer?
- montar, com?  o baixar algun driver?

Merci.

---

### Post by papapep on 2007-12-25
Sembla que, per ara i tant, poca cosa hi pots fer:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/88863](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/88863)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93072](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93072)

O sigui, que és un problema conegut, però que no s'hi ha posat ningú a arreglar-ho. No sembla que sigui, per tant, un problema massa prioritari pels desenvolupadors del kernel.

---

### Post by pserra on 2007-12-26
Merci Papapep,
doncs no hi farem rés.
Gracies per la teva ràpida resposta.
[COLOR="Navy"]**I Bones Festes!!**[/COLOR]

---

