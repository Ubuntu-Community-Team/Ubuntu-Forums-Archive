---
title: "forward root system mail to external email address? how?"
date: 2006-06-17
forum: Desktop Environments
---

### Post by jetpeach on 2006-06-17
title says it all, some of us are interested from an old thread here
[http://www.ubuntuforums.org/showthread.php?t=7321](http://www.ubuntuforums.org/showthread.php?t=7321)
but that doesn't say how to send it to an external (gmail for myself) address.  basically, i don't like having to use the terminal mail program to read it and don't use any mail program except gmail, so the solutions using evolution aren't any good to me...

thanks for any help!

---

### Post by jjcv on 2006-06-17
MAke sure you have a mail server installed.... something like postfix.

Edit /etc/aliases

added or edit an entry for root to forward email:

root:     [email]myname@gmail.com[/email]

Save the file.

Run the program 'newaliases' which will update the aliase database and test it.

---

### Post by scxtt on 2006-06-17
i use a program called "mailx" to mail from the command line - all i had to do to forward email sent to $user@$hostname was to add a .forward file (that contains only the email address you want to forward to in it - i used my gmail account) in the users ~ directory ... worked fine ... i only have 1 user account on my box, and it's allowed root access via sudo - i've also not explicitly enabled the root account (all root mail goes to that users /var/mail/$username box) ... if you have, try putting a .forward in /root ...

---

### Post by TheWizzard on 2006-06-20
hi jetpeach - i think i found the cause of the problem and a workaround.
i used the default installation configuration for dapper drake. 
- root's mail can be forwarded to a local mailbox, but not to an external one. probably for security reasons. 
- workaround: 
1) forward root's mail to your local mailbox
2) create /home/yourusername/.forward
3) add the external email address to this file and finish with an empty line. 
this works on my box. 

cheers

---

### Post by jetpeach on 2006-06-20
thanks guys, i'll be testing this out shortly.

---

### Post by TheWizzard on 2006-09-11
OK, here's how to forward root's mail to an external account like gmail:
I'm using the KDE version of Ubuntu, but this should work also in GNOME. Just use gedit instead of kate. 


use synaptic/adept/apt-get to install &#8216;postfix&#8217; and &#8216;mailx&#8217;
during the installation you have to answer some questions. In adept you have to click on &#8216;show details&#8217;
type = &#8216;internet site&#8217;; mail name = &#8216;hostname&#8217;
I'm not sure if this is the best, but it works. 

Forward the rootmail to your local account: 
1.Menu -> System -> Konsole. 
2.Typ: sudo kate /root/.forward 
3.Typ username@localhost (your username and your localhostname!) <enter>
4.Save and exit Kate

Forward your local mail to the external account
1.Menu -> System -> Konsole. 
2.Typ: kate /home/username/.forward 
3.Typ the external email address <enter> 
4.Save and exit Kate 

You can check the mailserver with the command: sudo tail -f /var/log/mail.info

---

### Post by solo23 on 2008-01-28
I try setting up my system using TheWizzard's guidelines but its not working. I'm behind a proxy so I set the folling line in the main.cf. 


proxy_interfaces = 10.0.255.250

Can some one help plz

using Gusty

---

