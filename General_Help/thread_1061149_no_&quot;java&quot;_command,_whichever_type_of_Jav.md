---
title: "no &quot;java&quot; command, whichever type of Java I install"
date: 2009-02-05
forum: General Help
---

### Post by Nathan_M on 2009-02-05
I have  several types of Java installed (using apt-get), but whatever I do, there is no java command. How can I fix this? I've tried reinstalling the official Sun one, but still can't get anything working.

Weirdly, I've just discovered, there is a javac command!

---

### Post by Nathan_M on 2009-02-05
Sorry... one of those times when you search for ages for something, then as soon as you decide to resort to a forum post, you find the solution...

$ sudo update-java-alternatives -s java-6-sun

---

