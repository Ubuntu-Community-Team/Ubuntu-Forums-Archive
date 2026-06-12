---
title: "Eye Candy"
date: 2007-05-21
forum: Desktop Effects &amp; Customization
---

### Post by myattb on 2007-05-21
Hi All,

I want to do a few things to the standard distro look and feel just to get things a bit more organised on screen (for me anyway) but not sure where to look for what I want (or if it even exists).

I am looking for a dock bar for the desktop (like Mac OS X) so that I can put my most utilised tools and applications here. Can anyone help / point me in the right direction for what I am looking for?

Thanx.

---

### Post by tkjacobsen on 2007-05-21
Maybe gnome-dock is what you are looking for. See this howto [http://ubuntuforums.org/showthread.php?t=302570&highlight=cairo](http://ubuntuforums.org/showthread.php?t=302570&highlight=cairo)

Or if you are using KDE, try kxdocker.

EDIT:
alternatively you might want to check out gimmie [http://beatnik.infogami.com/Gimmie](http://beatnik.infogami.com/Gimmie)

---

### Post by Ozeuss on 2007-05-21
i don't know the OSX dock, but you can
1) create and ordinary panel on the bottom, making it a bit larger, transparent, and not expandable (centered). 
2) use gimmie as suggested. i wasn't very fond of it.
3) use avant-window-navigator. very cool and useful, but you need a composite running (compiz or beryl), and you need to compile it yourself/ add a repository for the svn version (there are no version in the ubuntu repos).
those are the ones i used. there are more options, i think.

---

### Post by silent1643 on 2007-05-21
> **Ozeuss said:**
> i don't know the OSX dock, but you can
1) create and ordinary panel on the bottom, making it a bit larger, transparent, and not expandable (centered). 
2) use gimmie as suggested. i wasn't very fond of it.
3) use avant-window-navigator. very cool and useful, but you need a composite running (compiz or beryl), and you need to compile it yourself/ add a repository for the svn version (there are no version in the ubuntu repos).
those are the ones i used. there are more options, i think.

[link]("http://www.taimila.com/ubuntuosx.php")

---

### Post by raul_ on 2007-05-21
> **Ozeuss said:**
>  you need a composite running (compiz or beryl), and you need to compile it yourself/ add a repository for the svn version (there are no version in the ubuntu repos).


I didn't compile it. There's a repository somewhere in the forums

---

### Post by myattb on 2007-05-24
Hi - please help!!!

I went away and looked at the suggested apps and decided to go with avant-windows-navigator.
I followed the guide here [http://ubuntuforums.org/showthread.php?p=2307772](http://ubuntuforums.org/showthread.php?p=2307772) but I still can't get it to work?

I have Beryl installed and the applications (AVN and Affinity) look to be installed OK as far as I can tell? - is there any logging/diagnostics I can provide to help diagnose the problem?

Strange behaviour is that affinity preferences will load but not the application? And neither the preferences or the application will load for AWN??

I don't know if I have done anything wrong with the install or make process?
I don't know if I need to uninstall and try again - or even how to successfully uninstall.

So any guidance would be much appreciated.

Thanx

---

### Post by notwen on 2007-05-24
[Here]("http://ubuntuforums.org/showthread.php?t=385981") is the current AWN guide here on the forums.  If you run into any trouble post your issue and wait for help. =]  I myself use AWN and don't see me changing anytime soon as far as docks go.  Good luck on your quest for eye candy.

---

### Post by myattb on 2007-05-24
Thanks for the reply......
That is the same guide that I followed - same issues as previous post stand.

Any logging/configuration information I can provide to see if the install on my machine is correct?

---

### Post by reacocard on 2007-05-24
> **myattb said:**
> Thanks for the reply......
That is the same guide that I followed - same issues as previous post stand.

Any logging/configuration information I can provide to see if the install on my machine is correct?

Just run them from a terminal and post the output, that's the easiest way.

Also, the SVN version works much much much much much better than the stable for both of these right now, so if you're not already using that, you should try upgrading first.

---

### Post by myattb on 2007-05-25
I ran both AWN and Affinity from my terminal as suggested and got the following output

ben@Inspiron8200:~$ avant-window-navigator
Segmentation fault (core dumped)

ben@Inspiron8200:~$ affinity
Action Engine : Scanning /home/ben/.gnome2/affinity/actions
Action Engine : Scanning /usr/local/share/affinity/actions
Application Engine : Scanning /home/ben/.local/share/applications
Application Engine : Scanning /usr/local/share/applications
Application Engine : Scanning /usr/share/applications
Application Engine : Scanning /usr/share/applications/kde
Application Engine : Scanning /usr/share/applications/screensavers
Desktop Search Engine : Tracker
Segmentation fault (core dumped)

