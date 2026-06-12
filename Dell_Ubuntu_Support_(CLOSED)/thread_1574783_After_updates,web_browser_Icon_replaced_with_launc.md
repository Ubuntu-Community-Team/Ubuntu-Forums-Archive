---
title: "After updates,web browser Icon replaced with launchpad"
date: 2010-09-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hoppy3 on 2010-09-14
[SIZE=4]Inspiron 910,Ubuntu 8.04[/SIZE]
 
[SIZE=4]This model has two desktop modes, the Dell desktop, and Classic desktop, I prefer the classic where my problem appeared a few days ago.[/SIZE]
[SIZE=4]After downloading and installing (many) updates, and doing a restart, the web browser icon was replaced by a launchpad.[/SIZE]
[SIZE=4]Clicking on this, I get error: Not a launch-able item, clicking on Web browser in applications-internet window, I get error:[/SIZE]
[SIZE=4]failed to execute child process "abrowser" (no such file or directory).[/SIZE]
[SIZE=4]I realize this is not a critical problem because I can use the Dell desktop mode where everything works fine. [/SIZE]
[SIZE=4]But I would like some help with it. I've searched this forum, learned a few things, but did not find anything specific enough to help me because linux is new to me.[/SIZE]
[SIZE=4]I tried going into the launch-pad properties and changing it but got nowhere.[/SIZE]

[SIZE=4]Thanks......Larry[/SIZE]

---

### Post by mörgæs on 2010-09-15
What happens if you go into Synaptic and select 'reinstall' for Abrowser?

---

### Post by hoppy3 on 2010-09-15
Thanks for your response.
Reinstalled abrowser and got an error: ume-config-belmont subprocess post-installation script returned error exit status 1.
Did a re-start and nothing changed.

---

### Post by wilee-nilee on 2010-09-15
You can make your own launcher on the desktop, in the panel or in the menu. Just open a launch builder; and with (command) browse go to file-user-bin and click on the browser it will add it to the command.

You can also use the command this way.
[ATTACH]169585[/ATTACH]

I think most of us are used to a OS desktop reference rather then the manufacturers, I have no clue what your talking about there.

---

### Post by hoppy3 on 2010-09-15
Thanks a lot!
I used your screenshot and changed launcher properties. I had no idea what to put in there before.
Problem solved..................thanks again

---

### Post by wilee-nilee on 2010-09-15
> **hoppy3 said:**
> Thanks a lot!
I used your screenshot and changed launcher properties. I had no idea what to put in there before.
Problem solved..................thanks again

Hey it's all small steps for most of us. ;)

---

### Post by ecran on 2010-10-31
I also had this same problem earlier this week with updates.  I'm a complete Ubuntu novice but was able to follow the instructions above to get the launch icon to start Firefox.  Now I have some additional questions I hope someone can guide me through.

I did figure out how to return the browser icon to the top panel and get that to start the browser by using the same commands noted above for the launcher.

But, I can't start the browser by clicking on it in the applications drop down menu.  When I click on it I get an error  message as follows   "could not launch menu item failed to execute child process "abrowser" (no such file or directory)"

An additional thing I've noticed is when you click on the "about web browser" in the help menu you get this message  "XML Parsing Error: undefined entity Location: chrome://browser/content/about dialog Line number 40, column 9:  

any chance one of you pros could guide me through these issues?

many thanks

---

