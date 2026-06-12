---
title: "Bash launcher script for Java App (OmegaT) issues"
date: 2009-04-30
forum: General Help
---

### Post by Gvigo on 2009-04-30
Hello and thanks in advance for any suggestions.

I'm using 8.10.

I've already installed the latest jre from Sun, but I want to leave the stock jre from the repositories installed and use the new jre only for OmegaT because the old one works with other apps and I don't want to mess with it.  (OmegaT is a java Computer Aided Translation app)  

By the way, the reason I want to use the new jre (6.0.13) is that there's a bug in the old one affecting the gui that's been corrected by Sun in releases more recent than the one in the repositories.

I'm assuming there's a way to tell OmegaT which jre to use in the launcher script, but I don't know much about writing scripts and I just can't figure out where and how to add what I need. 

The script below works, but it uses the old jre.


```
[INDENT]#!/bin/bash

#-Dsun.java2d.opengl=true \      #add somewhwere to improve gui speed
#-/etc/jre1.6.0_13        #path to new jre
java -Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel -jar /usr/local/lib/OmegaT/OmegaT_2.0.1_Beta_Without_JRE/OmegaT.jar
[/INDENT]
```

---

### Post by i.r.id10t on 2009-04-30
Add in a "export JAVA_HOME=/path/to/new/jre"

and maybe a "PATH=$PATH:/path/to/new/jre/bin"

---

### Post by Gvigo on 2009-05-01
Thanks, I think that's what I needed

But, I couldn't get it to work, probably because jre1.6.0.13 wasn't being found, and then I did some things and now I have serious java problems...   like I keep getting "java: command not found"...   this is probably the result of some error I made with update-alternatives java...  I'll have to figure it out later

---

### Post by Gvigo on 2009-05-01
For those who may be interested in doing something similar in the future, I ended up just changing the last line to:

[INDENT]/usr/lib/jvm/jre1.6.0_13/bin/java -Dswing.defaultlaf=com.sun.java.swing.plaf.gtk.GTKLookAndFeel -jar /usr/local/lib/OmegaT/OmegaT_2.0.1_Beta_Without_JRE/OmegaT.jar



[/INDENT]

---

