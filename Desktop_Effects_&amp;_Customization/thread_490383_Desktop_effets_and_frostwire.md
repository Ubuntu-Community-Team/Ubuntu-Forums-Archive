---
title: "Desktop effets and frostwire"
date: 2007-07-02
forum: Desktop Effects &amp; Customization
---

### Post by Morhas on 2007-07-02
Is there anyway to use frostwire while desktop effects are enabled? Whenever I try to I just get a blank screen. Any thoughts?

---

### Post by hyperair on 2007-07-02
Add this line:
```

AWT_TOOLKIT="MToolkit"

```

into your /etc/environment file, then restart the computer. Then it should work.

---

### Post by TrueJk7 on 2007-07-02
Hence the "this is may not work" warning they put on there. Is it while Frostwire is open or while you are playing video media from it? If so, this is a noraml bug with compiz. If you're looking for good desktop effects you may also want to look into "beryl" I personaly use it. More than just the modified compiz that default Ubuntu comes with.

Edit: HyperAir replyed before I posed by response

---

### Post by Morhas on 2007-07-02
Stupid questoin: how do I give myself permissions to change that file?

And Im plan on using beryl, I want to get a little more fimilar with linux before I jump into beryl though.

---

### Post by TrueJk7 on 2007-07-02
if I am right it being a text file you can

# sudo gedit /etc/environment

then just do what hyperair said :)

---

### Post by Morhas on 2007-07-02
Hmmm. That didn't seem to work. Any other ideas? I still get the same error as before.

---

### Post by Morhas on 2007-07-02
```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_CA.UTF-8"
AWT_TOOLKIT="MToolkit"

```

Is what /etc/enviroment lookds like. I it can't be fixed. What are other good p2p programes that would work with the desktop effects enabled?

Thanks.

---

### Post by AndrewGene on 2007-07-02
AWT_TOOLKIT="MToolkit"

type that into the terminal when you see the blank screen.  It should then go away.
Instead of beryl try the compiz fusion.  It is very easy to install.  Plus beryl won't be upgraded anymore because it merged with compiz (hence, compiz fusion).

---

### Post by jrekkedal on 2007-08-09
This fix worked for me after a restart of my PC.  

Can someone explain the "why" it fixed it?  I don't like being a simply cut/paste enduser. :confused:

---

### Post by esc1 on 2007-08-09
I don't get why compiz fusion has a problem with this.  What I understood is its a flash problem.  The workaround I'm using is to make an executable text file with the following and make it executable.

#!/bin/bash
export AWT_TOOLKIT=MToolkit
export HOSTNAME=localhost
/usr/bin/frostwire

---

### Post by hyperair on 2007-08-09
Well considering the fix is for all Swing applications, I put it into my /etc/environment file, so that it's fixed systemwide.

Anyway, the environment variable probably overrides the GUI toolkit that Java uses for its Swing applications, so you'll use another toolkit (in this case MToolkit) as opposed to the buggy one.

---

### Post by esc1 on 2007-08-10
I can't find /etc/environment

Using Compiz Fusion.  Would like to fix this problem.  Can you go into more detail for a noob?

---

### Post by hyperair on 2007-08-11
Run this command in a terminal:
```
echo "AWT_TOOLKIT=MToolkit" | sudo tee /etc/environment
```

---

