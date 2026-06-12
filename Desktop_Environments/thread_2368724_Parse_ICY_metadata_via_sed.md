---
title: "Parse ICY metadata via sed"
date: 2017-08-14
forum: Desktop Environments
---

### Post by darkskylord88 on 2017-08-14
Hello, everyone!
I have a trouble with sed and parsing ICY metadata, i read help about sed - very hard.
So, trouble's name is notification of current mplayer song.
A create mplayer-somafm.sh
```

#!/bin/bash
mplayer $1 2>&1 | while read -r line; do
    if grep "ICY" <<< "$line" &>/dev/null; then
        echo $line | sed "s/^.*ICY[^:]*: StreamTitle='//p";
        notify-send "$line";
    fi;
done

```

But, out are:
ICY Info: StreamTitle='Tensnake - Things Left To Say';StreamUrl='';
Tensnake - Things Left To Say';StreamUrl='';

How do I delete ';StreamUrl=''; ?
Only "Tensnake - Things Left To Say" should be.
Best regards, Vladimir

---

### Post by steeldriver on 2017-08-14
You shouldn't need both sed and grep - either

```

$ echo "ICY Info: StreamTitle='Tensnake - Things Left To Say';StreamUrl='';'" | sed -n "/ICY/ s/^.*ICY[^:]*: StreamTitle='\([^']*\).*/\1/p"
Tensnake - Things Left To Say

```

(using a sed capture group note the -n to prevent default printing) or

```

$ echo "ICY Info: StreamTitle='Tensnake - Things Left To Say';StreamUrl='';'" | grep -Po "ICY Info: StreamTitle='\K[^']*"
Tensnake - Things Left To Say

```
or
```

$ echo "ICY Info: StreamTitle='Tensnake - Things Left To Say';StreamUrl='';'" | grep -Po "ICY Info: StreamTitle='\K.*?(?=')"
Tensnake - Things Left To Say

```

using perl-style look behind

---

### Post by darkskylord88 on 2017-08-15
Hello, Steeldriver!
Thanks for help!

```

mplayer $1 2>&1 | while read -r line; do
    if grep "ICY" <<< "$line" &>/dev/null; then
    song=$(grep -Po "ICY Info: StreamTitle='\K.*?(?=')" <<< $line);
    notify-send SomaFM "$song";
   fi;
done

```

I need grep for notify-send, without it the notify-send show too many notifications

---

