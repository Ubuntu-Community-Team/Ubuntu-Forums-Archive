---
title: "sending text file as body of email"
date: 2009-06-01
forum: General Help
---

### Post by meg23 on 2009-06-01
I have program set up with mailx that takes a text file and emails it to me automatically. However, the text in the body of the email does not retain the formatting of the original text file, it is all squished together with no appropriate spacing. Is there anyway to retain the line by line formatting?

---

### Post by LoneWolfJack on 2009-06-01
if I understand you correctly, you are sending the contents of a plain text file within a html body tag. html does not interpret line breaks, so you will have to add them before the text file is inserted into the html body in the form of <br> or <p>.

---

### Post by meg23 on 2009-06-01
Didn't quite work. Here is what I got in my gmail account:

> <p>The Daily Summary</p> JMintheAM.pls jm-in-the-am.sh rename-move.sh sysinfo.sh test.txt test.txt.save wfln1480.pls mg Darwin Kernel Version 8.11.0: Wed Oct 10 18:26:00 PDT 2007; root:xnu-792.24.17~1/RELEASE_PPC ==================================== Uptime: === 15:13 up 1 day, 17:23, 3 users, load averages: 0.00 0.00 0.00 Network: === Local: 192.168.3.131 Hardrive: === Filesystem Size Used Avail Capacity Mounted on /dev/disk1s3 149G 86G 63G 58% /Volumes/Storage Videos: ===

---

### Post by LoneWolfJack on 2009-06-01
doesn't look like you are sending html mails. is the html working for the rest of the email?

---

### Post by Mirge on 2009-06-01
In the mail headers you'll need to send: Content-type: text/plain

That is, I'm assuming it IS sending text/html content type, which would explain the text not retaining its original format.

---

### Post by fragos on 2009-06-01
I get reasonable formating by only using returns at the end of paragraph. You won't have control of line length on the recieving end and this keeps paragraphs looking like paragraphs word wraped to match the recievers line length.

---

### Post by meg23 on 2009-06-01
Its a straight text file. This is what the text file looks like (test.txt):

mg
Darwin Kernel Version 8.11.0: Wed Oct 10 18:26:00 PDT 2007; root:xnu-792.24.17~1/RELEASE_PPC
====================================
 
Uptime: 
=== 
15:13  up 1 day, 17:23, 3 users, load averages: 0.00 0.00 0.00
 
Network:
=== 
Local: 192.168.3.131
 
Hardrive: 
=== 
Filesystem     Size   Used  Avail Capacity  Mounted on
/dev/disk1s3   149G    86G    63G    58%    /Volumes/Storage
 
Videos:
===

This is what I get in my gmail inbox:

The Daily Summary JMintheAM.pls jm-in-the-am.sh rename-move.sh sysinfo.sh test.txt test.txt.save wfln1480.pls mg Darwin Kernel Version 8.11.0: Wed Oct 10 18:26:00 PDT 2007; root:xnu-792.24.17~1/RELEASE_PPC ==================================== Uptime: === 13:10 up 1 day, 15:20, 4 users, load averages: 0.00 0.05 0.19 Network: === Local: 192.168.3.131 Your IP: 71.199.97.183 Common Ports Hardrive: === Filesystem Size Used Avail Capacity Mounted on /dev/disk1s3 149G 86G 63G 58% /Volumes/Storage Videos: ===

Is there anyway to preserve the formatting by reformatting the text using html? The html tags were not recognized by gmail.

---

### Post by aeiah on 2009-06-01
you need to declare a content type. either

Content-Type: text/plain; charset=ISO-8859-1
Content-Transfer-Encoding: 7bit

or 

Content-Type: text/html; charset=ISO-8859-1
Content-Transfer-Encoding: 7bit

should be fine. one is plaintext, the other html. i dont know if the encoding: 7bit lines are necessary.

so, choose which one you want and put it before everything else in your email and see if it helps.

in gmail, when viewing an email, you can use the drop down menu next to reply to choose 'show original'. this will show the sourcecode of the message and might give you a clue as to what you need to include. things like mimetype are probably included by your mailing program automatically.

---

### Post by meg23 on 2009-06-01
I tried adding it to the beginning of the text file but no dice. This is script I use to send the email:
```

echo $(cat -s test.txt) | mailx -s "testing ssmtp setup" me@gmail.com
```

---

### Post by aeiah on 2009-06-01
> **meg23 said:**
> I tried adding it to the beginning of the text file but no dice. This is script I use to send the email:
```

echo $(cat -s test.txt) | mailx -s "testing ssmtp setup" me@gmail.com
```

well im not too sure since ive never used it before. it seems mailx wont do html anyway, unless its been updated. maybe you should just use sendmail like this:

[http://www.unix.com/unix-advanced-expert-users/14177-unable-sent-mail-html-format-mailx-command.html](http://www.unix.com/unix-advanced-expert-users/14177-unable-sent-mail-html-format-mailx-command.html)

---

