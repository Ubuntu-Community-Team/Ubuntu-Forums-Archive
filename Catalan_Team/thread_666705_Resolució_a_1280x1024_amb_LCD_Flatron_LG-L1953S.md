---
title: "Resolució a 1280x1024 amb LCD Flatron LG-L1953S"
date: 2008-01-13
forum: Catalan Team
---

### Post by Lluís Martí on 2008-01-13
hola a tothom.
fa molt poc m'he instal·lat ubuntu i amb més o menys feina he anat aconseguint que tot em funcioni. el problema és que aquests reis m'han dut una LCD nova que m'està donant molts maldecaps a l'hora de configurar-la. he estat voltant i regirant per internet tot el que he pogut però no sóc capaç de trobar-hi el què; espero que hem pogueu donar un cop de mà!

el meu equip té una targeta gràfica ATI Radeon 7500 i la nova pantalla és una LCD Flatron LG-L1953S. com que amb el monitor antic tenia la configuració en 1024x768 i controlador ATI, la visualització sobre la LCD em sortia deformada: allargada i escapçada per la part inferior de la pantalla.

segons les especificacions del fabricant la resolució màxima permesa és 1280x1024@75, i la recomanada és 1280x1024@60, totes dues amb el controlador VESA. la qüestió és que després de fer els canvis corresponents a l'apartat de 'Preferències de la pantalla i els gràfics' i reobrir la sessió la pantalla queda negra i m'apareix el missatge "SEÑAL FUERA DE RANGO - 46.4 KHz/43 Hz"

entenc que aquests valors queden fora dels definits pel fabricant [Hortiz: 30-83KHz / Vert: 56-75Hz], el que no acabo d'entendre és d'on carai es treu aquests 46.4 KHz/43 Hz. 

