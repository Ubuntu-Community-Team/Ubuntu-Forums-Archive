---
title: "Firefox crashing and create a new profile doenst work too"
date: 2006-08-13
forum: Desktop Environments
---

### Post by Emanuel Felipe on 2006-08-13
hello..

Im having a strange problem with firefox, in some pages like [http://www.w3schools.com/](http://www.w3schools.com/) he crashes, everytime.

In terminal, the message is: "Exceção de ponto flutuante" (portuguese, in english should be something like "floating point exception" not sure...).

Ive tried to remove the profile folder, but doesnt work, the new profile dont start, it gets the same message but after starts the firefox window.

If someone can help me... Ive got the firefox that is in the sources, and swiftfox 1.5.0.6 but as they use the same profile, I get the same error.

And please, AVOID messages like "use opera" and just "I dont know"... thanks

---

### Post by CREEPING DEATH on 2006-08-13
I was having FF issues too, I just removed and re-installed it (sudo-apt).  Surprisingly I didn't lose anything and it works correctly now.  when you re-install, be sure to copy and paste everything that was removed, not just FF.  Good luck!

CD

---

### Post by the-linux-guy on 2006-08-13
Check the version of your installed java engine. Open a terminal and give a "java -version" command, if it says 1.5.x, a lot of people (me included) seem to have massive problems with firefox. I de-installed ALL java related stuff that came with Ubuntu and manually installed java version 1.4.2_08 from Sun's website, with the corresponding java-plugin in my ~/.mozilla/plugins directory. All my troubles vanisched like snow before the sun since then... And Ubuntu became more responsive too... ;-)

---

### Post by Emanuel Felipe on 2006-08-13
> **the-linux-guy said:**
> Check the version of your installed java engine. Open a terminal and give a "java -version" command, if it says 1.5.x, a lot of people (me included) seem to have massive problems with firefox. I de-installed ALL java related stuff that came with Ubuntu and manually installed java version 1.4.2_08 from Sun's website, with the corresponding java-plugin in my ~/.mozilla/plugins directory. All my troubles vanisched like snow before the sun since then... And Ubuntu became more responsive too... ;-)

emanuel@darkstar:~$ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
emanuel@darkstar:~$



Version 1.4.2... =(

So... I disable the java and javascript options in firefox, and it still crashing in some sites...

Anyway, I will try to reinstall java... thanks for your help

---