ben@Inspiron8200:~$ 

Any suggestions?

Thanx

---

### Post by reacocard on 2007-05-25
> **myattb said:**
> I ran both AWN and Affinity from my terminal as suggested and got the following output

ben@Inspiron8200:~$ avant-window-navigator
Segmentation fault (core dumped)

ben@Inspiron8200:~$ affinity
Action Engine : Scanning /home/ben/.gnome2/affinity/actions
Action Engine : Scanning /usr/local/share/affinity/actions
Application Engine : Scanning /home/ben/.local/share/applications
Application Engine : Scanning /usr/local/share/applications
Application Engine : Scanning /usr/share/applications
Application Engine : Scanning /usr/share/applications/kde
Application Engine : Scanning /usr/share/applications/screensavers
Desktop Search Engine : Tracker
Segmentation fault (core dumped)

ben@Inspiron8200:~$ 

Any suggestions?

Thanx

I hate C, it never gives useful errors :mad:

You could try using the packages from the repository instead, they're known to work for many. Just do a 'sudo make uninstall' in the source directory to remove your current install, then follow the guide to add the repo.

---

### Post by raul_ on 2007-05-25
> **reacocard said:**
> I hate C, it never gives useful errors :mad:

You could try using the packages from the repository instead, they're known to work for many. Just do a 'sudo make uninstall' in the source directory to remove your current install, then follow the guide to add the repo.

If you programmed the code then you know where you're accessing memory, and then it's up to you to know if you should be accessing it or not :mrgreen:

That is surely a bug, report it to the authors.

sidenote:  you should hate gcc because reporting errors is the compilers job :) i personally find it much better than javac (and here come the flames) :popcorn:

---

### Post by reacocard on 2007-05-25
> **raul_ said:**
> If you programmed the code then you know where you're accessing memory, and then it's up to you to know if you should be accessing it or not :mrgreen:

That is surely a bug, report it to the authors.

sidenote:  you should hate gcc because reporting errors is the compilers job :) i personally find it much better than javac (and here come the flames) :popcorn:

I meant runtime errors. Segfault is really unhelpful for diagnosing problems. And I'm not at all a C dev. Without more info, I can't exactly make a bug report though, can I?

---

### Post by raul_ on 2007-05-25
> **reacocard said:**
> I meant runtime errors. Segfault is really unhelpful for diagnosing problems. And I'm not at all a C dev. Without more info, I can't exactly make a bug report though, can I?

Of course. But you can tell the authors "hey I tried running your program and your program segfaulted"
They'll probably ask you to generate a backtrace with a "please" in the end ;)

I have to admit that debugging a segfault can take a lot of time though. specially because i just can't work with ddd

---

### Post by myattb on 2007-05-26
I did an un-install and reinstalled again.
But I was unable to get AWN or Affinity working - so I changed from Beryl to Compiz and I can now use both AWN and Affinity?

The only remaining issue is that I can't access the settings for either (System -> Preferences) as nothing happens when I select the option for either app? Suggestions??

I also need to know how to load both Beryl and AWN on startup - I think I am right in saying that they both need an entry in sessions startup programs - but what command do I need for them?

Thanx

---

### Post by reacocard on 2007-05-26
> **myattb said:**
> I did an un-install and reinstalled again.
But I was unable to get AWN or Affinity working - so I changed from Beryl to Compiz and I can now use both AWN and Affinity?

The only remaining issue is that I can't access the settings for either (System -> Preferences) as nothing happens when I select the option for either app? Suggestions??

I also need to know how to load both Beryl and AWN on startup - I think I am right in saying that they both need an entry in sessions startup programs - but what command do I need for them?

Thanx

What do you get when running the settings apps (avant-preferences, affinity-preferences) from a terminal?

For loading at startup, the command for beryl is beryl (or beryl-manager is you want the systray icon), and for AWN is avant-window-navigator.

---

### Post by myattb on 2007-05-26
Thanks for the startup commands :D

This is the terminal output from running the preferences commands

ben@Inspiron8200:~$ avant-preferences
/usr/local/share/avant-window-navigator/window.glade

(avant-preferences:5669): libglade-WARNING **: could not find glade file '/usr/local/share/avant-window-navigator/window.glade'
Traceback (most recent call last):
  File "/usr/local/bin/avant-preferences", line 250, in <module>
    app = main()
  File "/usr/local/bin/avant-preferences", line 125, in __init__
    self.wTree = gtk.glade.XML(self.gladefile, domain=APP) 
