---
title: "upstart variable expansion ambiguity"
date: 2012-05-23
forum: Desktop Environments
---

### Post by sean abbott on 2012-05-23
I'm writing my first upstart job to run selenium2 as a service on VMs.  This was my first hack: [http://paste.ubuntu.com/1003268/](http://paste.ubuntu.com/1003268/)  It didn't work, and after adding the suggested environment variable lines to debug my environment, I found out it's because the variables aren't expanding as I expected.  In the pastebin version, they expand like so:   SELENIUM_EXEC='java -jar $SELENIUM_JAR'  So, I saw that in ***some*** of the examples, variable appear to be escaped by single quotes (like here:  [http://upstart.ubuntu.com/cookbook/#env](http://upstart.ubuntu.com/cookbook/#env)), so I tried,   SELENIUM_EXEC="java -jar '$SELENIUM_JAR'"  and then my environment output was:  SELENIUM_EXEC='java -jar '"'"'$SELENIUM_JAR'"'"  #yes, this is a ton of alternating single and double quotes  So, I have two questions.  Which usage of variables is correct if you are going to expand them?  This one:   [http://upstart.ubuntu.com/cookbook/#env](http://upstart.ubuntu.com/cookbook/#env)  or this one: [http://upstart.ubuntu.com/cookbook/#environment-variables](http://upstart.ubuntu.com/cookbook/#environment-variables)  # (scroll to the 'as another example' part.)  Second:  can someone give me a hint as to how to get variable expansion to work as expected?  Thanks!  sean

---

