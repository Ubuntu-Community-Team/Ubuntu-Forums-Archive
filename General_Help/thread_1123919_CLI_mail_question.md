---
title: "CLI mail question"
date: 2009-04-12
forum: General Help
---

### Post by thelastunavail on 2009-04-12
Recently I installed a new video driver and when i hit control-alt-f1 and went to the command line (non GUI) version of ubuntu hardy it said I have new mail when i logged in.. which i found odd because i never set up evolution mail on the gui and only use webbased gmail. How can i check to see what the message is? could my system be hacked and someones useing it as a mail server or something? any help is appriciated, thanks!

---

### Post by dcstar on 2009-04-12
> **thelastunavail said:**
> Recently I installed a new video driver and when i hit control-alt-f1 and went to the command line (non GUI) version of ubuntu hardy it said I have new mail when i logged in.. which i found odd because i never set up evolution mail on the gui and only use webbased gmail. How can i check to see what the message is? could my system be hacked and someones useing it as a mail server or something? any help is appriciated, thanks!

a) Install the mailx package

b), No, the system generates many things which it tries to inform you about by mailing it to you - if you want to ignore them then that is your choice.

---

### Post by thelastunavail on 2009-04-12
Think I got it now, i will checkout mailx, thanks! :)

---

### Post by hyper_ch on 2009-04-12
check /var/mail for new mail. When you run cronjobs and there's output it will normally be maild to your user. As you have not setup an MTA yet it's very likely to be in /var/mail/ somewhere

---

