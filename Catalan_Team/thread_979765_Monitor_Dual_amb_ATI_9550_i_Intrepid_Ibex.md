---
title: "Monitor Dual amb ATI 9550 i Intrepid Ibex"
date: 2008-11-12
forum: Catalan Team
---

### Post by kukat on 2008-11-12
He estat buscant i buscant, i he vist moltísimes coses, però no hi ha forma de fer anar els dos monitors com si fos un.

Tinc l'Intrepid Ibex (meravellós! jejej) i els drivers de l'ATI Sapphire 9550 (256MB) (fglrx) amb el Catalyst Control Center a Aplicacions (on suposadament es deuria de configurar el monitor dual) però no hi ha manera.

El meu xorg.conf es aquest:

#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"fglrx"
EndSection

I si, li falten moltes coses, diria jo (per a configurar). Però em fa por tocar res del xorg per si espatlle el sistema gràfic (que va de meravella amb el Compiz-Fusion). 

El monitor per defecte es TFT i l'altre es CRT. 

Alguna suggerència??? 

PD: he fet alguna cosa com: sudo aticonfig --initial=dual-head --screen-layout=above, sense resultats. Però la veritat es que vaig un poc perdut!:confused:

Si algú té alguna possible solució o alguna indicació per configurar el xorg, moltíssimes gràcies!!!!!!!!!

---

