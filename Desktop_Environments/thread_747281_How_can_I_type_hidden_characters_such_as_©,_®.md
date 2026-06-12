---
title: "How can I type hidden characters such as ©, ®"
date: 2008-04-06
forum: Desktop Environments
---

### Post by apo00 on 2008-04-06
In Ubuntu, how can I type hidden characters such as  ©, ®, ...?
In Windows I can type those by holding ALT and type the character code in numpad. But it doesn't work in Ubuntu.

---

### Post by Kevbert on 2008-04-06
If you're using Open Office Word Processor, you can use select Insert menu and select special character, a list of characters is displayed (including copywrite and registered).  
Alternatively you can use the old cut and paste method.  Go to Applications-Accessories-Character Map.  To select a character double click on the one you want.  Press the copy button and paste it into whatever you want with either a right click on the mouse and select paste or Ctrl-V as required.

---

### Post by apo00 on 2008-04-06
> **Kevbert said:**
> If you're using Open Office Word Processor, you can use select Insert menu and select special character, a list of characters is displayed (including copywrite and registered).  
Alternatively you can use the old cut and paste method.  Go to Applications-Accessories-Character Map.  To select a character double click on the one you want.  Press the copy button and paste it into whatever you want with either a right click on the mouse and select paste or Ctrl-V as required.
Thanks for reply but you misunderstand me. I mean typing those characters with keyboard only for fast and convenient.
I know both methods you give. When post this thread, I have to open Open Office just to extract the  © characters. It is inconvenient. And using Character Map is the same.
It is strange if Linux/Ubuntu doesn't have a method like Windows. I thought that Linux users prefer using keyboard while Window users prefer using mouse :lolflag:

---

### Post by mcduck on 2008-04-06
Depending on your keyboard layout most of special characters and accented letter can be accessed using the right Alt-key (or Alt Gr, which ever your keyboard layout has.) You can also combne AltGr with Shift to get even more special characters.

Typically, AltGr+R should type ®, and AltGr+C is the combo for ©.

If you can get these to work, check your keyboard layout, and if there's "international" version of the layout available, try that instead. For example the normal US keyboard map doesn't support these, but US International does.

