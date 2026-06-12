---
title: "Python and cron"
date: 2009-03-10
forum: General Help
---

### Post by blairm on 2009-03-10
Hi,

Have a python script that works when run from the shell but won't when run by cron. The script checks an rss feed and emails a list of headlines, links and first paragraphs.
I'm aware this is a pretty common problem but after a fair bit of reading have been unable to solve it; it seems the most common error is not fully qualifying the path, but thought I had done that. I have tried various changes to it to no avail.
The output of crontab -l is:

```
PATH=/usr/sbin:/usr/bin:/sbin:/bin
* * * * * python /home/usr/bin/Documents/messinground.py

```
 
The system log shows the following every minute:

```
2009-03-11 10:49:01	orpheus	/USR/SBIN/CRON[14006]	(blairm) CMD (python /home/usr/bin/Documents/messinground.py)
2009-03-11 10:49:01	orpheus	sSMTP[14008]	Unable to locate mail
2009-03-11 10:49:01	orpheus	sSMTP[14008]	Cannot open mail:25
2009-03-11 10:49:01	orpheus	/USR/SBIN/CRON[13999]	(blairm) MAIL (mailed 103 bytes of output but got status 0x0001 )

```  

There appears to be no mail for root or blairm.

If it's relevant, the script I'm trying to run is below (yes, I'm aware the md5 is a little redundant where it is at the moment; figured I'd try to get the script running via cron before tackling comparisons):

```
#! /usr/bin/env python

import urllib
import sys
import xml.dom.minidom
import hashlib
import os


#The url of the feed
address = 'http://www.stuff.co.nz/rss/national'

#Our actual xml document
f = open('alerttest.txt.tmp',  'w')

document = xml.dom.minidom.parse(urllib.urlopen(address))
for item in document.getElementsByTagName('item'):
    title = item.getElementsByTagName('title')[0].firstChild.data
    link = item.getElementsByTagName('link')[0].firstChild.data
    description = item.getElementsByTagName('description')[0].firstChild.data
    
    print>>f,  '"%s" %s (%s)''' % (link.encode('UTF8', 'replace'),
                                            title.encode('UTF8','replace'),
                                            description.encode('UTF8','replace'))
    

orig_md5= hashlib.md5(file('alerttest.txt').read())
new_md5= hashlib.md5(file('alerttest.txt.tmp').read())

if orig_md5.digest() ==new_md5.digest():
    os.remove('alerttest.txt.tmp')
    #exit or something
    sys.exit()
    
    
else:
    os.rename('alerttest.txt.tmp',  'alerttest.txt')
f.close()

import smtplib

# from http://stackoverflow.com/questions/399129/failing-to-send-email-with-the-python-example
FROMADDR = "my.address@gmail.com"
LOGIN    = FROMADDR
PASSWORD = "mypassword"
TOADDRS  = ["my.address@xtra.co.nz"]
SUBJECT  = "Test alert"

msg = ("From: %s\r\nTo: %s\r\nSubject: %s\r\n\r\n"
       % (FROMADDR, ", ".join(TOADDRS), SUBJECT) )
msg += open('alerttest.txt', 'r').read()

server = smtplib.SMTP('smtp.gmail.com', 587)
server.set_debuglevel(1)
server.ehlo()
server.starttls()
server.login(LOGIN, PASSWORD)
server.sendmail(FROMADDR, TOADDRS, msg)
server.quit()

  

```

Any advice gratefully received!

Blair

---

