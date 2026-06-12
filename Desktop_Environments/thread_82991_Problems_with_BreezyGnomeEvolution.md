---
title: "Problems with Breezy/Gnome/Evolution"
date: 2005-10-27
forum: Desktop Environments
---

### Post by ions on 2005-10-27
Some problems I've had with Breezy.  Yes I have searched and to no avail.  I would have posted these seperately but I think they're mostly Gnome related.

Problems with Machine A:

1. No streaming video in FF. I have searched here and Google and tried just about everything I've found. It worked fine with Hoary. I figure I'll wait for the Ubuntuguide to come out so at least I'll have some sort of base level of information to explain what I've tried other than "everything". Yes I do have the codecs. Sound does work though so I can hear the videos.

2. Evolution Mail. As soon as I have to download or view an attachment Evolution becomes unusably laggy. Real bad. Receiving, sending or forwarding any mail with an attachment is a long painful process. 7 or 8 minutes to send an email with a 100KB attachment. And no, it's not my connection.

3. FF Crashes. Just disappears. Not as much as it used to when I had the tabbrowser extension but it still does once in a while. No rhyme or reason. Sometimes it'll just disappear when idling with one local tab open. I'll get up to use the can and come back to find FF gone.

4. Evolution Calendar. I add an appointment. "Go crazy at 11AM on Tuesday". If I click the Gnome clock in the panel it displays that I have set an appointment to go crazy at 7AM. If I set my appointment for later in the afternoon, 4PM for example, the calendar under that clock says I have set it for noon.

5. My apps do not appear on the same virtual desktops that they were on when I shut down as they did in Hoary. No big deal but I need to do a bit of sorting I never had to in Hoary.

6. Going to Places > Recent Documents does not work unless I have already opened a document. So when I first start my machine and want to work on the same doc I was working on yesterday I may as well just go through Nautilus and open it that way cause Recent Documents does nothing at startup.

Problems with Machine B:

1. No streaming video in FF. I have searched here and Google and tried just about everything I've found. It worked fine with Hoary. I figure I'll wait for the Ubuntuguide to come out so at least I'll have some sort of base level of information to explain what I've tried other than "everything". Yes I do have the codecs. Sound does work though so I can hear the videos.

2. Instead of the pleasent GDM login screen I get an error and a default login screen. The error says:

> 
The Configuration is not correct!

This configuration file contains an invalid command line for the login dialogue, so running the default command. Please fix your configuration.


I am given an OK button to click.

Just to add that getting them to this point wasn't a smooth trouble free road. Following these directions: [https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes) did not lead to a trouble free process. It was a pain on both machines I've upgraded from Hoary.

---

### Post by Kyral on 2005-10-27
The Streaming Video thing can be solved by nabbing an Extension called "MediaPlayerConnectivity" from the Firefox Extensions place :D

---

### Post by ions on 2005-10-27
[QUOTE=Kyral]The Streaming Video thing can be solved by nabbing an Extension called "MediaPlayerConnectivity" from the Firefox Extensions place :D[/QUOTE]

Nope.  No further ahead.

---

### Post by ions on 2005-10-27
Found the problem for the Evolution Calendar.  "UTC" is set as the time zone....Don't know why it would have been changed on me but it was.  Still have a few outstnading problems.

---

### Post by ions on 2005-10-28
No one eles is having these problems?  Should I submit a bug?

---

### Post by Abandon on 2005-10-28
[QUOTE=ions]
1. No streaming video in FF. I have searched here and Google and tried just about everything I've found. It worked fine with Hoary. I figure I'll wait for the Ubuntuguide to come out so at least I'll have some sort of base level of information to explain what I've tried other than "everything". Yes I do have the codecs. Sound does work though so I can hear the videos.

2. Evolution Mail. As soon as I have to download or view an attachment Evolution becomes unusably laggy. Real bad. Receiving, sending or forwarding any mail with an attachment is a long painful process. 7 or 8 minutes to send an email with a 100KB attachment. And no, it's not my connection.[/QUOTE]

