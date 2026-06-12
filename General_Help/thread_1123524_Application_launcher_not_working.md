---
title: "Application launcher not working"
date: 2009-04-12
forum: General Help
---

### Post by cristian.vrabie on 2009-04-12
Hi guys,
I recently installed Intellij IDEA into **/opt/idea**. To launch the ide you have to call **/opt/idea/bin/idea.sh** wich launches the java app with the right parameters. 

I tried to do an application launcher for it but it doesn't do anything. 

So I tried to open it in terminal. Both calling **/opt/idea/bin/idea.sh** or **sh /opt/idea/bin/idea.sh** work but if I close the terminal this also closes the app. Further more, ** /opt/idea/bin/idea.sh &** behaves the same.

After some reading i did: **nohup /opt/idea/bin/idea.sh &**. Now if I close the terminal the app doesn't close. 

However, the application launcher still doesn't work. (i tried to add the command directly into the application launcher and making a script that does the nohup launch then pointing the launcher to it).

Any idea what's going on?

---

### Post by cristian.vrabie on 2009-04-12
Just tried it on KDE and it seems to work. It may be a GNOME specific thing (thought I can't imagine what it could be).

---

