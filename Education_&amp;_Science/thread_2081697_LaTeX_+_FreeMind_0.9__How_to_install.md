---
title: "LaTeX + FreeMind 0.9 : How to install"
date: 2012-11-07
forum: Education &amp; Science
---

### Post by pooja on 2012-11-07
Hi, 
I have a problem installing LaTeX plugin for FreeMind.
I've downloaded and extracted the plugin from sourceforge.net but I don't know how to install it.
These are the instructions from the author of the package:
 
```

Installing LaTeXMath Freemind Plugin
====================================

I'm using Linux, under other OSes installation steps may vary.

My FREEMIND_HOME is e.g. /usr/local/freemind-bin-max-0.9.0_RC_7


You'll need to provide the following 3 files:

1. FREEMIND_HOME/plugins/LaTeXMath.xml

  Get it from fm-plugin-latexmath/src/main/resources/

2. FREEMIND_HOME/plugins/latexmath/fm-plugin-latexmath.jar

  cd fm-plugin-latexmath 
  mvn package

  Look for it in target/ and rename it accordingly.


3. FREEMIND_HOME/plugins/latexmath/jlatexmath.jar
  
  Get it from http://forge.scilab.org/index.php/p/jlatexmath/ or
  from your local repository, as it should be downloaded 
  automatically via maven in the previous step, eg.:

  ls ~/.m2/repository/net/sf/alxa/jlatexmath/0.9.3-SNAPSHOT/*jar
 
  Look for the latest and rename it accordingly.

  
--//--

```

From Terminal, I typed the code ```
whereis freemind
``` to get the path:** /usr/share/freemind/**.
I transferred the *LaTeXMath.xml* file from the downloaded package in ~/Downloads/LaTeXMath-Freemind-Plugin-master/ to the /usr/share/freemind/plugins/. All this, roughly corresponds to step #1 of the instructions above. How do I proceed next? As you can see, step #2 mentions some *.jar file which I cannot locate in either target folder (/usr/share/freemind) or downloaded package. There are no *.jar files in the downloaded package, only 2 *.java files -- LatexMathNodeHook.java and  LatexMathNodeView.java. These 2 *.java files are tucked deep within various sub-folders.

---

