---
title: "font issue with Talend Open Studio"
date: 2022-01-27
forum: Desktop Environments
---

### Post by pchantry on 2022-01-27
Hello,

I use Ubuntu 20.04 and I encounter a problem with ONE application (Talend Open Studio) : the app cannot display some characters in some fields, for example:

- at startup, the license agreement page :

[IMG]https://i.stack.imgur.com/n6rXQ.png[/IMG]

- further in the app, in mutli-line fields:

[IMG]https://i.stack.imgur.com/485OP.png[/IMG]


When I run the job, the console log shows the same font problem.


I asked the question 
on Talend community forums ([https://community.talend.com/s/feed/0D55b00006oBMSGCA4?language=en_US](https://community.talend.com/s/feed/0D55b00006oBMSGCA4?language=en_US)), 
on Stackoverflow ([https://stackoverflow.com/questions/70768665/talend-open-studio-encoding-issue](https://stackoverflow.com/questions/70768665/talend-open-studio-encoding-issue)), 
on Eclipse forums ([https://www.eclipse.org/forums/index.php/t/1109916/](https://www.eclipse.org/forums/index.php/t/1109916/)). 
No solution so far, so I ask here.

Seems to be a font issue. I tried changing default system fonts (gnome-tweak-tool) and in Talend I tried changing all the fonts in Preferences. None of these attempts worked.
I have no problem in other apps like Eclipse or Dbeaver (Talend Studio an Dbeaver are Eclipse Based Apps). And one colleague with same laptop and OS don't see the problem in Talend.

Something must be wrong with my Ubuntu laptop.

Any idea ?

Thank you,
Philippe

---

### Post by pchantry on 2022-07-04
Finally a guy on StackOverflow found the solution : [https://stackoverflow.com/questions/70768665/talend-open-studio-encoding-issue](https://stackoverflow.com/questions/70768665/talend-open-studio-encoding-issue)

---