[http://en.wikipedia.org/wiki/AltGr_key#X_Window_System]("http://en.wikipedia.org/wiki/AltGr_key#X_Window_System")

Edit: Alternative way would be to define a compose key in your keyboard settings, and then, for example, compose+o+c will generate ©.

---

### Post by Kevbert on 2008-04-07
Thanks McDuck.  Sorry apo00.

---

### Post by Kevbert on 2008-04-07
I've had a look at the AltGr key combinations and found the following:

According to xorg.conf my keyboard is as follows:
        Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"

Pressing AltGr+key gives the following results (Top left to bottom right)
` |	1 ¹	2 ²	3 ³	4 &#8364;	5 ½	6 ¾	7 {	8 [	9 ]	0 }	- \	= 	bkspc
q @	w &#322;	e e	r ¶	t &#359;	y &#8592;	u &#8595;	i &#8594;	o ø	p þ	[ 	]	
a æ	s ß	d ð	f &#273;	g &#331;	h &#295;	j j	k &#312;	l &#322;	;	'	#
\ |	z «	x »	c ¢	v &#8220;	b &#8221;	n n	m µ	, 	. ·	/

Example pressing AltGr+1 displays ¹

Pressing AltGr+shift+key gives the following (Top left to bottom right)
` |	1 ¡	2 &#8539;	3 £	4 ¼	5 &#8540;	6 &#8541;	7 &#8542;	8 &#8482;	9 ±	0 °	- ¿	= 	bkspc
q &#937;	w &#321;	e E	r ®	t &#358;	y ¥	u &#8593;	i &#305;	o Ø	p Þ	[ 	] 
a Æ	s §	d Ð	f ª	g &#330;	h &#294;	j J	k &	l &#321;	; 	'	#
\ ¦	z <	x >	c ©	v &#8216;	b &#8217;	n N	m º	, ×	. ÷	/

Example pressing AltGr+shift+q displays &#937;.

Some keys don't have any new codes attached such as [ and ].
Sorry for the jumbled up typing (my tabs don't seem to be working)
Hope this is of use.

---

### Post by der_joachim on 2008-04-07
As McDuck already stated, you can define a compose key in your xorg.conf.  It is a nice visual way of character input. *Compose + o + r* gives you an ®. Likewise, é is typed by *Compose + ' + e*.

Configuring a compose key in xorg is quite easy. In this example, I have mapped it to the right alt key.  Open your /etc/X11/xorg file with root priviliges in your favourite text editor, find your keyboard section make sure it looks like the code below. Save and restart X and you should be set. Note that I assume that you use US layout here. 
```

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us(intl)"
	Option		"XkbOptions"	"compose:ralt"
EndSection

```

PS: don't blindly trust me and make sure to make a backup of your xorg.conf first. ;)

---

### Post by apo00 on 2008-04-11
Thank you all for helps.
After I edited my xorf.conf and restarted the X server, the system warned me the X config was different from Gnome config, then I chose my X config.
Those are my keyboard result with Right Alt + O pressed before:
```

` 1 2 3 4 5 6 7 8 9 0 - =
 q &#7832; &#339; ® t &#7833; &#367; i ° p [ ] \
  å § d f g h j k l ; ´
   z ¤ © v b n m , . /
```
I don´t know why it is very different from the layout in wiki: [AltGr_key#X_Window_System]("http://en.wikipedia.org/wiki/AltGr_key#X_Window_System")

And the main problem is **I can´t type the normal quotes (single quote and double quote)  like these: '  and ". In the new layout they become ´ and ¨**
My old xorg.conf:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection
```
My new one:
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us(intl)"
        Option		"XkbOptions"	"compose:ralt"
EndSection
```
Of course the quotes are more important for me than © or ®, so now I go back to my old config and wait your helps.

---

### Post by der_joachim on 2008-04-12
How about using the standard US layout instead of the US international layout? As far as I can see, I can use normal quotes with no problems whatsoever. 

As for the AltGr versus compose key: please note that these are both very different systems. The right alt layout differs per country. The bad ol' dunch layout had a few very obscure typesetting signs and of course the florin sign (for the old currency).  
IMHO, using compose keys  saves you a lot of hassle. You do not need to remember a lot oy obscure alt codes anymore. [This list]("http://www.hermit.org/Linux/ComposeKeys.html") gives all compose key sequences and most of these sequences are pretty self-explanatory. Want the euro sign? Well. it looks like a c with two dashes. Accordingly, you can compose a euro sign (&#8364;)  by Compose + = + C.

---

### Post by apo00 on 2008-04-12
I change to US layout: ```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"compose:ralt"
EndSection
```
and everything works perfect. With compose key I can type all characters in this [[COLOR="Blue"]list[/COLOR]]("http://www.hermit.org/Linux/ComposeKeys.html"). Without compose key I can type without errors (quotes key now works normally)
Thank you again.

---

### Post by MemoryDump on 2008-04-18
> **apo00 said:**
> I change to US layout: ```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"compose:ralt"
EndSection
```
and everything works perfect. With compose key I can type all characters in this [[COLOR="Blue"]list[/COLOR]]("http://www.hermit.org/Linux/ComposeKeys.html"). Without compose key I can type without errors (quotes key now works normally)
Thank you again.

so does this give you the ability to use the right ALT key to enter ALT characters?
like this list: [http://www.tedmontgomery.com/tutorial/ALTchrc.html](http://www.tedmontgomery.com/tutorial/ALTchrc.html)

my wife is freaking out on me cause she can't simply do: right-Alt-Key + 144 for a É

---

### Post by der_joachim on 2008-04-18
> **MemoryDump said:**
> so does this give you the ability to use the right ALT key to enter ALT characters?
like this list: [http://www.tedmontgomery.com/tutorial/ALTchrc.html](http://www.tedmontgomery.com/tutorial/ALTchrc.html)

my wife is freaking out on me cause she can't simply do: right-Alt-Key + 144 for a É

With the settings you quoted, you cannot use the Alt-Num codes. The settings you quoted enable the compose key. An É is typed as Compose+'+E. It takes some getting used to, but the good news is that you do not have to remember those pesky Alt-codes anymore.

You can disable the Compose key by commenting out (that is: putting a # before it) or removing the following line from your xorg.conf:
```

Option		"XkbOptions"	"compose:ralt"

```
You can also remap Compose to say... Right windows key. Replace the line above by the line below:
```

Option		"XkbOptions"	"compose:rwin"

```
That would in theory enable you to both use alt-codes  and the compose key simultaneously. I never bothered learning the alt-Num combination (pesky I tells ya... ;)), so I cannot help your wife any further.

---

### Post by erlyrisa on 2008-04-19
In hardy herron (at the very least - I am unsure about gutsy)

the gnome keyboard configuration options have all this already - no need for special xorg settings

---

