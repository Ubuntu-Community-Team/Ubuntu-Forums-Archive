---
title: "I broke apt-get?? I think, please read."
date: 2005-07-19
forum: Desktop Environments
---

### Post by Bandit on 2005-07-19
I just installed Uby 5.04 on my new HD that just arrived and I was going thru installing all my apps. But for some reason now when I go to gnome preferences and try to use the Add Remove software in apt-get it just sits there. But when I click on advanced to switch over to the synaptic apt-get interface it told me I have a broken file or something.. I cant remember at the momment since I am at work.
But anyway the rest of syn aptget seems to be fine, I have installed more apps since then. But how do I get it to show the gnome apps list again.
Thanks,
Joey

---

### Post by mad_scientist03 on 2005-07-19
I would go to the terminal and try "sudo apt-get update" and then "sudo apt-get upgrade" to see what messages get spit to the screen. Post those messages, and maybe we can figure out what's happening.

---

### Post by Lord Illidan on 2005-07-19
or u could type

sudo apt-get -f install 

into a terminal, which will repair broken packages, but before it asks you to do anything copy the output and paste it here...

---

### Post by Bandit on 2005-07-19
Tried what you guys suggested and still no go. The program loads, but the GnomeApts dialog screen still doesnt show anything. Apt-Get its self seems fine?

---

### Post by mad_scientist03 on 2005-07-19
I dont' understand. When you login, click on "Applications", then "System Tools", then "Terminal". Open a terminal, and try either the two commands I listed above ("sudo apt-get update", "sudo apt-get upgrade"), or the command Lord Illidan spoke of, "sudo apt-get -f install".

There should be no "GnomeApts dialog screen", just some text output to the terminal. Copy and paste that output into a reply here, and we can help you diagnose the problem.

---

