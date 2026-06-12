---
title: "dbus and network manager errors!"
date: 2009-06-13
forum: General Help
---

### Post by bornagainpenguin on 2009-06-13
In the interests of full disclosure I've had a topic about this in the Absolute Beginners section for two months now without getting any answers.  I recently reinstalled Jaunty from scratch and am hoping to get this last thing solved that is holding me back from being able to fully enjoy Ubuntu 9.04.

When I open Straw Feed Reader it seems to hang and only a few of my feeds get updated while the hard drive thrashes like crazy.  Earlier versions of the program run fine in earlier releases of Ubuntu, so I know it has something to do with Jaunty.  Also, I think the issues I have may be related to the Python update, which broke compatibility with earlier versions of that language.

Starting thee application from the terminal gives me the following error:

```
strawdbus.py:69:start_services: Error while connecting to NetworkManager: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 7 matched rules; type="method_call", sender=":1.61" (uid=1000 pid=5778 comm="/usr/bin/python /usr/bin/straw ") interface="(unset)" member="state" error name="(unset)" requested_reply=0 destination=":1.11" (uid=0 pid=2879 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))

```

Can someone please tell me how to fix this in Jaunty, so I can stay with the latest release?

Thanks in advance!

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-06-14
/bump

---

### Post by bornagainpenguin on 2009-06-14
What do I have to do to get help with this issue?

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-06-15
My other thread on this issue is here: [http://ubuntuforums.org/showthread.php?t=1140811](http://ubuntuforums.org/showthread.php?t=1140811)

As you can see I've been trying to get help on this since April 27th and no one has even bothered to respond to me!  If this keeps up I may have to say the heck with Linux and try moving back to Windows XP and start searching for a working offline feed reader that will run under that environment.

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-06-15
/BUMPing because no one cares

---

### Post by bornagainpenguin on 2009-06-16
HELLLOOOOOO????

IS ANYONE THERE?

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-06-19
/regular bump

---

### Post by bornagainpenguin on 2009-07-02
/Still interested bump

---

### Post by bornagainpenguin on 2009-07-09
/bump

---

### Post by AFarris01 on 2009-07-10
I'm sorry you've gone for so long w/o help... it could be that nobody else has experienced this error before, or nobody that has seen your thread knows enough about your issue to help. I can honestly say I'm one of the latter, but I'd like to try and help anyway.

first off, i'd like to start with some questions:
1. what have you tried before to fix this, if anything at all?
2. does your network manager work properly already?
3. have you observed this issue in any other programs?
4. What version of python do you have installed?
5. what version of Straw do you have installed?

there may be more pertinent info to ask for later...but that should do it for now. 

From the error message you posted, the little bit about 'access denied' looks like a permissions issue, possibly an issue with the program's networking implementation. I'd strongly consider filing a bug report with the Straw devs, give them the error, and see if they can find a problem.  

all this being said, I don't use feed readers, but I installed straw just to give it a spin, and see if I could see what you were seeing... sure enough, fresh after installing I launch from a terminal and receive several errors, including the one you've observed:
```

$ straw
FeedCategoryList.py:92:load_data: Feed 'Straw news' from http://www.gnome.org/projects/straw/news.rss (1) was already in PseudoCategory Uncategorized, skipping
FeedCategoryList.py:92:load_data: Feed 'art.gnome.org releases' from http://art.gnome.org/backend.php (2) was already in PseudoCategory Uncategorized, skipping
FeedCategoryList.py:92:load_data: Feed 'FootNotes - gnomedesktop.org' from http://www.gnomedesktop.org/backend2.php (3) was already in PseudoCategory Uncategorized, skipping
FeedCategoryList.py:92:load_data: Feed 'GNOME News' from http://planet.gnome.org/news/rss20.xml (4) was already in PseudoCategory Uncategorized, skipping
FeedCategoryList.py:92:load_data: Feed 'Linux.com' from http://www.linux.com/index.rss (5) was already in PseudoCategory Uncategorized, skipping
/usr/lib/straw/straw/FeedListView.py:435: GtkWarning: A floating object was finalized. This means that someone
called g_object_unref() on an object that had only a floating
reference; the initial floating reference is not owned by anyone
and must be removed with g_object_ref_sink().
  rowiter = self._model.append(parent)
**strawdbus.py:69:start_services: Error while connecting to NetworkManager: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 7 matched rules; type="method_call", sender=":1.76" (uid=1000 pid=29429 comm="/usr/bin/python /usr/bin/straw ") interface="(unset)" member="state" error name="(unset)" requested_reply=0 destination=":1.13" (uid=0 pid=4258 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))**


```

This is with: 
    Python 2.6.2
    Straw 0.27

My thoughts are that it's a bug, and you should use the "Help >*Report a problem" link in straw to log a bug report on bugzilla. sorry :(

alternatively...you could try picking up some python skills and try fixing it yourself, then send a patch to the devs :)

