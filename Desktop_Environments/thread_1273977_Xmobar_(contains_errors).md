---
title: "Xmobar (contains errors)"
date: 2009-09-24
forum: Desktop Environments
---

### Post by PurposeOfReason on 2009-09-24
Xmobar won't start and I'm not too sure as to why, I'm sure my config it valid:
```

Config { font = "xft:Terminus-11"
       , bgColor = "black"
       , fgColor = "lightskyblue"
       , position = Top
       , commands = [ Run Date "%a %b %_d %Y" "date" 360
                    , Run Date "%H:%M:%S" "time" 10
                    , Run StdinReader
                    ]
       , sepChar = "%"
       , alignSep = "}{"
       , template = "%StdinReader% }{<fc=DarkSlateGray3>[ %date% ]</fc><fc=aquamarine2,black>[ %time% ]</fc>"
       }

```

---

