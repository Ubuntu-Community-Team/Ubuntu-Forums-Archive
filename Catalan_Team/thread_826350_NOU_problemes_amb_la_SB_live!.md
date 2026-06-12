---
title: "NOU: problemes amb la SB live!"
date: 2008-06-11
forum: Catalan Team
---

### Post by ferreret on 2008-06-11
HOla, acab de migrar a Ubuntu, i tenc problemes amb el so. el SO operatiu em detecta la tarja de so:

product: SB Live! EMU10k1
vendor: Creative Labs
bus info: pci@0000:00:0d.0
version: 0a
width: 32 bits
clock: 33MHz
capabilities:
Power Management,
bus mastering,
PCI capabilities listing
configuration:
driver: EMU10K1_Audigy
latency: 64
maxlatency: 20
mingnt: 2
module: snd_emu10k1


Però seguesc sense tenir so. què puc fer?

Tampoc puc veure els videos del youtube al firefox, i això que el connector està instal·lat.

---

### Post by orestesmas on 2008-06-14
Quan dius que "no tens so", què vols dir exactament?

Amb quins programes ho has provat?
Com tens els controls del mesclador?
Què uses, Gnome, KDE o algun altre excriptori?

Si de cas primer mirem tot això, i després ja seguirem...

---

### Post by CarlesOriol on 2008-06-15
Comprova que no tinguis la sblive + una tageta de so a placa mare i estiguis intentant reproduir el so per l'altra.

Si és així amb gstream-properties pots triar el dispositiu predeterminat en les aplicacions que usen el motor gstream. També pots deshabilitar la targeta de so de la placa base.

---

### Post by ferreret on 2008-06-25
gràcies, no se com m'ho he fet però al final l'he fet funcionar eheheh

---