1: System/Help/Ubuntu 5.10 starterguide. Oh..and try Gxine. After installing you do have to run it once to install the plugins. 

2: Could be related to you're hostname. Post the content of you're /etc/hosts here!

---

### Post by ions on 2005-10-28
```
$ cat /etc/hosts
127.0.0.1 localhost.localdomain localhost tux

# The following lines are desirable for IPv6 capable hosts
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

# The following lines are desirable for IPv6 capable hosts
# (added automatically by netbase upgrade)

::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by ions on 2005-10-28
Installed gxine.  It just launches an instance of gxine that freezes when I try to view a stream in FF.  Feel like I'm getting closer though.

---

### Post by ions on 2005-11-02
I guess I should have mentioned all the lovely hard locks I'm getting too.  Almost 10 since Breezy went 'Stable'.  I had less than 5 during the whole Hoary run and I started in the beginning.

Also, Evolution does not remember the last thing I did after being restarted.  And since I'm getting these hardlocks it's all the more annoying.  When Evolution starts up it always displays messages that were just previously marked as junk or changes read status back to unread.

---

### Post by ions on 2005-11-03
Oh here's a new one.  I left the machine alone today to idle for about 8 hours.  Coming back to it I find it incredibly slow.  Opening terminals takes 15 seconds.  Going between virtual desktops takes almost 10 seconds.  I can type faster than it is displayed in irssi.  Switching tabs in FF takes a while too.  I never found Breezy to be zippy, frankly a little slower than Hoary overall so far but this is ridiculous.  This is a Barton 3200 with a gig of ram.  Top shows nothing eating ram or proc.  Sensors shows nice cool temps.

---

### Post by ions on 2005-11-04
Shutting down last night took about 6 or 7 minutes.  Eventually it did though.  Yeah, still here and becoming increasingly frustrated.

---

### Post by ions on 2005-11-04
The application Nicotine won't even start for me.  It worked a short time ago, I changed a directory name and now it no longer works.  Even if I change the directory back to its original name.

---

### Post by maltje on 2005-11-05
[QUOTE=ions]The application Nicotine won't even start for me.  It worked a short time ago, I changed a directory name and now it no longer works.  Even if I change the directory back to its original name.[/QUOTE]

The same probs here!!
Are the servers down????

---

### Post by ions on 2005-11-05
[QUOTE=maltje]The same probs here!!
Are the servers down????[/QUOTE]

I've never seen the servers being down cause Nicotine to lock altogether.  But that could be.

---

### Post by ions on 2005-11-14
Well I still have the above problems.  I had an old spare machine laying around and decided to put FreeBSD on it to test that OS for a while to see if I liked it.  I was enjoying it until the hard drive died.  I really don't want to leave Ubuntu but I'm not living with these problems from an "upgrade".

---

### Post by ions on 2005-11-14
Found a memory leak in Mono.  Killed Mono apps off and at least the machine is moderately responsive now.  The offending app is likely Tomboy.

Does anyone even care?

---

### Post by rkinder on 2005-11-15
[QUOTE=ions]Found a memory leak in Mono.  Killed Mono apps off and at least the machine is moderately responsive now.  The offending app is likely Tomboy.

Does anyone even care?[/QUOTE]

Don't worry, you're not alone... evolution 2.4 is causing much lost productivity for me ATM...

I would steer away from mono and mono-based apps for the time being - see the note from Jon Trowbridge for Beagle 0.1.2 ([One important detail: Beagle 0.1.2 requires Mono 1.1.10, which was released at the end of last week. 1.1.10 fixes some serious io-layer bugs that caused Beagle to crash or lock up, so everyone should upgrade right away.]("http://blog.trowbridge.org/index.php?p=52")).

---

### Post by ions on 2005-11-15
Yeah I've gotten rid of Mono.  Sucks cause I was used to Tomboy.  At least I no longer have to deal with the sluggishness due to a memory leak.  Just instability.  I came home today to see a handful of apps had crashed.  Mostly  Gnome apps.  Irssi had a core dump too.  

Nice to hear I'm not alone.

---

