---
title: "ggmail"
date: 2008-02-27
forum: Desktop Environments
---

### Post by solarwind on 2008-02-27
Hey all, after asking the Ubuntu community for lots of Python and pyGTK help, I finally got around to finishing my project, ggmail. I don't know where the best place to post this, so I'm posting here.

[SIZE="5"][ggmail Released!]("http://www.blog.solarwind.metafy.org/category/ggmail/")[/SIZE]

> Hey all! I&#8217;m proud to announce the very first release of ggmail (1.0.0 alpha) to the public. ggmail is a free and open source gmail notifier for Linux (soon to be ported to Windows). ggmail is written in 100% Python using the pyGTK/pyGOBJECT libraries and lives in the system tray thanks to the pynotify library. It works by accessing and parsing the gmail atom feed.

> Purpose/How It Works:

    * The purpose of ggmail is to quietly sit in the system tray (Gnome, KDE and others) and check for new gmail email messages every x seconds (specified in the configuration file). When a new email arrives, the icon changes to a red colour and pops up a notification. If the icon stays blue, you don&#8217;t have any new messages. If the icon is green, the program is in the process of checking for new messages.
    * Clicking on the icon (normal left click) will force it to check for new messages.
    * Right clicking on the icon will launch Firefox and bring you to gmail.
    * Middle clicking on the icon will quit the program.
    * Only clicking on the icon invokes an action, clicking on the label does nothing.


Click the link above for all the information relating to this project. What I need right now is a lot of testers. This is the very first release with about two days worth of testing and coding. Linux only at this time. Test it out and tell me how it works! Don't be afraid to say it sucks, but please post constructive feedback, thanks!

---

### Post by solarwind on 2008-02-28
Anyone :P?

---

### Post by tropcky on 2008-02-28
ya bro sure 
 i will test that but what dos  i mean what its jop ?

---

### Post by solarwind on 2008-02-28
> **tropcky said:**
> ya bro sure 
 i will test that but what dos  i mean what its jop ?

It sits in the system tray and checks for gmail emails and notifies you.

---

### Post by tropcky on 2008-02-29
ops 
man i forgat how can install the tar.gz files   send me how plez

---

### Post by kellemes on 2008-02-29
Works pretty fine, good job.

---

### Post by themtx on 2008-02-29
Nice work!  Thanks for sharing.

---

### Post by johnnylavah on 2008-02-29
pretty cool!

---

### Post by tropcky on 2008-02-29
still no body wanna tell how to install the tar.gz ?
  come on guys i need thees application

---

