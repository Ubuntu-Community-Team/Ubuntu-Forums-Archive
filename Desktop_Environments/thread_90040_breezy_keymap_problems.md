---
title: "breezy keymap problems"
date: 2005-11-14
forum: Desktop Environments
---

### Post by BROKEN_LADDER on 2005-11-14
what the heck did breezy do with the keymaps system?

i use a dvorak keymap with customizations to type esperanto characters.  this always worked fine in xmodmap, but when i first started usinga distro where xorg started using xkb instead, i had to make a new customized map.  this worked fine in hoary, where i edited /etc/X11/xkb/keymap/us/dvorak (as i recall).  here's an excerpt to show you what i did to add the circumflexes to various characters.

> 
    key <AE09> { [          9,  parenleft,  dead_grave] };
    key <AE10> { [          0,  parenright      ]       };
    key <AE11> { [ bracketleft, braceleft       ]       };
    key <AE12> { [ bracketright, braceright,  dead_tilde] };

    key <AD01> { [  apostrophe, quotedbl, dead_acute, dead_diaeresis    ] };
    key <AD02> { [      comma,  less,   dead_cedilla, dead_caron        ] };
    key <AD03> { [      period, greater, dead_abovedot, periodcentered  ] };
    key <AD04> { [          p,  P               ]       };
    key <AD05> { [          y,  Y, yen          ]       };
    key <AD06> { [          f,  F               ]       };
    key <AD07> { [          g,  G, gcircumflex, Gcircumflex ]   };
    key <AD08> { [          c,  C, ccircumflex, Ccircumflex ]   };
    key <AD09> { [          r,  R, registered, copyright]       };
    key <AD10> { [          l,  L               ]       };
    key <AD11> { [      slash,  question        ]       };


now in breezy, i don't even see the path to this file anymore.  all the keymaps i find are at /usr/share/keymaps/i386/

what's even weirder, is they are all .gz files.  when i read them, they look like xmodmap files.

is breezy using xmodmap or xkb?  what the heck is going on here?  someone please help.

thanks!!

---

### Post by BROKEN_LADDER on 2005-11-14
i finally got this one figured out!  no fun though.

it turns out, all the xkb keymap files are now in /etc/X11/xkb/symbols/

in my case, the dvorak keymap i use is a variant of the standard us keymap, so i edited /etc/X11/xkb/symbols/us as listed in quote below.

this allowed me to add all kinds of neat characters like these (notice the esperanto characters!):

&#198; &#214; &#201; &#162; &#8364; &#209; &#174; &#169; &#165; &#308; &#292; &#364; &#348; &#284; &#264;