Hope that helps a bit...
Andrew

---

### Post by AFarris01 on 2009-07-10
After a little hunting, I located the problematic function, in file "/usr/lib/straw/straw/strawdbus.py": 
```

nm_interface = dbus.Interface(proxy_obj, NetworkListener.SERVICE_NAME)

```
This is the function that is returning the error... I don't have time right now to look at the dbus python file and see if I*can find out whats going wrong, but there's some followup info if you'd care to look into it yourself.

I'll post along later if I find something further

---

### Post by bornagainpenguin on 2009-07-11
> **AFarris01 said:**
> After a little hunting, I located the problematic function, in file "/usr/lib/straw/straw/strawdbus.py": 
```

nm_interface = dbus.Interface(proxy_obj, NetworkListener.SERVICE_NAME)

```
This is the function that is returning the error... I don't have time right now to look at the dbus python file and see if I*can find out whats going wrong, but there's some followup info if you'd care to look into it yourself.

I'll post along later if I find something further

THANK YOU!  I'd just about given up hope of ever seeing any attempts at getting this fixed until the developers were able to get back to things.  Unfortunately I'm not a programmer, just an end user, so I am unable to make any use of the information supplied.

Does anyone else have any idea how to fix the situation, now that AFarris01 has pointed out the files causing trouble?

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-07-11
Whoops, shows me for not checking to make sure I'd seen all the posts...

> **AFarris01 said:**
> I'm sorry you've gone for so long w/o help... it could be that nobody else has experienced this error before, or nobody that has seen your thread knows enough about your issue to help. I can honestly say I'm one of the latter, but I'd like to try and help anyway.

I'm the same but I usually manage to muddle along somehow any way... ;)

> **AFarris01 said:**
> first off, i'd like to start with some questions:

Sure, shoot!

> **AFarris01 said:**
> 1. what have you tried before to fix this, if anything at all?

I posted in here and at the eeeuser.com forums, and tried running as root, to see if that affected the permissions (it didn't) and pestering the developers at their blog about the situation--but being as how Real Life ™ has been getting in the way of Real Soon Now ® for over a year, not much hope there I'm afraid.

> **AFarris01 said:**
> 2. does your network manager work properly already?
Yes.

> **AFarris01 said:**
> 3. have you observed this issue in any other programs?
Other than this issue, everything else seems to work fine as far as I can tell.

> **AFarris01 said:**
> 4. What version of python do you have installed?
The distro default for Jaunty.

> **AFarris01 said:**
> 5. what version of Straw do you have installed?
See above.


> **AFarris01 said:**
> alternatively...you could try picking up some python skills and try fixing it yourself, then send a patch to the devs :)

Heh...maybe some day--I'm hoping to eventually pick up python, if for no other reason than to be able to better pick up ren'py which I am a fan of.

> **AFarris01 said:**
> Hope that helps a bit...
Andrew

Hey, just knowing that someone else has read the post and I'm not out here shouting in the wind to myself while mothers hurry young children along with encouragements not to stare at the deranged man helps! :)  Thank you for taking the time when no one else would!

Hopefully you might be able to piece together something that will allow me to do a quick and dirty hack or someone else more knowledgeable than the two of us might take a peek over the two of our shoulders and tell us how to fix the situation.  At least I can hope to be able to eventually be able to install Jaunty on my eeepc and enjoy the much improved flash and video performance while using the latest 2.6 kernel release...

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-07-28
/nudges thread

