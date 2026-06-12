---
title: "how to change keyboard character map"
date: 2008-11-01
forum: Desktop Environments
---

### Post by kornelix on 2008-11-01
I needed to add German umlaut characters (äöüß) and the Euro sign (€) to my US keyboard. Here is a 1-minute lesson on how to do this or similar tasks.

```

//  This keyboard map adds German umlauts, sharfes-S, and Euro symbol 
//  to the standard US keyboard layout as follows:
//       right-Alt + A O U S E  >>  ä ö ü ß €
//       right-Alt + shift + A O U  >>  Ä Ö Ü
//
//
//  Ubuntu 8.04:
//  Save this file as /etc/X11/xkb/symbols/us_de
//  In the file /etc/X11/xorg.conf, change "XkbLayout" to "us_de"
//
//  Ubuntu 8.10:
//  In the first section of the file /usr/share/X11/xkb/symbols/us,
//  replace or add the lines below marked with:  //***

default
partial alphanumeric_keys modifier_keys 
xkb_symbols "basic" {

    name[Group1]= "U.S. English";

    // Alphanumeric section
    key <TLDE> {    [     grave,    asciitilde    ]    };
    key <AE01> {    [      1,    exclam         ]    };
    key <AE02> {    [      2,    at        ]    };
    key <AE03> {    [      3,    numbersign    ]    };
    key <AE04> {    [      4,    dollar        ]    };
    key <AE05> {    [      5,    percent        ]    };
    key <AE06> {    [      6,    asciicircum    ]    };
    key <AE07> {    [      7,    ampersand    ]    };
    key <AE08> {    [      8,    asterisk    ]    };
    key <AE09> {    [      9,    parenleft    ]    };
    key <AE10> {    [      0,    parenright    ]    };
    key <AE11> {    [     minus,    underscore    ]    };
    key <AE12> {    [     equal,    plus        ]    };

    key <AD01> {    [      q,    Q         ]    };
    key <AD02> {    [      w,    W        ]    };
    key <AD03> {    [      e,    E, EuroSign  ]    };                   //***
    key <AD04> {    [      r,    R        ]    };
    key <AD05> {    [      t,    T        ]    };
    key <AD06> {    [      y,    Y        ]    };
    key <AD07> {    [      u,    U, udiaeresis, Udiaeresis    ]    };    //***
    key <AD08> {    [      i,    I        ]    };
    key <AD09> {    [      o,    O, odiaeresis, Odiaeresis    ]    };    //***
    key <AD10> {    [      p,    P        ]    };
    key <AD11> {    [ bracketleft,    braceleft    ]    };
    key <AD12> {    [ bracketright,    braceright    ]    };

    key <AC01> {    [      a,    A, adiaeresis, Adiaeresis    ]    };    //***
    key <AC02> {    [      s,    S, ssharp    ]    };                   //***
    key <AC03> {    [      d,    D        ]    };
    key <AC04> {    [      f,    F        ]    };
    key <AC05> {    [      g,    G        ]    };
    key <AC06> {    [      h,    H        ]    };
    key <AC07> {    [      j,    J        ]    };
    key <AC08> {    [      k,    K        ]    };
    key <AC09> {    [      l,    L        ]    };
    key <AC10> {    [ semicolon,    colon        ]    };
    key <AC11> {    [ apostrophe,    quotedbl    ]    };

    key <AB01> {    [      z,    Z         ]    };
    key <AB02> {    [      x,    X        ]    };
    key <AB03> {    [      c,    C        ]    };
    key <AB04> {    [      v,    V        ]    };
    key <AB05> {    [      b,    B        ]    };
    key <AB06> {    [      n,    N        ]    };
    key <AB07> {    [      m,    M        ]    };
    key <AB08> {    [     comma,    less        ]    };
    key <AB09> {    [    period,    greater        ]    };
    key <AB10> {    [     slash,    question    ]    };

    // End alphanumeric section

    include "level3(ralt_switch)"                              //***
};

```

---

### Post by kikazaru on 2008-11-02
Nice work... maybe you can help me do this:

I want to map the "Muhenkan" and "Henkan" buttons on a Lenovo T400 with a Japanese keyboard to function as backspace buttons... I tried inserting this in my us dvorak international keymap, but it doesn't achieve anything. I tried mapping them to keys like "a" but that didn't work either... I think the NFER and XFER buttons aren't recognized. I tried this with the generic 105 key, generic japanese 106 key layouts...


    key <NFER> { [  KP_Delete            ] };
    key <XFER> { [  KP_Delete            ] };

Incidentally, I changed buttons like the "a" key to the "o" key to check that I was actually having *some* effect, -which indeed I was.

---

### Post by kornelix on 2008-11-02
> **kikazaru said:**
> Nice work... maybe you can help me do this ... 

I wish I could help but I am really clueless.

I wish also that someone with some common sense would redesign the whole key-mapping mess. There must be an easy to use GUI somewhere that allows one to map arbitrary new characters to specific key combinations, but I have not been able to fine one.

Does anyone out there know more?

---

