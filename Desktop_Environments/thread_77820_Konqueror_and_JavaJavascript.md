---
title: "Konqueror and Java/Javascript"
date: 2005-10-17
forum: Desktop Environments
---

### Post by skyboy on 2005-10-17
I can't get Konqueror to run Java or Javascript. I just installed the last JVM. I tried it with Firefox, and it worked like a charm. Bug or silly me ??

---

### Post by Belohin on 2005-10-19
In Konqueror you can do the settings in Settings menu -> Configure Konqueror -> Java&Javascript section. There is a field Path to java executable. If simple 'java' does not work (some lack in PATH environmental variable ?) write the whole path to the installed java binary.
The Javascript option is on the next tab.

---

### Post by bennettg on 2005-11-08
since i am such a noob, can you tell me the path(s) or at least the file names so I can fix this as well.

thanks in advance

---

### Post by f1dave on 2005-11-08
I don't know if it works with java, but there is a feature in konqueror that scans for plugins installed for other browsers. Click the plugins section in "configure konqueror" and then click "scan for new plugins". Perhaps that will do the trick.

---

### Post by bennettg on 2005-11-09
tried that. no luck.

can anyone else assist?

---

### Post by Thorsten on 2005-11-11
[quote=skyboy]I can't get Konqueror to run Java or Javascript. I just installed the last JVM. I tried it with Firefox, and it worked like a charm. Bug or silly me ??[/quote] 
First of all, Java and JavaScript really have nothing to do with each other. You don't need any additional applications to run JavaScript. Either your browser does JavaScript or it doesn't (in which case, there's nothing you can do.) Konqueror does JavaScript, however. All you need to do is enable it with Menu -> Settings -> Configure Konqueror -> Java & JavaScript [categories on left] -> JavaScript [tab on right] -> [x] Enable JavaScript globally ... and set all options to "Allow."

Regarding Java, it depends on the method you chose to install the JVM. If you installed Java using a Kubuntu package manager (e.g., apt-get, synaptic, kynaptic, adept), the Java start script should be in an executable path. You can test this by opening a konsole an running
```
which java
``` 
If you get no output, there is no executable named "java" in your path. Otherwise, you'll get the full path to "java." If "java" is in your path, it will be sufficient to simply specify "java" in the "Path to java executable" field in Konqueror's configuration dialog.

HTH,
Thorsten

---

### Post by wdiggums on 2008-04-30
click places:click computer: click file system : click usr : click lib: click jvm : click the folder for your installed java ( ie java-1.6.0-sun ) : click bin : right click java :click properties : the location should be shown for the link to executable java ,highlight and copy the location  :open konqueror click settings , configure , java .  paste the link to executable java into konqueror . click apply , this is what finally worked for me best wishes all:)

---