---

### Post by bornagainpenguin on 2009-08-05
/Bump to show that I care.  We all need a little more bumping in our lives.  Perhaps if...

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-08-10
I started a thread in the Karmic section on removing Straw from Ubuntu, since it was broken in Jaunty and still breaking under then Alpha Karmic release (one or two?)  bcat had some advice on the python code, which fixed a similar issue and which he hoped might help my case--

[QUOTE=bcat]I don't use Straw, but maybe I can help you anyway. I ran in to the same error a couple months ago when I was writing a Python script to run shell commands when NetworkManager changed state. It seems that at some point (probably when NM 0.7 was released) the NM D-Bus interface was changed in a way that broke old code that tried to get the current NetworkManager state value. I just looked at the file where you're getting an error, and I think the fix I used might also work here.

Edit /usr/lib/straw/straw/strawdbus.py and change this:

```
                # don't touch offline if it has been previously set.
                if not Config.get_instance().offline:
                        nl.set_state(proxy_obj.state())
```

to this:

```
                # don't touch offline if it has been previously set.
                if not Config.get_instance().offline:
                        nm_props = dbus.Interface(proxy_obj, dbus.PROPERTIES_IFACE)
                        nm_state = nm_props.Get(NetworkListener.SERVICE_NAME, "State")
                        nl.set_state(nm_state)
```[/QUOTE]

Unfortunately while this updated bit of code made the error I posted in this thread go away in Terminal, the issue of not getting updated feeds persists.  I am unable to take this any further without error messages, so if anyone has any ideas on where to go from here, I'm all ears.

I really like Ubuntu and prefer it greatly to WinXP on my eeepc, but without Straw I am missing one of the biggest benefits (to me) of having such a portable computer.  I am having a harder time dealing with the conflicts of running Hardy Heron when the better hardware support for things like Flash and video is moving on with Jaunty and Karmic.  At this point I'd might as well install WinXP and use Litestep to adjust the desktop to my screen...

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-08-22
/forlorn bump

---

### Post by BIGtrouble77 on 2009-09-19
I'm having trouble with this too.  May want to try liferea until this gets fixed (if ever).  It's a native gtk app and works well.

