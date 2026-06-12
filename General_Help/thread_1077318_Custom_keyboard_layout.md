---
title: "Custom keyboard layout"
date: 2009-02-22
forum: General Help
---

### Post by Disident on 2009-02-22
Hello!
I'm running Kubuntu 8.04.
I followed the instructions from here:
[http://www.linux.com/feature/113715](http://www.linux.com/feature/113715)
and made myself usefull keyboard layout.
It's shown in System Settings so it seems it can be used, but it doesn't work. It act like standard Croatian keyboard layout (which I modified into mine).

e.g.
i would like that when I press AltGr+E I get "é", and when I press AltGr+Shift+E I get "&#283;", so I add line:
```

    key <AD03> { [    any,    any, 	eacute,		ecaron  ] };

```

whole file:
```

// $XKeyboardConfig: xkeyboard-config/symbols/hr,v 1.17 2007-10-04 21:49:26 svu Exp $
//

default partial alphanumeric_keys
xkb_symbols "basic" {

    name[Group1]="Croatia";

    include "rs(latin)"

    // Redefine these keys to match XFree86 Croatian layout
    key <AE01> { [         1,     exclam,   asciitilde,   dead_tilde ] };
    key <AE03> { [         3, numbersign,  asciicircum, dead_circumflex ] };
    key <AE05> { [         5,    percent,       degree, dead_abovering ] };
    key <AE07> { [         7,      slash,        grave,   dead_grave ] };
    key <AB10> { [     minus, underscore, dead_belowdot, dead_abovedot ] };
};

partial alphanumeric_keys 
xkb_symbols "us" {

    name[Group1]= "Croatia - US keyboard with Croatian letters";

    include "us"

    key <AD01> { [    any,    any,	backslash	        ] };
    key <AD02> { [    any,    any,	bar      	        ] };
    key <AD03> { [    any,    any, 	eacute,		ecaron  ] };
    key <AD04> { [    any,    any,	racute,		rcaron	] };
    key <AD05> { [    any,    any,      tcaron                  ] };
    key <AD06> { [    any,    any,	zacute,       zabovedot ] };
    key <AD07> { [    any,    any,      uacute,         uring   ] };
    key <AD08> { [    any,    any,      iacute                  ] };
    key <AD09> { [    any,    any,      oacute                  ] };
    key <AD11> { [    any,    any, 	scaron,		Scaron  ] };
    key <AD12> { [    any,    any, 	dstroke, 	Dstroke ] };
    key <AC01> { [    any,    any,      aacute,         aogonek ] };
    key <AC02> { [    any,    any,      sacute,         eogonek ] };
    key <AC03> { [    any,    any,      dcaron                  ] };
    key <AC04> { [    any,    any,	bracketleft             ] };
    key <AC05> { [    any,    any,	bracketright            ] };
    key <AC08> { [    any,    any, 	lacute,		lcaron  ] };
    key <AC09> { [    any,    any,	lstroke                 ] };
    key <AC10> { [    any,    any,	ccaron,		Ccaron  ] };
    key <AC11> { [    any,    any, 	cacute,		Cacute  ] };
    key <LSGT> { [    any,    any, 	bar			] };
    key <AB01> { [    any,    any,	nacute		        ] };
    key <AB04> { [    any,    any,	at                      ] };
    key <AB05> { [    any,    any,	braceleft               ] };
    key <AB06> { [    any,    any,	braceright,     ncaron  ] };
    key <AB07> { [    any,    any,	section                 ] };
    key <AB08> { [    any,    any, 	semicolon               ] };
    key <AB09> { [    any,    any, 	colon			] };
    key <AB10> { [    any,    any, 	minus,    underscore  	] };
    key <BKSL> { [    any,    any,	zcaron,	    Zcaron      ] };

    include "level3(ralt_switch)"

};


partial alphanumeric_keys 
xkb_symbols "alternatequotes" {

    name[Group1]= "Croatia - Use guillemets for quotes";

    include "rs(latinalternatequotes)"
};

partial alphanumeric_keys 
xkb_symbols "unicode" {

    name[Group1]= "Croatia - Use Croatian digraphs";

    include "rs(latinunicode)"
};

partial alphanumeric_keys 
xkb_symbols "unicodeus" {

    name[Group1]= "Croatia - US keyboard with Croatian digraphs";

    include "rs(latinunicodeyz)"
};


```

Did I do something wrong? Can anyone help me solve this?

---

### Post by Disident on 2009-02-24
bump

---

