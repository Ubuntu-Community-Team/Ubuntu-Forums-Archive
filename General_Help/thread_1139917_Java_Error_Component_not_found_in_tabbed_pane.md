---
title: "Java Error: Component not found in tabbed pane"
date: 2009-04-27
forum: General Help
---

### Post by amrbekhit on 2009-04-27
Hello all,

I've come across this error while using JabRef, a Java based reference manager:

```
java.lang.IllegalArgumentException: component not found in tabbed pane
	at javax.swing.JTabbedPane.setSelectedComponent(JTabbedPane.java:659)
	at net.sf.jabref.imports.OpenDatabaseAction.performPostOpenActions(Unknown Source)
	at net.sf.jabref.imports.OpenDatabaseAction.openIt(Unknown Source)
	at net.sf.jabref.imports.OpenDatabaseAction$1.run(Unknown Source)
```

The error occurs when I have a library already and I try to open another library. JabRef opens the new library in a new tab and I get this error. The program seems to work just fine however and this error doesn't happen all the time.

I worried I might have done something to my Java installation as I did remove OpenJDK and install Sun Java 6 to get JabRef to work at its best.

I've attached a list of all my installed packages in the text file, in case I have a package missing.

Any ideas?

--Amr

---

### Post by blueled on 2009-10-18
Although this post is quite old, I had the same problem until a while ago, and I solved it by adding the extension .bib to the filename I was trying to open with JabRef and was giving me the same error.

So, in case this was the case with you too and were trying to open a file "articles", just rename it "articles.bib"

---

