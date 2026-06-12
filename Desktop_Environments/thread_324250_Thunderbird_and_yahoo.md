---
title: "Thunderbird and yahoo"
date: 2006-12-23
forum: Desktop Environments
---

### Post by hraposo on 2006-12-23
Who knows configure thunderbird to receive mails from yahoo beta mail?

---

### Post by Warbo on 2006-12-23
I personally use FetchYahoo to screenscrape my Yahoo emails every 15 minutes (using CRON, which I set up with GNOME-Schedule from Universe) and dump them into Mbox files in a hidden folder in my Home. I then use Evolution (but you could use Thunderbird) to read them.

Problems with this are: 1) I can't send emails from Evolution, I need to log in to Yahoo's webmail 2) FetchYahoo doesn't work with the new beta interface, so I keep Yahoo on the older interface (which suits me better anyway, as the new interface is completely unusable for me [white fonts on a white background])

Hope that gives you a direction in your research :)

PS: I think you may need to get the latest fetchyahoo script from fetchyahoo.sourceforge.net because the one in Ubuntu doesn't work anymore

---

### Post by hraposo on 2006-12-23
In thunderbird I configure one yahoo account but when the thunderbird goes to download the mails appears:
negative vibes from [email]hldraposo@yahoo.com[/email] What this mean?

---

### Post by Warbo on 2006-12-23
I only use my overly-complicated system because I am using the free Yahoo webmail. If you are using the paid-for POP3 access and have a problem, then sorry that is out of my depth :(

---

### Post by paparucino on 2006-12-23
> **hraposo said:**
> In thunderbird I configure one yahoo account but when the thunderbird goes to download the mails appears:
negative vibes from [email]hldraposo@yahoo.com[/email] What this mean?
I can suggest Gmail (the mail service from google). It's free and allows you to retry/write mails with your preferred mailreader.

---

### Post by AmandaKerik on 2007-02-01
There's an easy way to get your yahoo and even hotmail emails into Thunderbird - [http://webmail.mozdev.org/](http://webmail.mozdev.org/)
It's easy to set up, fast to use... just follow the instructions on the site!
I also find it vastly easier to use compared to ypops.

Hope this helps,
Amanda

---

### Post by nm newbie on 2007-05-01
i have tried to install the webmail (thunderbird 1.5), but when i do, i get the message that it is not a valid package. the files are on my desktop as per the instructions on their forum. what am i doing wrong? any help would be greatly appreciated. using feisty fawn.  thanks

---

### Post by nanotube on 2007-05-03
doesn't yahoo provide pop access nowadays?

---

### Post by nanotube on 2007-05-03
> **nm newbie said:**
> i have tried to install the webmail (thunderbird 1.5), but when i do, i get the message that it is not a valid package. the files are on my desktop as per the instructions on their forum. what am i doing wrong? any help would be greatly appreciated. using feisty fawn.  thanks

i had no problems with webmail extension (for hotmail) on tb2.0. maybe you should [upgrade]("http://ubuntuforums.org/forumdisplay.php?f=251")? :)

---

### Post by Depressed Man on 2007-05-31
I have problems but it seems with localhost. No matter what port I pick for the webmail extension it won't switch to a green light.

---

### Post by nanotube on 2007-05-31
> **Depressed Man said:**
> I have problems but it seems with localhost. No matter what port I pick for the webmail extension it won't switch to a green light.

what ports have you tried? you have to have a port higher than 1024, and also not taken up by anything else listening (you can check with command "netstat -plantu" )
i have it running on port 4000, e.g.

---

### Post by jrusso2 on 2007-05-31
I can't get the webmail or the hotmail plugin working.  Will not connect to localhost and it won't let me change the ports.

---

### Post by Depressed Man on 2007-05-31
I've tried 1100,4000,2500, and any other # I could randomly generate for about 3 minutes. 

Though the problem itself may be localhost? Pinging localhost seems to take forever.. 

Also my terminal reads.

username@localhost:~$ 

Is that normal?

---

### Post by jazzman84116 on 2007-05-31
I use Free pops to acces my Yahoo Mail  Localhost Port 2000

---

