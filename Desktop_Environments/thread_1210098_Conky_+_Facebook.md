---
title: "Conky + Facebook"
date: 2009-07-11
forum: Desktop Environments
---

### Post by sdlynx on 2009-07-11
Hey,

Does anybody know if I can get conky to show how many facebook notifications I have?

Thanks,
sdlynx

---

### Post by gighsmighly on 2009-09-01
I guess no one really responded.. sory dood

[http://kudanai.blogspot.com/2009/07/facebook-inbox-count-for-conkyothers.html](http://kudanai.blogspot.com/2009/07/facebook-inbox-count-for-conkyothers.html)

---

### Post by pilp4 on 2009-09-10
Bump. I totally agree the only scripts are for inbox message count, which, for me at least, really inst as useful as seeing how many notifications you have.

---

### Post by exutable on 2009-09-28
I totally agree, here is the start of a notification script, I just wrote it quickly and could probably be made to show notification number instead but...

I just shows your most recent notifications in the amount you want.  For example the last 5


```

#Written by Dane Shea, this code was mostly taken from the Specto

# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public
# License as published by the Free Software Foundation; either
# version 2 of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU General Public
# License along with this program; if not, write to the
# Free Software Foundation, Inc., 59 Temple Place - Suite 330,
# Boston, MA 02111-1307, USA.

import urllib2
import formatter
import htmllib
import re
import sys
from cStringIO import StringIO

username = sys.argv[1]
password = sys.argv[2]
notamt = int(sys.argv[3])


class Facebook():
    
    def __init__(self, email, password):
        self.email = email
        self.password = password
    
    def connect(self):
        opener = urllib2.build_opener(urllib2.HTTPCookieProcessor())
        urllib2.install_opener(opener)
        response = urllib2.urlopen(urllib2.Request("https://login.facebook.com/login.php?m&amp;next=http%3A%2F%2Fm.facebook.com%2Fhome.php", "email=%s&pass=%s&login=Login" % (self.email, self.password)))
        if "form action=\"https://login.facebook.com/login.php" in response.read():
            return False
        else:
            return True
            
    def get_notifications(self):
            notifications = []
            connection = urllib2.urlopen("http://m.facebook.com/notifications.php")
            messages = connection.read().split("<hr />")
            for line in messages:
                #search notification
                notification = re.search('<div><a href="/.+.php\?.+>(.+)</div>', line)
                if notification != None:
                    outstream = StringIO()
                    p = htmllib.HTMLParser(formatter.AbstractFormatter(formatter.DumbWriter(outstream)))
                    p.feed(notification.group())
                    notification = re.sub("(\[.\])", "", outstream.getvalue())
                    notifications.append(notification.strip('\n'))
            return notifications
    def print_notifications(self):
        notifications = self.get_notifications()
        for notification in notifications[0:notamt]:
            print notification
                    
                    
test = Facebook(sys.argv[1], sys.argv[2])
if(test.connect()):
    test.print_notifications()
else:
    print "Can't connect to Facebook at this time"


```


Example code for conkyrc:
```
${execpi 300 python ~/Scripts/facebooknotifications.py ********** ********* 5}
```

Tell me if you guys have any ideas, bugs or features you think I should include

---

### Post by AllRadioisDead on 2009-10-12
> **exutable said:**
> I totally agree, here is the start of a notification script, I just wrote it quickly and could probably be made to show notification number instead but...

I just shows your most recent notifications in the amount you want.  For example the last 5


```

#Written by Dane Shea, this code was mostly taken from the Specto

# This program is free software; you can redistribute it and/or
# modify it under the terms of the GNU General Public
# License as published by the Free Software Foundation; either
# version 2 of the License, or (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU
# General Public License for more details.
#
# You should have received a copy of the GNU General Public
# License along with this program; if not, write to the
# Free Software Foundation, Inc., 59 Temple Place - Suite 330,
# Boston, MA 02111-1307, USA.

import urllib2
import formatter
import htmllib
import re
import sys
from cStringIO import StringIO

username = sys.argv[1]
password = sys.argv[2]
notamt = int(sys.argv[3])


class Facebook():
    
    def __init__(self, email, password):
        self.email = email
        self.password = password
    
    def connect(self):
        opener = urllib2.build_opener(urllib2.HTTPCookieProcessor())
        urllib2.install_opener(opener)
        response = urllib2.urlopen(urllib2.Request("https://login.facebook.com/login.php?m&amp;next=http%3A%2F%2Fm.facebook.com%2Fhome.php", "email=%s&pass=%s&login=Login" % (self.email, self.password)))
        if "form action=\"https://login.facebook.com/login.php" in response.read():
            return False
        else:
            return True
            
    def get_notifications(self):
            notifications = []
            connection = urllib2.urlopen("http://m.facebook.com/notifications.php")
            messages = connection.read().split("<hr />")
            for line in messages:
                #search notification
                notification = re.search('<div><a href="/.+.php\?.+>(.+)</div>', line)
                if notification != None:
                    outstream = StringIO()
                    p = htmllib.HTMLParser(formatter.AbstractFormatter(formatter.DumbWriter(outstream)))
                    p.feed(notification.group())
                    notification = re.sub("(\[.\])", "", outstream.getvalue())
                    notifications.append(notification.strip('\n'))
            return notifications
    def print_notifications(self):
        notifications = self.get_notifications()
        for notification in notifications[0:notamt]:
            print notification
                    
                    
test = Facebook(sys.argv[1], sys.argv[2])
if(test.connect()):
    test.print_notifications()
else:
    print "Can't connect to Facebook at this time"


```
Example code for conkyrc:
```
${execpi 300 python ~/Scripts/facebooknotifications.py ********** ********* 5}
```Tell me if you guys have any ideas, bugs or features you think I should include
I'm sorry, this may sound stupid, but where do we add our email/password? 
I tried replacing the asterisks, but the script didn't work.

---

### Post by shadesofevil on 2009-11-21
check out fbcmd

[http://fbcmd.dtompkins.com/](http://fbcmd.dtompkins.com/)

---

### Post by sdlynx on 2010-01-20
thanks guys, idk why ubuntuforums didn't sub me to this, but apparently I wanted to do this in July last year and now do again.  I happened upon my own thread haha.

anyway, I tried using the rss notification thing facebook provides but it returns "incompatible browser".

I'll try exutable's code.

Edit: Right so I can get the notifications, but not the number.
Regardless, is it possible to truncate the data retrieved from {rss <url> 1 item_title 1}?

---