[http://liferea.sourceforge.net/](http://liferea.sourceforge.net/)

I don't know python and dbus well enough to address the straw permissions issue, but it looks painfully simple to fix for someone in the know.

-bt

---

### Post by bornagainpenguin on 2009-09-22
> **BIGtrouble77 said:**
> I'm having trouble with this too.  May want to try liferea until this gets fixed (if ever).  It's a native gtk app and works well.

[http://liferea.sourceforge.net/](http://liferea.sourceforge.net/)

It doesn't really work offline, even though there are supposed to be conversion "filter" scripts that would allow this:
[http://ubuntuforums.org/showthread.php?t=1251672](http://ubuntuforums.org/showthread.php?t=1251672)

Also see the Liferea blog where one of the developers makes it clear they have a different definition of "offline" than most would:
[http://liferea.blogspot.com/2008/05/full-google-reader-support.html](http://liferea.blogspot.com/2008/05/full-google-reader-support.html)

> **BIGtrouble77 said:**
> I don't know python and dbus well enough to address the straw permissions issue, but it looks painfully simple to fix for someone in the know.

-bt

From the standpoint of a non-programmer I am inclined to agree, it doesn't seem like this should be all that difficult to fix.  Unfortunately no one seems to care about us, the users.  The lead developers claim to be working on it (in the midst of being distracted by Real Life) but reading their blog page makes it clear they too have abandoned us in favor of a largely theoretical rewrite: 
[http://strawreader.wordpress.com/2009/06/14/update/](http://strawreader.wordpress.com/2009/06/14/update/)

Meanwhile the Straw package isn't even being planned for inclusion in the upcoming release of Karmic:
[https://bugs.launchpad.net/ubuntu/+source/straw/+bug/409387](https://bugs.launchpad.net/ubuntu/+source/straw/+bug/409387)

My attempts at lighting a fire under one of the packagers or coders has failed miserably and they'd rather pull the package, rather than fixing the darn thing,

Which is the root of my bitterness over this subject--by the way people have been reacting you'd think we were demanding new features or for the developers to make the application run on a 386 or something, instead of simply asking for their application to remain functioning as it did before in the most recent releases.  But they just don't care...

I don't know what I'm going to do when support for Hardy runs out and I have no choice but to move on to a more recent version of Ubuntu in order to keep getting security fixes and better hardware support.

--bornagainpenguin

---

### Post by bornagainpenguin on 2009-10-20
/hope springs eternal

---

### Post by kozuscek on 2009-12-15
Hello from a fellow user.

I've just installed straw on a well-updated Jaunty (9.04) and it fails to fetch any feeds, in either offline or online mode. When ran from the shell, it reports that the network manager has turned it down:

strawdbus.py:69:start_services: Error while connecting to NetworkManager: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 6 matched rules; type="method_call", sender=":1.175" (uid=500 pid=5313 comm="/usr/bin/python /usr/bin/straw ") interface="(unset)" member="state" error name="(unset)" requested_reply=0 destination=":1.13" (uid=0 pid=3443 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))

The gui itself shows no error message at all - refreshing feeds return instantly (with no data, of course) and adding feeds just leaves the dialog progress bar looping to infinity.

Apparently, straw is a python app that uses dbus to kindly ask the network manager component to give it internet access, and the latter just says "**** off". nm has been giving me similar trouble  in a lot of different scenarios; from what I can discern, it's just abandonware.

I'll try a fresh install of straw (not from ubuntu repos, but from gnome themselves) to see it that helps at all.

Thank you for pinging so consistently for so long.
-i

---

### Post by kozuscek on 2009-12-15
According to [http://projects.gnome.org/straw/](http://projects.gnome.org/straw/), the project has been abandonware for two years now.

Need to find sth else then.

---

### Post by bornagainpenguin on 2010-05-03
> **kozuscek said:**
> Hello from a fellow user.

I've just installed straw on a well-updated Jaunty (9.04) and it fails to fetch any feeds, in either offline or online mode. When ran from the shell, it reports that the network manager has turned it down:

strawdbus.py:69:start_services: Error while connecting to NetworkManager: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 6 matched rules; type="method_call", sender=":1.175" (uid=500 pid=5313 comm="/usr/bin/python /usr/bin/straw ") interface="(unset)" member="state" error name="(unset)" requested_reply=0 destination=":1.13" (uid=0 pid=3443 comm="/usr/sbin/NetworkManager --pid-file /var/run/Netwo"))

The gui itself shows no error message at all - refreshing feeds return instantly (with no data, of course) and adding feeds just leaves the dialog progress bar looping to infinity.

Apparently, straw is a python app that uses dbus to kindly ask the network manager component to give it internet access, and the latter just says "**** off". nm has been giving me similar trouble  in a lot of different scenarios; from what I can discern, it's just abandonware.

I'll try a fresh install of straw (not from ubuntu repos, but from gnome themselves) to see it that helps at all.

Thank you for pinging so consistently for so long.
-i

Straw will work on Jaunty if you uninstall the python adns library.  Yes, the same one it complains about not having in terminal if you remove it.  :confused:  All I know is it starts working again once that package is removed.  Doesn't do much for the rampant segmentation faults though...

Also, /BUMP

--bornagainpenguin

---

### Post by bornagainpenguin on 2010-05-12
Habitual BUMP

---

### Post by bornagainpenguin on 2010-07-26
A friend on the eeeuser.com forums who knew that I'd been looking for a solution to this for some time now introduced me to [Naufrago!]("http://www.gnomefiles.com/app.php/Naufrago!") on [Gnomefiles.com]("http://www.gnomefiles.com").  This nice little app is pretty much exactly what the doctor ordered.  While it is still only at version .0.1 it is functionally able to step right into the gaping void the loss of Straw made.  I strongly recommend anyone searching for an offline feed reader for Linux give this app a look despite its very alpha status.

--bornagainpenguin

PS: How would I go about recommending an app for inclusion to the repositories?

---