RuntimeError: could not create GladeXML object
ben@Inspiron8200:~$ 

ben@Inspiron8200:~$ affinity-preferences
/usr/local/share/affinity/window.glade

(affinity-preferences:5684): libglade-WARNING **: could not find glade file '/usr/local/share/affinity/window.glade'
Traceback (most recent call last):
  File "/usr/local/bin/affinity-preferences", line 277, in <module>
    app = main()
  File "/usr/local/bin/affinity-preferences", line 147, in __init__
    self.wTree = gtk.glade.XML(self.gladefile, domain=I18N_DOMAIN) 
RuntimeError: could not create GladeXML object
ben@Inspiron8200:~$

---

### Post by reacocard on 2007-05-26
> **myattb said:**
> Thanks for the startup commands :D

This is the terminal output from running the preferences commands

ben@Inspiron8200:~$ avant-preferences
/usr/local/share/avant-window-navigator/window.glade

(avant-preferences:5669): libglade-WARNING **: could not find glade file '/usr/local/share/avant-window-navigator/window.glade'
Traceback (most recent call last):
  File "/usr/local/bin/avant-preferences", line 250, in <module>
    app = main()
  File "/usr/local/bin/avant-preferences", line 125, in __init__
    self.wTree = gtk.glade.XML(self.gladefile, domain=APP) 
RuntimeError: could not create GladeXML object
ben@Inspiron8200:~$ 

ben@Inspiron8200:~$ affinity-preferences
/usr/local/share/affinity/window.glade

(affinity-preferences:5684): libglade-WARNING **: could not find glade file '/usr/local/share/affinity/window.glade'
Traceback (most recent call last):
  File "/usr/local/bin/affinity-preferences", line 277, in <module>
    app = main()
  File "/usr/local/bin/affinity-preferences", line 147, in __init__
    self.wTree = gtk.glade.XML(self.gladefile, domain=I18N_DOMAIN) 
RuntimeError: could not create GladeXML object
ben@Inspiron8200:~$

Hah, I've seen that before. It's an easy fix:
```
sudo rm /usr/local/bin/affinity-preferences
sudo rm /usr/local/bin/avant-preferences
```

---

### Post by myattb on 2007-05-27
Works perfectly - thanks :D

Can you explain what happened (just to help my understanding while trying to learn about Linux and Ubuntu?) Why did I need to remove these? Why did they cause the issue?

Much appreciated.

---

### Post by reacocard on 2007-05-27
> **myattb said:**
> Works perfectly - thanks :D

Can you explain what happened (just to help my understanding while trying to learn about Linux and Ubuntu?) Why did I need to remove these? Why did they cause the issue?

Much appreciated.

They were files left over from your first try. Since /usr/local/bin is before /usr/bin in $PATH, they were picked up and run, but they couldn't find the data files in /usr/local/share, since they had been removed. Getting rid of those two files allowed the correct ones in /usr/bin to run and find the new data files in /usr/share.

---

### Post by myattb on 2007-05-28
Thanks - makes sense.....
So would I need to run the same command for all user accounts on the machine if they logged in before the setup was sorted out?

Other question - why can't I get Beryl to work properly (only compiz)?
I would really like to utilise some of the effects but It screws up the desktop (and sometimes crashes completely).
Could it be I am running on older machine? Are there issues with certain graphics cards (I have an ATI  mobile card in my Inspiron 8200 laptop).

ben@Inspiron8200:~$ lspci | grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 01)

Any guidance appreciated as always.

---

### Post by reacocard on 2007-05-28
> **myattb said:**
> Thanks - makes sense.....
So would I need to run the same command for all user accounts on the machine if they logged in before the setup was sorted out?

No, it'd work for all users automatically. Anything that is done outside of /home has system-wide effects.

> Other question - why can't I get Beryl to work properly (only compiz)?
I would really like to utilise some of the effects but It screws up the desktop (and sometimes crashes completely).
Could it be I am running on older machine? Are there issues with certain graphics cards (I have an ATI  mobile card in my Inspiron 8200 laptop).

ben@Inspiron8200:~$ lspci | grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 [Mobility FireGL 9000] (rev 01)

Any guidance appreciated as always.

Beryl is still unstable. It's not surprising it has issues with some cards, and ATI's drivers aren't exactly the best. ;) NVidia and Intel cards are better bets. My integrated Intel 915GM graphics run Beryl (and Compiz) perfectly, although I can't use blur since it has no pixel shaders. :(

---