he editat els valors del xorg.conf, he fet un dpkg-reconfigure xserver-xorg i res de res. he anat provant diverses combinacions i això del fora de rang em passa sovint; he trobat que si escullo l'opció "LCD Panel 1280x8000" em deixa configurar-ho a 1024x768; de fet, en un altre post d'aquest fòrum [[http://ubuntuforums.org/showthread.php?t=544400]](http://ubuntuforums.org/showthread.php?t=544400]) m'ha semblat entendre que el problema és que el driver VESA té aquesta resolució màxima (és així?). se us acut de quina manera podria aconseguir la màxima resolució del monitor?

en fi, gràcies per la vostra atenció.
espero tingueu pietat d'un ubuntu-passerell com jo!

---

### Post by PauGNU on 2008-01-15
Bones

Pots posar-nos el teu xorg.conf?. Has provat amb el controlador "ati" (en lloc de vesa)?.

Salut

---

### Post by Lluís Martí on 2008-01-15
bona nit, PauGNU
he provat el driver 'ati' i el que em trobo és que la imatge m'apareix allargassada i una part de l'escriptori em queda fora de la pantalla. i el que trobo més curiós de tot plegat és que, malgrat que selecciono una resolució de 1280x1024, obrint el menú de la pantalla (clicant els botons de la pròpia pantalla) m'indica que aquesta està a 1024x768.

el xorg.conf amb el driver 'ati' és el següent:

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"L1953S"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	56-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
	Monitor		"L1953S"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1280x1024" "1200x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

tens alguna idea? gràcies!

---

### Post by PauGNU on 2008-01-15
Fes una cosa. Executa a la consola:
```
sudo dpkg-reconfigure -phigh xserver-xorg 
```

A veure si automàticament t'ho posa bé.

---

### Post by patrickfromspain on 2008-01-16
has probat borrant els valors de HorzSync y VertSync de l'xorg.conf?

---

### Post by Lluís Martí on 2008-01-16
doncs no, ni fent el dpkg-reconfigure ni esborrant les línies corresponents a HorzSync i VertSyn veig que em canvii i res. la veritat és que li estic agafant afecte al xorg.conf i ja passo gairebé més hores amb ell que amb el meu fill (!)

bé, la qüestió és que he seguit remenant i m'he trobat que existeix l'arxiu del log del xorg (Xorg.0.log) i on apareixen moltes línies com aquesta:

(II) RADEON(0): Not using default mode "640x350" (bad mode clock/interlace/doublescan)
[...]
(II) RADEON(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)

donant error per totes les resolucions, des de 640x250 fins a 2048x1536 (tot i que per aquestes, lògicament, l'error que dóna és "height too large for virtual size")

més endavant, també trobo missatges del tipus:

(II) RADEON(0): Not using default mode "1280x1024" (hsync out of range)
(II) RADEON(0): Not using default mode "1280x1024" (vrefresh out of range)

també per totes les resolucions.

no sé si això que us dic ara serveix d'alguna cosa o és més del mateix que ja us explicava abans. en fi, confio que tard o d'hora acabaré aconseguint veure-ho tot bé. 

moltes gràcies per la vostra ajuda

---

### Post by PauGNU on 2008-01-17
Fes una cosa. Redueix l'interval dels refrescos de pantalla.
Posa per exemple:

HorizSync 40-70
VertRefresh 60-70

I prova novament.

---

### Post by jodufi on 2008-01-17
Jo tinc un monitor LG1917S, que no és exactament el mateix però si de la familia, i funciona sense problemes. Normalment havia de configurar l'xorg.conf per a aconseguir la resolució desitjada, però amb Gusty m'ha funcionat perfectament sense tocar res. La principal diferència és que utilitzo nVidia enlloc d'ATI, adjunto la part de l'xorg.conf que et podria interessar:

Section "Device"
	Identifier	"nVidia Corporation NV44A [GeForce 6200]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Monitor genèric"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV44A [GeForce 6200]"
	Monitor		"Monitor genèric"
	Defaultdepth	24
EndSection

---

### Post by Lluís Martí on 2008-01-21
PauGNU: he provat de reduir l'interval dels refrescos tal com em dies, però el resultat continua sent el mateix, sembla com si l'ordinador no en fes gaire cas del que li poso al xorg.conf. d'altra banda, vaig pensar que si m'advertia de 'Senyal fora de rang', potser el que havia de fer era ampliar l'interval en lloc de reduir-lo, però els resultats continuen sent insatisfactoris.

remenant, remenant, he vist que a l'arxiu de log (Xorg.0.log) per tots els modes predefinits m'apareix l'indicador "Not using default mode...", pel que suposo que deu acabar agafant una llista de valors per defecte els que entro dins del xorg.conf, dels quals no sembla no acceptar-ne cap.

ara mateix ho tinc configurat amb el model genèric 'LCD Panel 1280x800' amb una resolució de 1024x768 a 75Hz, i el controlador VESA, que és el recomanat a les especificacions de la pantalla; no entenc doncs per què amb aquest controlador no em funciona per la resolució 1280x1024 que és la recomana el fabricant. He provat d'afegir a sac un ModeLine per 1280x1024 generat amb alguna d'aquestes pàgines que te'l generen on-line, però continuo tenint els mateixos problemes de fora de rang. com pot ser??!¿¿!?

jodufi: gràcies per passar-me el teu xorg.conf, malgrat que suposo que el problema ve més de la tarja gràfica que no pas del monitor; aquests dies voltant pels fòrums ja he vist que això de l'ubuntu+ati és ideal per foguejar novatos. encara que a base de sang, suor i llàgrimes, la veritat és que poc a poc vaig aprenent alguna cosa sobre aquest nou (per mi) món.

bé, ara acabo de trobar la pàgina XorgOnTheEdge ([https://wiki.ubuntu.com/XorgOnTheEdge](https://wiki.ubuntu.com/XorgOnTheEdge)), a veure si tinc sort i trobo alguna cosa que em permeti treure'n l'entrellat.

---

### Post by patrickfromspain on 2008-01-21
No facis servir el controlador vesa... la interfice no esta accelerada de cap manera i tot va molt lent i, encara pitjor, la resolucion maxima que soporta es 1024x768. Has de trobar la solucion fent servir el driver ati.

salut!

---

### Post by papapep on 2008-01-21
Lluís: has provat a configurar la gràfica amb l'[Envy]("http://albertomilone.com/nvidia_scripts1.html")?

---

### Post by CarlesOriol on 2008-01-22
Hi ha versió nova de l'envy d'ahir amb els controladors nous d'ati 8,01

---

### Post by Lluís Martí on 2008-01-23
he estat provant amb envy i m'apareix un missatge indicant que no reconeix la meva tarja amb cap versió del driver i que provi amb la instal·lació manual, però de fet cap de les tres opcions que apareixen (8-01, 8.40.0 i 8.28.8) tampoc la configuren correctament.

pel que he pogut entendre, Envy instal·la els drivers ATI propietaris, i segons sembla ATI no ofereix ja suport per el model de la meva tarja [Radeon 7500].

així que he seguit buscant pel costat dels drivers lliures, i he trobat una pàgina a la wiki d'ubuntu [[https://wiki.ubuntu.com/Bugs/AtiDriver]](https://wiki.ubuntu.com/Bugs/AtiDriver]) sobre els bugs d'aquest driver, però la solució que proposen justament per la Radeon 7500 no em funciona.

l'altra alternativa que proposa, a través de XorgOnTheEdge [[https://wiki.ubuntu.com/XorgOnTheEdge]](https://wiki.ubuntu.com/XorgOnTheEdge]), és instal·lar el nou driver, però vaig fent proves i em perdo encaramés. 

si algun dels 'veteranos' hi podeu donar una ullada i orientar-me una mica us estaré ben agraït. últimament ja somnio en xorgs...

---

### Post by Lluís Martí on 2008-01-27
començo a veure la llum!!

en la meva travessa pel desert avui he descobert la funció xrandr, i sense entendre massa bé que estava fent (suposo que un dia d'aquests tindré un ensurt) de moment he aconseguit configurar (ARA SÍ!!) la meva pantalla a 1280x1024.

després d'aconseguir amb gtf el ModeLine per la resolució i refresc desitjat (gtf 1280 1024 60), he creat un nou mode amb xrandr:

xrandr --newmode Prova 108.88 1280 1360 1496 1712  1024 1025 1028 1060 -HSync +Vsync
xrandr --addmode VGA-0 Prova
xrandr --output VGA-0 --mode Prova

i txa-txan! ho veig tot tal i com jo volia.

el que em trobo ara és que si tanco la sessió i torno a obrir no em queda cap rastre d'aquesta configuració. 

sabeu com podria aconseguir que aquests canvis fossin definitius?
gràcies per la paciència!

---

### Post by unlock24h on 2008-05-06
Hola, he conseguido los 1280x1024@60 modificando esto además de los modos en el xorg.conf:

Section "Monitor"
	Identifier	"Monitor genérico"
	Option		"DPMS"
	HorizSync	30-68
	VertRefresh	56-64
EndSection

con los valores del fabricante (30-83) y (56-75) se me ponía en 1280x1024@75

todo esto con debian y una Intel Q965/Q963 con el driver por defecto
saludos

---

