---
title: "Avant Window Navigator Weather Applet network error message"
date: 2011-04-29
forum: Desktop Environments
---

### Post by cymbaline42 on 2011-04-29
I have the weather applet (from awn-extras) installed with AWN.  After entering the location, it displays the weather conditions properly, but I keep getting a pop-up message whenever it tries to refresh that says that there is a network error and I am experiencing connectivity issues.  This is strange because there is no issue with the network and the applet updates and displays the current weather conditions accurately.  How do I get rid of this pop-up error message?

---

### Post by Frogs Hair on 2011-04-29
I was using the Weather.com widget on Awn until installed 11.04 and I had the same problem . It was not the network but the site or the applet its self. sometimes I would change cities to a larger city close by and it would work fine . It only happened once in a while.

---

### Post by cymbaline42 on 2011-05-06
Figured out the solution.  The error message can be suppressed by editing the configuration file. 

sudo gedit /usr/share/avant-window-navigator/applets/weather/weather.py

Comment out line 240 by adding a # at the beginning of the line.  It should look like this:

def network_error_cb(self, e, tb):
        if type(e) is NetworkException:
            print "Error in Weather:", e
#           self.notification.show()

Restart the weather applet, and the error message will not appear any more.

---

### Post by jetiandresito on 2011-06-07
Thanks for the solution! 
It worked fine for me with Weather applet version  0.4.1

---

### Post by omrisaber on 2011-06-19
Thanks for the tip, I confirm it worked fine for me !
:)

---

### Post by kaneeec on 2011-06-26
> **cymbaline42 said:**
> Figured out the solution.  The error message can be suppressed by editing the configuration file. 

sudo gedit /usr/share/avant-window-navigator/applets/weather/weather.py

Comment out line 240 by adding a # at the beginning of the line.  It should look like this:

def network_error_cb(self, e, tb):
        if type(e) is NetworkException:
            print "Error in Weather:", e
#           self.notification.show()

Restart the weather applet, and the error message will not appear any more.
Awesome! It was very annoying...

---

### Post by shimoda on 2011-11-06
The problem appeared suddenly for me 2 days ago... Anyone more or any ideas/solutions?

Edit: The error in terminal is
> Warning in Weather: error in get_conditions: Couldn't parse conditions: list index out of range

---

### Post by dli8ilb on 2011-11-07
looks like the weather channel (weather.com) has changed something on their end.

[http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=2693&page=1&isLive=true](http://awn.planetblur.org/index.php?shard=forum&action=g_reply&ID=2693&page=1&isLive=true)

[UNSOLVED]

---

### Post by dli8ilb on 2011-11-07
found a working solution:

[http://ubuntuforums.org/showpost.php?p=11435261&postcount=59](http://ubuntuforums.org/showpost.php?p=11435261&postcount=59)

---

### Post by shimoda on 2011-11-08
thanks dli8ilb, worked very well!

Seems that was some problem with the license... What kind of license is needed for a weather app??? :confused: Something with weather.com?

---

### Post by dli8ilb on 2012-01-13
well, it stopped working again :-(  i'll probably just end up removing the applet, as it's causing more trouble than it's worth.

---

### Post by spedsal on 2012-01-15
Yep, same.  I get a message about connectivity issues and the dock icon shows a "network error" type of icon.  The thread here seems to indicate that Weather.com changed to a paid API:

[http://ubuntuforums.org/showthread.php?t=1704685&page=8](http://ubuntuforums.org/showthread.php?t=1704685&page=8)

Hopefully the applet can be revised to use NOAA or some other free API soon.  :(

---

### Post by dli8ilb on 2012-01-24
most recent fix here: [http://ubuntuforums.org/showpost.php?p=11630257&postcount=78](http://ubuntuforums.org/showpost.php?p=11630257&postcount=78)

confirmed working

---

### Post by Leebo on 2012-01-24
Awesome Thanks!

---

### Post by smdofjmdsfjoiez on 2012-02-04
Thanks!

---

### Post by gaga654321 on 2012-03-27
Worked well till about 2012.02.28. Then stop everyting. "Fetching condition for...."
I have installed it on 10.04 and made these changes, and it is working perfectly, but not on natty.

Could anybody post me a working solution, I love this app?
I'am using Ubuntu natty,  and i have tried  the version on the CD, and I tried 0.4.1~bz830+201104200108~natty1 from the AWN Testing Team PPA, but still nothing

---

### Post by d-man97 on 2012-11-05
If you have been following along with all the changes over the last year or two, here is the most recent fix for "Show Map" being messed up:

[http://ubuntuforums.org/showthread.php?p=12339201#post12339201](http://ubuntuforums.org/showthread.php?p=12339201#post12339201)

---

