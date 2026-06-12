---
title: "Compiz is installed but nothing works ?"
date: 2007-09-13
forum: Desktop Effects &amp; Customization
---

### Post by czepluch on 2007-09-13
I installed compiz-fusion with trevino's repo, but when I try to run compiz --replace I get this:
```

/usr/bin/compiz.real (core) - Error: dlsym: /usr/lib/compiz/libccp.so: undefined symbol: getCompPluginInfo20070830
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'ccp'

```

And I cannot open ccsm ? :S

I had compiz-fusion before, but wanted to try another repo and now this happens.

---

### Post by z0phi3l on 2007-09-13
Try:

```
 compiz --replace & 
```

---

### Post by czepluch on 2007-09-13
> **z0phi3l said:**
> Try:

```
 compiz --replace & 
```

Still doesn't work.

---

### Post by czepluch on 2007-09-13
I would really like some help on this one. I'm running without window decorations or anything at this time. And it is driving me crazy.

---

### Post by czepluch on 2007-09-13
bump

---

### Post by jim_ski on 2007-09-13
This happened after another recent update too, got mine working by uninstalling all the compiz fusion in synaptic then reinstalling it, seems to have wiped my settings but its working again.

---

### Post by czepluch on 2007-09-13
> **jim_ski said:**
> This happened after another recent update too, got mine working by uninstalling all the compiz fusion in synaptic then reinstalling it, seems to have wiped my settings but its working again.

Thanks. But I've tried that like 10 times or so.

---

### Post by miguelitu on 2007-09-14
the same issu here

it was working before last update...

---

### Post by gtrtx on 2007-09-14
Just a thought.....

did you remove both   ~/.config/compiz  and  ~/.gconf/apps/compiz  before reinstalling?


Also in synaptic, make sure that the trevino repo's are the only ones you have enabled.  With synaptic open click the "Origin" button down in the left corner,  it will list all of your repositories that are enabled. Click the trevino repos and check to make sure everything is installed.

---

