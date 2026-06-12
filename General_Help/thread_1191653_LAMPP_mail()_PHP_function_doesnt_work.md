---
title: "LAMPP mail() PHP function doesnt work"
date: 2009-06-19
forum: General Help
---

### Post by psicloone on 2009-06-19
I`ve installed LAMPP server on UBUNTU.

I`m trying to send email to a gmail account, using the mail php function:

[COLOR=#000000][COLOR=#0000BB]mail[/COLOR][COLOR=#007700]([/COLOR][COLOR=#DD0000]'whatever@gmail.com'[/COLOR][COLOR=#007700], [/COLOR][COLOR=#DD0000]'My Subject'[/COLOR][COLOR=#007700], [/COLOR][COLOR=#0000BB]$message[/COLOR][COLOR=#007700]);[/COLOR][/COLOR]

but no message arrives in the email address.


What could be the problem?

---

### Post by bobtfish on 2009-06-19
Checking on mine it doesn't seem like the mail tools are there by default or installed by the LAMP server. Try "mail" and "mailx" on the command line, see if it tells you they aren't there. In Synaptic, if you go to Edit -> Mark packages by task, you can select Mail server, although I think that gives more than you really need. After that, good luck, I had a hell of a time getting it to work through php myself.

---

### Post by psicloone on 2009-06-19
When I type mail or mailx it says

The program 'mail' can be found in the following packages: 

 * heirloom-mailx
 * mailutils

---

### Post by bobtfish on 2009-06-19
Sorry, the program required seems to be "sendmail", but again I would expect running that from the command line will give you the same "The program sendmail can be found in the following... etc" meaning you don't have it.
I was going to recommend installing the Mail Server through Synaptic, but having tried that, I now can't get it to work... *head*<=>*wall*
I will get back to you when I stop being an idiot.

---

### Post by zadehas on 2009-06-19
You need to install a mail server in order for the mail function to work.
Postfix will do just fine.

```
sudo apt-get install postfix
```

Of course, you might need some extra config if you are behind a router or firewall etc, otherwise it should work out of the box.

---

### Post by psicloone on 2009-06-19
I installed Postfix. When i type mail in the terminal, I get:


kb@kb:~$ mail
No mail for kb
kb@kb:~$ 

which mean that my mail server should work. My PHP script for the email form uses this code to send the mail:


mail($email_address, $subject, $message, "From: yoursite.com Webmaster<admin@jyoursite.com>\n 
        X-Mailer: PHP/" . phpversion()); 


I opened php.ini and comented Win32 and removed the comment before UNIX and typed:    /usr/sbin/sendmail -i -t


[mail function]
; For Win32 only.
;SMTP = localhost

; For Win32 only.
;sendmail_from = [email]me@localhost.com[/email]

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
sendmail_path = sendmail_path = /usr/sbin/sendmail -i -t


Then I restarted the server and tried again - it didn`t work...

---

### Post by zadehas on 2009-06-21
After installing postfix, do this:
```
sudo /etc/init.d/postfix start
```
to make sure postfix is running.

You might want to also try 
```
sudo apt-get install nmap
```

and then 
```
nmap localhost
```

to see whether port 25 is open.

Leave php.ini to default values, you don't need to supply any sendmail path or parameters, at least not at this point.

If postfix is running, then your script should send the message to the mail server. However, you should bear in mind that this doesn't mean that the email will get through to your destination, it simply means that it has been handed over to the mail server.

---

### Post by Thyme on 2009-06-21
Try sending an email from the command line to ensure that you actually can send mail from your box:

sendmail -t
TO:to@example.com
FROM:from@example.com
SUBJECT:testing send mail
mail body
<control_D>

See if it's in the queue: mailq

Check the mail log, you should see "status=sent" if everything went ok: tail -n 25 /var/log/mail.log

As zadehas said, you should not need to modify the mail settings in the default php.ini.

---

### Post by psicloone on 2009-06-21
It` working with telnet - I sent letter to gmail.

But that:

[COLOR=Green]sendmail -t
TO:to@example.com
FROM:from@example.com
SUBJECT:testing send mail
mail body
<control_D>[/COLOR]

didn`t work with localhost sender.

[COLOR=Red]IT WORKER WHEN I TYPED MY IP AS SENDER.[/COLOR]

When I type:

nmap localhost
it shows:

Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-06-21 14:03 EEST
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Stats: 0:00:00 elapsed; 0 hosts completed (0 up), 0 undergoing Ping Scan
Ping Scan Timing: About 100.00% done; ETC: 14:03 (0:00:00 remaining)
Interesting ports on localhost (127.0.0.1):
Not shown: 995 closed ports
PORT    STATE SERVICE
21/tcp  open  ftp
25/tcp  open  smtp
80/tcp  open  http
443/tcp open  https
631/tcp open  ipp

Nmap done: 1 IP address (1 host up) scanned in 0.41 seconds

---

### Post by psicloone on 2009-06-21
kb@kb:~$ mailq
-Queue ID- --Size-- ----Arrival Time---- -Sender/Recipient-------
A68E16582FF*     319 Sun Jun 21 13:53:53  [email]kb@mail.localh[/email]ost
                                         [email]xavelus@example.com[/email]

---

### Post by zadehas on 2009-06-21
Looks to me like the mail() function is working, it sends the message to the mail server, from this point on is the job of the mail server to deliver the message.

Did you try to send a mail to an external address (like gmail, yahoo, etc)? Does it work?

---