### Post by solarwind on 2008-02-29
I'm only 17 years old so I didn't have time to make a proper tar.gz package or a deb file so I just made a *very* simple bash script installer. There are FULL instructions on the website on how to install: [http://www.blog.solarwind.metafy.org/2008/02/27/ggmail-100-alpha-released/](http://www.blog.solarwind.metafy.org/2008/02/27/ggmail-100-alpha-released/)

Thanks for the positive feedback guys!

Note: the only critical bug as of now is that it has the possibility to crash and not check for new messages if the internet connection times out during the time of checking. I'm working hard to fix this bug. Once that's fixed, I'll release a beta.

Any new features you guys want? Post them here and I'll try my best to add them in!

---

### Post by kellemes on 2008-03-01
> **solarwind said:**
> I'm only 17 years old so I didn't have time to make a proper tar.gz package or a deb file so I just made a *very* simple bash script installer. There are FULL instructions on the website on how to install: [http://www.blog.solarwind.metafy.org/2008/02/27/ggmail-100-alpha-released/](http://www.blog.solarwind.metafy.org/2008/02/27/ggmail-100-alpha-released/)

Thanks for the positive feedback guys!

Note: the only critical bug as of now is that it has the possibility to crash and not check for new messages if the internet connection times out during the time of checking. I'm working hard to fix this bug. Once that's fixed, I'll release a beta.

Any new features you guys want? Post them here and I'll try my best to add them in!

Well.. 3 things I thought about..
1- I don't feel comfortable typing my username/password in the conf-file.. isn't it possible to have it encrypted or something?
2- When I right-click the icon, the browser comes up but I still need to authenticate myself (the first time), can't this be done automatically?
3- configuration-gui?

---

### Post by solarwind on 2008-03-01
> **kellemes said:**
> Well.. 3 things I thought about..
1- I don't feel comfortable typing my username/password in the conf-file.. isn't it possible to have it encrypted or something?
2- When I right-click the icon, the browser comes up but I still need to authenticate myself (the first time), can't this be done automatically?
3- configuration-gui?

1. Totally understand, I'll try to have the gnome wallet thing manage it.
2. It can, I'll have to figure that out.
3. Sure thing bro.

---

### Post by tropcky on 2008-03-02
need ur help mate i install it and when i run i got thes

tropcky@tropcky-Linux:~$ ggmail.py
/usr/local/bin/ggmail.py:12: RuntimeWarning: Python C API version mismatch for module pytrayicon: This Python has API version 1013, module pytrayicon has version 1012.
  import pytrayicon
Checking mail...
Network error.
Traceback (most recent call last):
  File "/usr/local/bin/ggmail.py", line 151, in <module>
    gmailnotifier = ggmail()
  File "/usr/local/bin/ggmail.py", line 71, in __init__
    self.CheckMail()
  File "/usr/local/bin/ggmail.py", line 85, in CheckMail
    g.refreshInfo()
  File "/opt/ggmail/ggmail_atom.py", line 116, in refreshInfo
    p = sax.parseString(self.sendRequest().read(), self.m)
AttributeError: 'NoneType' object has no attribute 'read'
tropcky@tropcky-Linux:~$

---

### Post by solarwind on 2008-03-02
Just try starting it again.

---

### Post by tropcky on 2008-03-02
> **solarwind said:**
> Just try starting it again.

i tryed and it geves me the same err

---

### Post by solarwind on 2008-03-02
> **tropcky said:**
> i tryed and it geves me the same err

Hmm, sounds like a network error I don't know why it's doing that.

---

### Post by tropcky on 2008-03-02
> **solarwind said:**
> Hmm, sounds like a network error I don't know why it's doing that.

do u know how to fix that

---

### Post by solarwind on 2008-03-02
```
p = sax.parseString(self.sendRequest().read(), self.m)
AttributeError: 'NoneType' object has no attribute 'read'
```

From the traceback above, it seems that self.sendRequest is returning null or None which obviously doesn't have a read() method. I think the request is not getting through to gmail. Try again and post the error again.

---

### Post by tropcky on 2008-03-02
> **solarwind said:**
> ```
p = sax.parseString(self.sendRequest().read(), self.m)
AttributeError: 'NoneType' object has no attribute 'read'
```

From the traceback above, it seems that self.sendRequest is returning null or None which obviously doesn't have a read() method. I think the request is not getting through to gmail. Try again and post the error again.

Network error.
Traceback (most recent call last):
  File "/usr/local/bin/ggmail.py", line 151, in <module>
    gmailnotifier = ggmail()
  File "/usr/local/bin/ggmail.py", line 71, in __init__
    self.CheckMail()
  File "/usr/local/bin/ggmail.py", line 85, in CheckMail
    g.refreshInfo()
  File "/opt/ggmail/ggmail_atom.py", line 116, in refreshInfo
    p = sax.parseString(self.sendRequest().read(), self.m)
AttributeError: 'NoneType' object has no attribute 'read'

---

### Post by solarwind on 2008-03-02
> **tropcky said:**
> Network error.
Traceback (most recent call last):
  File "/usr/local/bin/ggmail.py", line 151, in <module>
    gmailnotifier = ggmail()
  File "/usr/local/bin/ggmail.py", line 71, in __init__
    self.CheckMail()
  File "/usr/local/bin/ggmail.py", line 85, in CheckMail
    g.refreshInfo()
  File "/opt/ggmail/ggmail_atom.py", line 116, in refreshInfo
    p = sax.parseString(self.sendRequest().read(), self.m)
AttributeError: 'NoneType' object has no attribute 'read'

Wow, what a strange error. Type ```
ping mail.google.com
``` in a terminal and post the output. If you get successful pings, press ctrl+c after 4 or 5 pings.

---

### Post by tropcky on 2008-03-02
here iit is 

PING googlemail.l.google.com (72.14.215.83) 56(84) bytes of data.
64 bytes from hu-in-f83.google.com (72.14.215.83): icmp_seq=1 ttl=246 time=301 ms
64 bytes from hu-in-f83.google.com (72.14.215.83): icmp_seq=2 ttl=246 time=261 ms
64 bytes from hu-in-f83.google.com (72.14.215.83): icmp_seq=3 ttl=246 time=253 ms
64 bytes from hu-in-f83.google.com (72.14.215.83): icmp_seq=4 ttl=246 time=306 ms
64 bytes from hu-in-f83.google.com (72.14.215.83): icmp_seq=5 ttl=246 time=264 ms
64 bytes from hu-in-f83.google.com (72.14.215.83): icmp_seq=6 ttl=246 time=296 ms
64 bytes from hu-in-f83.google.com (72.14.215.83): icmp_seq=7 ttl=246 time=259 ms

--- googlemail.l.google.com ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 7270ms
rtt min/avg/max/mdev = 253.754/277.556/306.678/21.207 ms

---

### Post by solarwind on 2008-03-02
Ok this is very very weird. Sorry for the bugs, lol. Attempting to fix now. I'll post as soon as I make some progress.

---

### Post by tropcky on 2008-03-02
> **solarwind said:**
> Ok this is very very weird. Sorry for the bugs, lol. Attempting to fix now. I'll post as soon as I make some progress.

no worry man evry grate programs have bugs   and nice work 
i will be waiting

---

### Post by solarwind on 2008-03-02
> **tropcky said:**
> no worry man evry grate programs have bugs   and nice work 
i will be waiting

Ok, I think I fixed your problem! New version of ggmail released!

[http://www.blog.solarwind.metafy.org/2008/03/02/ggmail-110-alpha-released/](http://www.blog.solarwind.metafy.org/2008/03/02/ggmail-110-alpha-released/)

Please read through that page.

---

### Post by solarwind on 2008-03-02
New version released. Fixed many bugs. ggmail is now very very reliable. Enjoy!

---

### Post by tropcky on 2008-03-02
i tryed the new one and still the same problem 

tropcky@tropcky-Linux:~$ ggmail.py
/usr/local/bin/ggmail.py:12: RuntimeWarning: Python C API version mismatch for module pytrayicon: This Python has API version 1013, module pytrayicon has version 1012.
  import pytrayicon
Checking mail...
Network error.
Traceback (most recent call last):
  File "/usr/local/bin/ggmail.py", line 151, in <module>
    gmailnotifier = ggmail()
  File "/usr/local/bin/ggmail.py", line 71, in __init__
    self.CheckMail()
  File "/usr/local/bin/ggmail.py", line 85, in CheckMail
    g.refreshInfo()
  File "/opt/ggmail/ggmail_atom.py", line 116, in refreshInfo
    p = sax.parseString(self.sendRequest().read(), self.m)
AttributeError: 'NoneType' object has no attribute 'read'
tropcky@tropcky-Linux:~$ In The Name Of The King R5 Xvid

---

### Post by solarwind on 2008-03-02
> **tropcky said:**
> i tryed the new one and still the same problem 

tropcky@tropcky-Linux:~$ ggmail.py
/usr/local/bin/ggmail.py:12: RuntimeWarning: Python C API version mismatch for module pytrayicon: This Python has API version 1013, module pytrayicon has version 1012.
  import pytrayicon
Checking mail...
Network error.
Traceback (most recent call last):
  File "/usr/local/bin/ggmail.py", line 151, in <module>
    gmailnotifier = ggmail()
  File "/usr/local/bin/ggmail.py", line 71, in __init__
    self.CheckMail()
  File "/usr/local/bin/ggmail.py", line 85, in CheckMail
    g.refreshInfo()
  File "/opt/ggmail/ggmail_atom.py", line 116, in refreshInfo
    p = sax.parseString(self.sendRequest().read(), self.m)
AttributeError: 'NoneType' object has no attribute 'read'
tropcky@tropcky-Linux:~$ In The Name Of The King R5 Xvid

No no, you're still running the old version. The new version doesn't use the sax parser.

Type this in the terminal:

```
sudo rm -rf /opt/ggmail
``` This will delete the old installation.
Then run the install.py script from the latest version to install again.

---

### Post by tropcky on 2008-03-02
> **solarwind said:**
> No no, you're still running the old version. The new version doesn't use the sax parser.

Type this in the terminal:

```
sudo rm -rf /opt/ggmail
``` This will delete the old installation.
Then run the install.py script from the latest version to install again.

body ther is no install.py  in the ggmail_2008-03-02_15h_08m_12s.tar.bz  files

---

### Post by solarwind on 2008-03-02
> **tropcky said:**
> body ther is no install.py  in the ggmail_2008-03-02_15h_08m_12s.tar.bz  files

OOps, totally my mistake. Forgot to include it... Here's the new download with the install.py included and some other minor fixes:

[http://www.mediafire.com/?wz9aeimdmbg](http://www.mediafire.com/?wz9aeimdmbg)

---

### Post by h3rt3q on 2008-03-02
i got the same error..

```
jack@cunet:~/Documents/ggmail$ ./ggmail.py 
./ggmail.py:13: RuntimeWarning: Python C API version mismatch for module pytrayicon: This Python has API version 1013, module pytrayicon has version 1012.
  import pytrayicon
No credentials have been set.
jack@cunet:~/Documents/ggmail$
```

yup.. no install.py

---

### Post by solarwind on 2008-03-02
Yea, just noticed I didn't include install.py in the latest release.

Here's the latest release with all needed files: [http://www.mediafire.com/?wz9aeimdmbg](http://www.mediafire.com/?wz9aeimdmbg)

You HAVE to run install.py so as to properly install the program and to set account credentials.

---

### Post by solarwind on 2008-03-03
> **tropcky said:**
> body ther is no install.py  in the ggmail_2008-03-02_15h_08m_12s.tar.bz  files

Dude, that's a really nice dark theme in your screenshot. Where did you get it?

---

### Post by tropcky on 2008-03-03
nice work my frend   it works so much fine now and i liked it  

keep working

---

### Post by solarwind on 2008-03-03
> **tropcky said:**
> nice work my frend   it works so much fine now and i liked it  

keep working

No problem! If you guys want any new features added, just post here!

---

### Post by h3rt3q on 2008-03-03
i think theres bug on your ggmail project.

my gmail password has a "@" character on it.
turns out ggmail connection error..

```

jack@cunet:~/Documents/ggmail$ ./ggmail.py
./ggmail.py:13: RuntimeWarning: Python C API version mismatch for module pytrayicon: This Python has API version 1013, module pytrayicon has version 1012.
  import pytrayicon
Checking mail...
--13:05:07--  https://myusername:*password*@aRREov3%40mail.google.com/mail/feed/atom/unread
           => `-'
Resolving @aRREov3@mail.google.com... failed: Name or service not known.
Done. New messages: -1 Checked in 1.142993927 s. Last checked: 2008-03-03 13:05:07

```

**sorry i changed my username..*

---

### Post by tropcky on 2008-03-03
> **solarwind said:**
> Dude, that's a really nice dark theme in your screenshot. Where did you get it?

here it is

---

### Post by tropcky on 2008-03-03
sorry forgat the icons themes here it is

---

### Post by solarwind on 2008-03-03
> **h3rt3q said:**
> i think theres bug on your ggmail project.

my gmail password has a "@" character on it.
turns out ggmail connection error..

```

jack@cunet:~/Documents/ggmail$ ./ggmail.py
./ggmail.py:13: RuntimeWarning: Python C API version mismatch for module pytrayicon: This Python has API version 1013, module pytrayicon has version 1012.
  import pytrayicon
Checking mail...
--13:05:07--  https://myusername:*password*@aRREov3%40mail.google.com/mail/feed/atom/unread
           => `-'
Resolving @aRREov3@mail.google.com... failed: Name or service not known.
Done. New messages: -1 Checked in 1.142993927 s. Last checked: 2008-03-03 13:05:07

```

**sorry i changed my username..*

LllllllOL! It's not a bug in my program. ggmail uses wget as a backend to fetch the atom feed to check for mail. As you can see, there are two @ symbols in the wget line and wget doesn't know how to handle that. Simple solution.

Download fixed version here: [http://www.mediafire.com/?d3mzujddp2p](http://www.mediafire.com/?d3mzujddp2p)

Thanks for the bug reports guys! You're really helping me improve this program! Tell me if the fix works!

---

### Post by solarwind on 2008-03-03
> **tropcky said:**
> sorry forgat the icons themes here it is

Thanks!

---

### Post by tropcky on 2008-03-03
> **solarwind said:**
> Thanks!

dem sorry i will upload it hold on 
i think it dosnt want to upload cus its so big   
the ferst one caold 
GnomeElephant-SavaneFree
and the second one 
GnomeElephant-Marine

u gonna faind it in 
gnome-look.org

---

### Post by solarwind on 2008-03-03
> **tropcky said:**
> dem sorry i will upload it hold on 
i think it dosnt want to upload cus its so big   
the ferst one caold 
GnomeElephant-SavaneFree
and the second one 
GnomeElephant-Marine

u gonna faind it in 
gnome-look.org

Yep, got it, thanks!

---

### Post by h3rt3q on 2008-03-03
still no luck solarwind...

```

jack@cunet:~/Documents/ggmail$ sudo rm -rf /opt/ggmail/
jack@cunet:~/Documents/ggmail$ clear

jack@cunet:~/Documents/ggmail$ ./install.py 
Installing ggmail...
Username: myusername
Password: 
Done.
jack@cunet:~/Documents/ggmail$ ./ggmail
bash: ./ggmail: No such file or directory
jack@cunet:~/Documents/ggmail$ ./ggmail.py
./ggmail.py:13: RuntimeWarning: Python C API version mismatch for module pytrayicon: This Python has API version 1013, module pytrayicon has version 1012.
  import pytrayicon
Checking mail...
wget -O - https://"myusername":"@aRREov3"@mail.google.com/mail/feed/atom/unread --no-check-certificate --server-response --timeout=10 --tries=3
--13:25:22--  https://myusername:*password*@arreov3%40mail.google.com/mail/feed/atom/unread
           => `-'
Resolving arreov3@mail.google.com... failed: Name or service not known.
Done. New messages: -1 Checked in 0.434072971344 s. Last checked: 2008-03-03 13:25:22

```

:(

---

### Post by solarwind on 2008-03-03
> **h3rt3q said:**
> still no luck solarwind...

```

jack@cunet:~/Documents/ggmail$ sudo rm -rf /opt/ggmail/
jack@cunet:~/Documents/ggmail$ clear

jack@cunet:~/Documents/ggmail$ ./install.py 
Installing ggmail...
Username: myusername
Password: 
Done.
jack@cunet:~/Documents/ggmail$ ./ggmail
bash: ./ggmail: No such file or directory
jack@cunet:~/Documents/ggmail$ ./ggmail.py
./ggmail.py:13: RuntimeWarning: Python C API version mismatch for module pytrayicon: This Python has API version 1013, module pytrayicon has version 1012.
  import pytrayicon
Checking mail...
wget -O - https://"myusername":"*password*"@mail.google.com/mail/feed/atom/unread --no-check-certificate --server-response --timeout=10 --tries=3
--13:25:22--  https://myusername:*password*@arreov3%40mail.google.com/mail/feed/atom/unread
           => `-'
Resolving arreov3@mail.google.com... failed: Name or service not known.
Done. New messages: -1 Checked in 0.434072971344 s. Last checked: 2008-03-03 13:25:22

```

:(

**Check your private messages NOW**. Hmm, this is odd. I think the only thing I can recommend to you right now is get rid of the @ character in your password. It's really not necessary and ggmail will work if you remove that character. The @ character is a trouble maker because it's part of the email address which separates the user name from the domain. Having it in your pass just confuses wget and I honestly don't know how to fix this. I'm trying my best to find a solution. But, again, the only thing I can recommend is removing the @ char from your pass and changing it to something else.

---

### Post by h3rt3q on 2008-03-03
> **solarwind said:**
> **Check your private messages NOW**. Hmm, this is odd. I think the only thing I can recommend to you right now is get rid of the @ character in your password. It's really not necessary and ggmail will work if you remove that character. The @ character is a trouble maker because it's part of the email address which separates the user name from the domain. Having it in your pass just confuses wget and I honestly don't know how to fix this. I'm trying my best to find a solution. But, again, the only thing I can recommend is removing the @ char from your pass and changing it to something else.

thx again for the prvate alert.
remove my @ in the password?
dont u think software developer should come with a program that meets the user requirement?
what if there is 10,000 people like me (having an @ in the passwd), and they like your program. do you think all will change their password?
or will they find another similiar program?

:confused:

---

### Post by solarwind on 2008-03-03
> **h3rt3q said:**
> thx again for the prvate alert.
remove my @ in the password?
dont u think software developer should come with a program that meets the user requirement?
what if there is 10,000 people like me (having an @ in the passwd), and they like your program. do you think all will change their password?
or will they find another similiar program?

:confused:

Hey, I'm 17 years old... come on, lol :P I program in my spare time as a hobby.

Alright alright, here's another attempt to fix... [http://www.mediafire.com/?edgym01mytj](http://www.mediafire.com/?edgym01mytj)

I hope this one works!

---

### Post by h3rt3q on 2008-03-03
> **solarwind said:**
> Hey, I'm 17 years old... come on, lol :P I program in my spare time as a hobby.

Alright alright, here's another attempt to fix... [http://www.mediafire.com/?edgym01mytj](http://www.mediafire.com/?edgym01mytj)

I hope this one works!

```
yay it worked!!

jack@cunet:~/Documents/ggmail$ ./ggmail.py 
./ggmail.py:13: RuntimeWarning: Python C API version mismatch for module pytrayicon: This Python has API version 1013, module pytrayicon has version 1012.
  import pytrayicon
Checking mail...
--13:49:57--  https://myusername@mail.google.com/mail/feed/atom/unread
           => `-'
Resolving mail.google.com... 209.85.143.18, 209.85.143.83, 209.85.143.19
Connecting to mail.google.com|209.85.143.18|:443... connected.
HTTP request sent, awaiting response... Read error (Connection timed out) in headers.
Retrying.

--13:50:08--  https://myusername@mail.google.com/mail/feed/atom/unread
  (try: 2) => `-'
Connecting to mail.google.com|209.85.143.18|:443... connected.
HTTP request sent, awaiting response... 
  HTTP/1.0 200 OK
  Set-Cookie: S=gmail=yToPQfPJBz0XZBsdhkqertgFnBg:gmail_yj=FmZCVf5PteplTSTfA:gmproxy=teYOBgeTrks:gmproxy_yj=OYEo9D3baK8:gmproxy_yj_sub=WBkMJj0OSnQ; Path=/mail
  Content-Type: text/xml; charset=UTF-8
  Cache-control: private
  Server: GFE/1.3
  Date: Mon, 03 Mar 2008 05:50:08 GMT
  Connection: Close
Length: unspecified [text/xml]

    [ <=>                                 ] 2,110         --.--K/s             

13:50:09 (11.54 MB/s) - `-' saved [2110]

Done. New messages: 3 Checked in 12.6411800385 s. Last checked: 2008-03-03 13:49:57
```

only that it get connection error after 60secs. another job for you!

---

### Post by solarwind on 2008-03-03
> **h3rt3q said:**
> ```
yay it worked!!

jack@cunet:~/Documents/ggmail$ ./ggmail.py 
./ggmail.py:13: RuntimeWarning: Python C API version mismatch for module pytrayicon: This Python has API version 1013, module pytrayicon has version 1012.
  import pytrayicon
Checking mail...
--13:49:57--  https://myusername@mail.google.com/mail/feed/atom/unread
           => `-'
Resolving mail.google.com... 209.85.143.18, 209.85.143.83, 209.85.143.19
Connecting to mail.google.com|209.85.143.18|:443... connected.
HTTP request sent, awaiting response... Read error (Connection timed out) in headers.
Retrying.

--13:50:08--  https://myusername@mail.google.com/mail/feed/atom/unread
  (try: 2) => `-'
Connecting to mail.google.com|209.85.143.18|:443... connected.
HTTP request sent, awaiting response... 
  HTTP/1.0 200 OK
  Set-Cookie: S=gmail=yToPQfPJBz0XZBsdhkqertgFnBg:gmail_yj=FmZCVf5PteplTSTfA:gmproxy=teYOBgeTrks:gmproxy_yj=OYEo9D3baK8:gmproxy_yj_sub=WBkMJj0OSnQ; Path=/mail
  Content-Type: text/xml; charset=UTF-8
  Cache-control: private
  Server: GFE/1.3
  Date: Mon, 03 Mar 2008 05:50:08 GMT
  Connection: Close
Length: unspecified [text/xml]

    [ <=>                                 ] 2,110         --.--K/s             

13:50:09 (11.54 MB/s) - `-' saved [2110]

Done. New messages: 3 Checked in 12.6411800385 s. Last checked: 2008-03-03 13:49:57
```

only that it get connection error after 60secs. another job for you!

Hmm, do you have a slow internet connection? If so, you can change the timeout options in the wget line in ggmail.py. If you have a pretty fast connection, you can leave it alone. ggmail has protection for getting stuck up and will kill a check process if it takes longer than 10 seconds and will retry 3 times. You can easily change this.

Also not a good idea to expose the Set-cookie line as anyone can use it to get into your gmail account... I just enabled all these things to debug, forgot to turn them off for releases...

---

### Post by solarwind on 2008-03-03
```
sudo gedit /opt/ggmail/ggmail.py
```

Search for (ctrl + f) "com =" without the quotes. That's the line that tells wget to fetch the atom feeds.

That line will look like this:
```
com = "wget -O - https://\"" + u + "\"@mail.google.com/mail/feed/atom/unread --no-check-certificate --server-response --timeout=10 --tries=3 --password=\"" + p + "\""
```

Try changing it to this:
```
com = "wget -O - https://\"" + u + "\"@mail.google.com/mail/feed/atom/unread --no-check-certificate --server-response --timeout=25 --tries=2 --password=\"" + p + "\""
```

Save and restart ggmail. Tell me how it goes!

---

### Post by h3rt3q on 2008-03-03
> **solarwind said:**
> Hmm, do you have a slow internet connection? If so, you can change the timeout options in the wget line in ggmail.py. If you have a pretty fast connection, you can leave it alone. ggmail has protection for getting stuck up and will kill a check process if it takes longer than 10 seconds and will retry 3 times. You can easily change this.

Also not a good idea to expose the Set-cookie line as anyone can use it to get into your gmail account... I just enabled all these things to debug, forgot to turn them off for releases...

yup the internet connection here in malaysia is very2 slow... i wish i had a good internet connection like you. i think adding some more delay will fix it.

dont worry about the cookies, i also edited them by pressing my keyboard randomly. thought of that earlier.

anyway thanks!

Best Of Luck,
Adam

---

### Post by solarwind on 2008-03-03
> **h3rt3q said:**
> yup the internet connection here in malaysia is very2 slow... i wish i had a good internet connection like you. i think adding some more delay will fix it.

dont worry about the cookies, i also edited them by pressing my keyboard randomly. thought of that earlier.

anyway thanks!

Best Of Luck,
Adam

Yep, if it's your internet, changing the timeout, as I described above, will work for sure! Thanks for the feedback dude! You helped make this program better!

---

### Post by nanotube on 2008-03-03
hey solarwind, good stuff here

just a couple of suggestions

first, if you are going to have this project and make more releases, i suggest you set it up on sourceforge. it will give you the development and hosting infrastructure (like file release servers, CVS or SVN, website, forums, mailing lists, etc. ) and give people a place to file bug reports 

second, instead of using wget, look into using some native python libraries (eg urllib2). if you can't solve the @password issue with wget...

---

### Post by bharadwaj on 2008-03-03
Can any one tell me the addvantages of this one over gTalk or Gmail notifier ?

---

### Post by tropcky on 2008-03-03
u know solarwind i wanna tell u some thing will make thes program the best 
try to make play vois u know when a new mail comes it plays ( u have a new mail ) or any sound  

think about it

---

### Post by solarwind on 2008-03-03
> **nanotube said:**
> hey solarwind, good stuff here

just a couple of suggestions

first, if you are going to have this project and make more releases, i suggest you set it up on sourceforge. it will give you the development and hosting infrastructure (like file release servers, CVS or SVN, website, forums, mailing lists, etc. ) and give people a place to file bug reports 

second, instead of using wget, look into using some native python libraries (eg urllib2). if you can't solve the @password issue with wget...

1. I already registered it on sourceforge but I hate their interface, lol. I have my own webhost that's a million times better. I'll just set up trac on my host and do it that way.

2. The first release used urllib2 but I absolutely hate it. I don't know why. But please tell me, why is it a better idea to use urllib2 over wget? By the way, I solved the @ character in the password issue by passing the password to wget as an option. Simple fix. But if there's still an advantage to using urllib2, please post and I'll try using it over wget.

> **bharadwaj said:**
> Can any one tell me the addvantages of this one over gTalk or Gmail notifier ?

Lol, I guess you'll just have to try it and find out ;) Please post if you want features added!

> **tropcky said:**
> u know solarwind i wanna tell u some thing will make thes program the best 
try to make play vois u know when a new mail comes it plays ( u have a new mail ) or any sound  

think about it

No problem at all! Playing sounds in Python is trivial. Will be included in the next release for sure. Anyone have any ideas for a sound that could be included? Please upload the wav/ogg/mp3/whatever file and I'll add it in. I'm not good with picking out sounds :P

---

### Post by christhemonkey on 2008-03-03
A reason why to use urllib2 over wget, ease of portability?

(although wget is available on windows, urllib2 would be included with python)

---

### Post by solarwind on 2008-03-03
> **christhemonkey said:**
> A reason why to use urllib2 over wget, ease of portability?

(although wget is available on windows, urllib2 would be included with python)

Right now, I have no plan to port this to winbloze and almost all unix systems have wget. I'll have to look at this urllib anyway...

---

### Post by christhemonkey on 2008-03-03
My apologies then, thought this:
> soon to be ported to Windows
sort of implied that you were planning to port it.

Also if you dont like urllib2, you can use urllib or httplib instead.

---

### Post by nanotube on 2008-03-03
> **solarwind said:**
> Right now, I have no plan to port this to winbloze and almost all unix systems have wget. I'll have to look at this urllib anyway...

well, if you're not planning on porting it to anywhere that may not have wget on it, then it really doesn't matter. if you can get wget to do everything you want it to, no reason to rewrite your code.

about sourceforge - its interface is indeed a bit clunky, but at least you can use it for CVS (or SVN) service. that will let others see the progress of your code, allow for easy collaboration, and give you easy access to older versions of your code (what did i do to introduce such-and-such bug?) even if you don't use sf.net, set up your own cvs on your webhost. version control systems are just cool. :) 

speaking of portability... you use "pytrayicon.so" in your code, but i couldn't find the source code to this file. do you have the source, or can you point me to where i can get a look at it? weird binary-only files in software make me wary :)

---

### Post by solarwind on 2008-03-08
1.2.0 beta released! Many fixes! Also got google code project page! Check it out: [http://code.google.com/p/ggmail/](http://code.google.com/p/ggmail/)

---

### Post by tropcky on 2008-03-08
hi i think we have to remove the ferst one fesrt   how i do that ???

---

### Post by solarwind on 2008-03-08
> **tropcky said:**
> hi i think we have to remove the ferst one fesrt   how i do that ???

Just type this in the terminal:

```
sudo rm -rf /opt/ggmail
``` That's all you need to do.

---

### Post by tropcky on 2008-03-08
thank u  it works now

---

### Post by solarwind on 2008-03-10
Anytime! New version released, check it out. Next version will have more configurability, ability to notify via sound and a GUI tool to configure!

---

### Post by solarwind on 2008-03-10
Check out the 2.0.0 release plans! Lots of new upcoming features! [http://www.blog.solarwind.metafy.org/2008/03/10/ggmail-130-final-release-plans/](http://www.blog.solarwind.metafy.org/2008/03/10/ggmail-130-final-release-plans/)

---

### Post by tropcky on 2008-03-10
bro wher is the download link ?

---

### Post by solarwind on 2008-03-10
Version 2.0.0 isn't released yet. All releases will be made on the google code website: [http://code.google.com/p/ggmail/downloads/list](http://code.google.com/p/ggmail/downloads/list) The latest version is 1.2.0 beta.

---

### Post by solarwind on 2008-05-10
Version 1.3.0 released.

---

