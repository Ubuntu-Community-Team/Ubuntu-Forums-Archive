---
title: "HOWTO: access gmail mailbox through mail notifier."
date: 2008-01-27
forum: Desktop Effects &amp; Customization
---

### Post by Stagger Lee on 2008-01-27
Hi, 

although I am new to Linux I am writing this little guide because I spent a lot of time trying to do this little trick and then I managed to with the help of Mail NOtify developer Jean-Yves LeFort. 

When I switched to Ubuntu, the thing I was missing the most was Gmail notifier. I like to use the web interface rather than Thunderbird or Evolution, for various reasons. And I like the idea of clicking on the little icon on the taskbar and be able to write a new email and do whatever I need. 

Mail Notify is an excellent tool, but by defaul it does not let you log into the mailbox with one click, like gmail does. If you want to do that, here is what you need to do. 

1) get Mail Notify from the repository :) or from [http://www.nongnu.org/mailnotify/]("http://www.nongnu.org/mailnotify/") and set it, entering username and pwd. 
2) go to System -> Preferences -> Preferred Applications and select custom, and enter "open-gmail" as the command. 
3) go to the Mail Notify settings and select Launch Mail Reader as the one click action. 
4) Then create a text file with the following content:

=== cut
#!/bin/sh
exec gnome-open [http://www.gmail.com](http://www.gmail.com)
=== cut

Name it open-gmail and save it to /usr/bin/open-gmail. 

5)Open terminal and type: he script executable:

sudo chmod a+x /usr/bin/open-gmail

Now when you click on the Mail Notify icon, your browser should open your gmail inbox: this is good both for reading incoming mail and for writing new messages. 

Hope it works. 


Cheers!

---

### Post by Cybergod on 2008-01-27
I would just use CheckGmail :)

---

### Post by Meyithi on 2008-01-28
Ditto, Checkgmail does everything I need.

---

### Post by scrooge_74 on 2008-01-28
I love checkgmail

---

### Post by noremac on 2008-01-28
Wow, I have just fallen in love with CheckGmail. Never knew of it till now. Being able to archive stuff without ever opening a browser is outstanding. Thanks!
-Cameron

---

### Post by noremac on 2008-01-28
Well, I still like this program, but only a few minutes after I installed it, I am seeing it frequently go to an error icon and has a "400 Bad Request" as the details if I have my mouse over the icon. It is still checking the email, but anyone know what might be causing this?
Thanks in advance.
-Cameron

---

### Post by Cybergod on 2008-01-28
> **noremac said:**
> Well, I still like this program, but only a few minutes after I installed it, I am seeing it frequently go to an error icon and has a "400 Bad Request" as the details if I have my mouse over the icon. It is still checking the email, but anyone know what might be causing this?
Thanks in advance.
-Cameron

I had some similar experiences with checkgmail when I first started using it.  I found a website that talks you through installing some extra stuff and it seemed to fix every problem I ever had.  Try this link [http://marius.scurtescu.com/2007/06/25/installing_checkgmail_on_ubuntu]("http://marius.scurtescu.com/2007/06/25/installing_checkgmail_on_ubuntu")

---

### Post by scrooge_74 on 2008-01-31
I had something like that problem a few weeks ago, seems somewhere and update broke it and another update fixed it

---

