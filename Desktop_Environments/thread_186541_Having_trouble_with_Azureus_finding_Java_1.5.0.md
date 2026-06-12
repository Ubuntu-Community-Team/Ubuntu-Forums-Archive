---
title: "Having trouble with Azureus finding Java 1.5.0?"
date: 2006-06-02
forum: Desktop Environments
---

### Post by vvlist on 2006-06-02
If you are getting error messages in the terminal when starting Azureus 2.4.0.2 saying something about not finding java 1.4.0 when you have 1.5.0 installed... try this:> sudo update-alternatives --config java
It will ask you what version of java to use, choose 1.5.0 which was > /usr/lib/jvm/java-1.5.0-sun/jre/bin/java in the terminal, run Azureus (from where ever you have it installed) and it should be fixed.:cool:

---

### Post by FredB on 2006-06-02
Thanks for the tip. I grabbed azureus from official site, and I modified the path in the launching script. Am I a little too geeky ? ;)

---