a complete list of the "codes" to add the different accents is here: [http://wiki.linuxquestions.org/wiki/List_of_keysyms](http://wiki.linuxquestions.org/wiki/List_of_keysyms)

> 
// $XKeyboardConfig: xkbdesc/symbols/us,v 1.15 2005/08/06 22:13:18 svu Exp $

//
// $XdotOrg: xc/programs/xkbcomp/symbols/us,v 1.1.4.3 2004/03/05 13:41:33 eich Exp $
// $XFree86: xc/programs/xkbcomp/symbols/us,v 1.6 2003/10/31 14:32:05 pascal Exp $

default
partial alphanumeric_keys modifier_keys
xkb_symbols "basic" {

   name[Group1]= "U.S. English";

   include "pc(common)"

   // Alphanumeric section
   key <TLDE> {        [     grave,    asciitilde      ]       };
   key <AE01> {        [         1,    exclam          ]       };
   key <AE02> {        [         2,    at              ]       };
   key <AE03> {        [         3,    numbersign      ]       };
   key <AE04> {        [         4,    dollar          ]       };
   key <AE05> {        [         5,    percent         ]       };
   key <AE06> {        [         6,    asciicircum     ]       };
   key <AE07> {        [         7,    ampersand       ]       };
   key <AE08> {        [         8,    asterisk        ]       };
   key <AE09> {        [         9,    parenleft       ]       };
   key <AE10> {        [         0,    parenright      ]       };
   key <AE11> {        [     minus,    underscore      ]       };
   key <AE12> {        [     equal,    plus            ]       };

   key <AD01> {        [         q,    Q               ]       };
   key <AD02> {        [         w,    W               ]       };
   key <AD03> {        [         e,    E               ]       };
   key <AD04> {        [         r,    R               ]       };
   key <AD05> {        [         t,    T               ]       };
   key <AD06> {        [         y,    Y               ]       };
   key <AD07> {        [         u,    U               ]       };
   key <AD08> {        [         i,    I               ]       };
   key <AD09> {        [         o,    O               ]       };
   key <AD10> {        [         p,    P               ]       };
   key <AD11> {        [ bracketleft,  braceleft       ]       };
   key <AD12> {        [ bracketright, braceright      ]       };

   key <AC01> {        [         a,    A               ]       };
   key <AC02> {        [         s,    S               ]       };
   key <AC03> {        [         d,    D               ]       };
   key <AC04> {        [         f,    F               ]       };
   key <AC05> {        [         g,    G               ]       };
   key <AC06> {        [         h,    H               ]       };
   key <AC07> {        [         j,    J               ]       };
   key <AC08> {        [         k,    K               ]       };
   key <AC09> {        [         l,    L               ]       };
   key <AC10> {        [ semicolon,    colon           ]       };
   key <AC11> {        [ apostrophe,   quotedbl        ]       };

   key <AB01> {        [         z,    Z               ]       };
   key <AB02> {        [         x,    X               ]       };
   key <AB03> {        [         c,    C               ]       };
   key <AB04> {        [         v,    V               ]       };
   key <AB05> {        [         b,    B               ]       };
   key <AB06> {        [         n,    N               ]       };
   key <AB07> {        [         m,    M               ]       };
   key <AB08> {        [     comma,    less            ]       };
   key <AB09> {        [    period,    greater         ]       };
   key <AB10> {        [     slash,    question        ]       };

   key <BKSL> {        [ backslash,         bar        ]       };
   // End alphanumeric section
};


partial alphanumeric_keys
xkb_symbols "intl" {

   name[Group1]= "U.S. English - International (with dead keys)";

   include "us(basic)"

   // Alphanumeric section
   key <TLDE> { [dead_grave, dead_tilde,         grave,       asciitilde ] };
   key <AE01> { [         1,     exclam,    exclamdown,      onesuperior ] };
   key <AE02> { [         2,         at,   twosuperior, dead_doubleacute ] };
   key <AE03> { [         3, numbersign, threesuperior,      dead_macron ] };
   key <AE04> { [         4,     dollar,      currency,         sterling ] };
   key <AE05> { [         5,    percent,      EuroSign                   ] };
   key <AE06> { [    6, dead_circumflex,    onequarter,      asciicircum ] };
   key <AE07> { [         7,  ampersand,       onehalf,        dead_horn ] };
   key <AE08> { [         8,   asterisk, threequarters,      dead_ogonek ] };
   key <AE09> { [         9,  parenleft, leftsinglequotemark, dead_breve ] };
   key <AE10> { [         0, parenright, rightsinglequotemark, dead_abovering ] };
   key <AE11> { [     minus, underscore,           yen,    dead_belowdot ] };
   key <AE12> { [     equal,       plus,      multiply,         division ] };

   key <AD01> { [         q,          Q,    adiaeresis,       Adiaeresis ] };
   key <AD02> { [         w,          W,         aring,            Aring ] };
   key <AD03> { [         e,          E,        eacute,           Eacute ] };
   key <AD04> { [         r,          R,    registered,       registered ] };
   key <AD05> { [         t,          T,         thorn,            THORN ] };
   key <AD06> { [         y,          Y,    udiaeresis,       Udiaeresis ] };
   key <AD07> { [         u,          U,        uacute,           Uacute ] };
   key <AD08> { [         i,          I,        iacute,           Iacute ] };
   key <AD09> { [         o,          O,        oacute,           Oacute ] };
   key <AD10> { [         p,          P,    odiaeresis,       Odiaeresis ] };
   key <AD11> { [ bracketleft,  braceleft,  guillemotleft, guillemotleft ] };
   key <AD12> { [bracketright, braceright, guillemotright,guillemotright ] };

   key <AC01> { [         a,          A,        aacute,           Aacute ] };
   key <AC02> { [         s,          S,        ssharp,          section ] };
   key <AC03> { [         d,          D,           eth,              ETH ] };

   key <AC09> { [         l,          L,        oslash,         Ooblique ] };
   key <AC10> { [ semicolon,      colon,     paragraph,           degree ] };
   key <AC11> { [dead_acute, dead_diaeresis, apostrophe,        quotedbl ] };

   key <AB01> { [         z,          Z,            ae,               AE ] };
   key <AB03> { [         c,          C,     copyright,             cent ] };
   key <AB06> { [         n,          N,        ntilde,           Ntilde ] };
   key <AB07> { [         m,          M,            mu,               mu ] };
   key <AB08> { [     comma,       less,      ccedilla,         Ccedilla ] };
   key <AB09> { [    period,    greater, dead_abovedot,       dead_caron ] };
   key <AB10> { [     slash,   question,  questiondown,        dead_hook ] };
   key <BKSL> { [ backslash,        bar,       notsign,        brokenbar ] };

   include "level3(ralt_switch)"
};

// Based on symbols/us_intl keyboard map:
// Dead-keys definition for a very simple US/ASCII layout.
// by Conectiva ([http://www.conectiva.com.br](http://www.conectiva.com.br))
// modified by Ricardo Y. Igarashi (iga@that.com.br)

// Added the following deadkeys, to make it truly international:
//
// dead_macron: on AltGr-minus
// dead_breve: on AltGr-parenleft
// dead_abovedot: on AltGr-period
// dead_abovering: on AltGr-0
// dead_doubleacute: on AltGr-equal (as quotedbl is already used)
// dead_caron: on AltGr-less (AltGr-shift-comma)
// dead_cedilla: on AltGr-comma
// dead_ogonek: on AltGr-semicolon
// dead_belowdot: on AltGr-underscore (AltGr-shift-minus)
// dead_hook: on AltGr-question
// dead_horn: on AltGr-plus (AltGr-shift-equal)
// dead_diaeresis: on AltGr-colon (Alt-shift-semicolon)
//
// those were already there:
// dead_grave
// dead_acute
// dead_circumflex
// dead_tilde
// dead_diaeresis

partial alphanumeric_keys
xkb_symbols "alt-intl" {

 name[Group1]= "U.S. English - Alternative international (former us_intl)";

 include "us"

 key <TLDE> { [ dead_grave, dead_tilde,    grave,            asciitilde    ] };
 key <AE05> { [          5, percent,       EuroSign                        ] };
 key <AE06> { [          6, dead_circumflex, asciicircum,    asciicircum   ] };
 key <AE09> { [          9, parenleft,     dead_breve,       dead_breve    ] };
 key <AE10> { [          0, parenright,    dead_abovering,   dead_abovering] };
 key <AE11> { [      minus, underscore,    dead_macron,      dead_belowdot ] };
 key <AE12> { [      equal, plus,          dead_doubleacute, dead_horn     ] };

 key <AD03> { [          e, E,              EuroSign,         cent         ] };

 key <AC10> { [  semicolon, colon,          dead_ogonek,   dead_diaeresis  ] };
 key <AC11> { [ dead_acute, dead_diaeresis, apostrophe,    quotedbl        ] };

 key <AB08> { [      comma, less,           dead_cedilla,  dead_caron      ] };
 key <AB09> { [     period, greater,        dead_abovedot, dead_circumflex ] };
 key <AB10> { [      slash, question,       dead_hook,     dead_hook       ] };

 include "level3(ralt_switch)"
};

// based on a keyboard map from an 'xkb/symbols/dk' file
//
// $XFree86: xc/programs/xkbcomp/symbols/dvorak,v 1.5 2004/01/03 16:35:07 herrb Exp $

partial alphanumeric_keys
xkb_symbols "dvorak" {

   name[Group1]= "U.S. English - Dvorak";

   // Alphanumeric section

   key <TLDE> { [       grave, asciitilde, dead_grave, dead_tilde      ] };

   key <AE01> { [          1,  exclam          ]       };
   key <AE02> { [          2,  at              ]       };
   key <AE03> { [          3,  numbersign      ]       };
   key <AE04> { [          4,  dollar, cent, EuroSign]       };
   key <AE05> { [          5,  percent         ]       };
   key <AE06> { [          6,  asciicircum, dead_circumflex, dead_circumflex ] };
   key <AE07> { [          7,  ampersand       ]       };
   key <AE08> { [          8,  asterisk        ]       };
   key <AE09> { [          9,  parenleft,  dead_grave] };
   key <AE10> { [          0,  parenright      ]       };
   key <AE11> { [ bracketleft, braceleft       ]       };
   key <AE12> { [ bracketright, braceright,  dead_tilde] };

   key <AD01> { [  apostrophe, quotedbl, dead_acute, dead_diaeresis    ] };
   key <AD02> { [      comma,  less,   dead_cedilla, dead_caron        ] };
   key <AD03> { [      period, greater, dead_abovedot, periodcentered  ] };
   key <AD04> { [          p,  P               ]       };
   key <AD05> { [          y,  Y, yen          ]       };
   key <AD06> { [          f,  F               ]       };
   key <AD07> { [          g,  G, gcircumflex, Gcircumflex]       };
   key <AD08> { [          c,  C, ccircumflex, Ccircumflex]       };
   key <AD09> { [          r,  R, registered, copyright]       };
   key <AD10> { [          l,  L               ]       };
   key <AD11> { [      slash,  question        ]       };
   key <AD12> { [      equal,  plus            ]       };

   key <AC01> { [          a,  A, ae, AE       ]       };
   key <AC02> { [          o,  O, odiaeresis, Odiaeresis]       };
   key <AC03> { [          e,  E, eacute, Eacute]       };
   key <AC04> { [          u,  U, ubreve, Ubreve]       };
   key <AC05> { [          i,  I               ]       };
   key <AC06> { [          d,  D               ]       };
   key <AC07> { [          h,  H, hcircumflex, Hcircumflex]       };
   key <AC08> { [          t,  T               ]       };
   key <AC09> { [          n,  N, ntilde, Ntilde]       };
   key <AC10> { [          s,  S, scircumflex, Scircumflex]       };
   key <AC11> { [      minus,  underscore      ]       };

   key <AB01> { [   semicolon, colon, dead_ogonek, dead_doubleacute ] };
   key <AB02> { [          q,  Q               ]       };
   key <AB03> { [          j,  J, jcircumflex, Jcircumflex]       };
   key <AB04> { [          k,  K               ]       };
   key <AB05> { [          x,  X               ]       };
   key <AB06> { [          b,  B               ]       };
   key <AB07> { [          m,  M               ]       };
   key <AB08> { [          w,  W, ubreve, Ubreve]       };
   key <AB09> { [          v,  V               ]       };
   key <AB10> { [          z,  Z               ]       };
};

// phonetic layout for Russian letters on an US keyboard
// by Ivan Popov <pin@konvalo.org> 2005-07-17

// level3 modifier is a shortcut to the "us" meaning of the keys where
// we place cyrillic letters, handy for accessing the corresponding
// punctuation marks.
// It is important to have access to punctuation marks, and the rest of
// alphabetical keys are added for being consequent so that the users
// can expect the level3 modifier to give what the key label shows.

partial alphanumeric_keys
xkb_symbols "rus" {

   name[Group1]= "U.S. English - Russian phonetic";

   include "us(basic)"

key.type[group1]="FOUR_LEVEL_ALPHABETIC";

   key <LatA> {        [ Cyrillic_a, Cyrillic_A ]      };
   key <LatB> {        [ Cyrillic_be, Cyrillic_BE ]    };
   key <LatW> {        [ Cyrillic_ve, Cyrillic_VE ]    };
   key <LatG> {        [ Cyrillic_ghe, Cyrillic_GHE ]  };
   key <LatD> {        [ Cyrillic_de, Cyrillic_DE ]    };
   key <LatE> {        [ Cyrillic_ie, Cyrillic_IE ]    };
   key <TLDE> {        [ Cyrillic_io, Cyrillic_IO, grave, asciitilde ] };
   key <LatV> {        [ Cyrillic_zhe, Cyrillic_ZHE ]  };
   key <LatZ> {        [ Cyrillic_ze, Cyrillic_ZE ]    };
   key <LatI> {        [ Cyrillic_i, Cyrillic_I ]      };
   key <LatJ> {        [ Cyrillic_shorti, Cyrillic_SHORTI ]    };
   key <LatK> {        [ Cyrillic_ka, Cyrillic_KA ]    };
   key <LatL> {        [ Cyrillic_el, Cyrillic_EL ]    };
   key <LatM> {        [ Cyrillic_em, Cyrillic_EM ]    };
   key <LatN> {        [ Cyrillic_en, Cyrillic_EN ]    };
   key <LatO> {        [ Cyrillic_o, Cyrillic_O ]      };
   key <LatP> {        [ Cyrillic_pe, Cyrillic_PE ]    };
   key <LatR> {        [ Cyrillic_er, Cyrillic_ER ]    };
   key <LatS> {        [ Cyrillic_es, Cyrillic_ES ]    };
   key <LatT> {        [ Cyrillic_te, Cyrillic_TE ]    };
   key <LatU> {        [ Cyrillic_u, Cyrillic_U ]      };
   key <LatF> {        [ Cyrillic_ef, Cyrillic_EF ]    };
   key <LatH> {        [ Cyrillic_ha, Cyrillic_HA ]    };
   key <LatC> {        [ Cyrillic_tse, Cyrillic_TSE ]  };
   key <AC10> {        [ Cyrillic_che, Cyrillic_CHE, semicolon, colon ] };
   key <AD11> {        [ Cyrillic_sha, Cyrillic_SHA, bracketleft, braceleft] };
   key <AD12> {        [ Cyrillic_shcha, Cyrillic_SHCHA, bracketright, braceright ]    };
   key <AE12> {        [ Cyrillic_hardsign, Cyrillic_HARDSIGN, equal, plus ] };
   key <LatY> {        [ Cyrillic_yeru, Cyrillic_YERU ]        };
   key <LatX> {        [ Cyrillic_softsign, Cyrillic_SOFTSIGN ]        };
   key <BKSL> {        [ Cyrillic_e, Cyrillic_E, backslash, bar ]      };
   key <AC11> {        [ Cyrillic_yu, Cyrillic_YU, apostrophe, quotedbl ] };
   key <LatQ> {        [ Cyrillic_ya, Cyrillic_YA ]    };

   include "level3(ralt_switch)"
};


---

### Post by Rxke on 2005-11-15
This is a golden tip, thanks!

---

