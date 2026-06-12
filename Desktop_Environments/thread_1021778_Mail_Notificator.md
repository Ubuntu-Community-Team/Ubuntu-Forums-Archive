---
title: "Mail Notificator"
date: 2008-12-25
forum: Desktop Environments
---

### Post by slimx3m on 2008-12-25
does anybody knows how i could intall "Evolution Jean-Yves Lefort's Mail Notification plugin"?

---

### Post by katana2k on 2009-01-01
type 'sudo apt-get install evolution-plugins' into a terminal

---

### Post by slimx3m on 2009-01-26
i have all the plug-ins loaded.  and i thought that plugin is a special one because i even have one that it is supposed to do the same as the "Evolution Jean-Yves Lefort's Mail Notification plugin", but since is not that one then it does not recognize it.

---

### Post by Kobalt on 2009-01-26
Are you talking about the "mail-notification-evolution" package ?

---

### Post by slimx3m on 2009-01-26
> Are you talking about the "mail-notification-evolution" package ?
well, i do have the package installed.  

what i am trying to do is to configure mail notification app, but i can not compleate the configuration using evolution becuase it says that > "Evolution Jean-Yves Lefort's Mail Notification plugin" is not install.  so what i am trting to figure out is... where i could find such a plugin? i've been looking every where and i can not find it.  i know that the evolution-plugin package brings a mail notificator add-on, but i don't know which one mail notificator app is really asking for.

---

### Post by ugm6hr on 2009-01-26
[http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/)

This is *mail-notification* in synaptic.  Depending on your version of Ubuntu, getdeb.net may have newer versions.

*mail-notification-evolution* is the Evolution plugin (I have never used it).

You can configure mail-notification directly (i.e. without involving Evolution at all) - It appears in the System menu somewhere.

---

### Post by sirlatrom on 2009-02-06
> **ugm6hr said:**
> [http://www.nongnu.org/mailnotify/](http://www.nongnu.org/mailnotify/)

This is *mail-notification* in synaptic.  Depending on your version of Ubuntu, getdeb.net may have newer versions.

*mail-notification-evolution* is the Evolution plugin (I have never used it).

You can configure mail-notification directly (i.e. without involving Evolution at all) - It appears in the System menu somewhere.

mail-notification is great and all, but it requires the above mentioned plugin. Here's the error message displayed *in* the Mail Notification preferences dialog:

> Mail Notification can not contact Evolution. Make sure that Evolution is running and that the Evolution Jean-Yves Lefort's Mail Notification plugin is loaded.I am missing it too since a recent update to Jaunty, but I don't know how this applies to the original poster's situation.

---

### Post by slimx3m on 2009-02-12
> **sirlatrom said:**
> mail-notification is great and all, but it requires the above mentioned plugin. Here's the error message displayed *in* the Mail Notification preferences dialog:

I am missing it too since a recent update to Jaunty, but I don't know how this applies to the original poster's situation.

i know :( i which to configure mail notification fully but i guess that i would have to wait until they fix it for next version.

---

### Post by sharon.gmc on 2009-02-12
yup, i can't wait for the next version. . .

---

### Post by ronaldrand on 2009-03-07
I upgraded to Jaunty (disastrous!) and had this same problem. Lefort's plugin is nowhere to be found in Evolution. But I had some success copying it from:

/usr/lib/evolution/2.24/plugins/liborg-jylefort-mail-notification.so
/usr/lib/evolution/2.24/plugins/org-jylefort-mail-notification.eplug

To the new evolution plugins folder. (I don't remember the version number at the moment.) It did not work as expected, so don't get your hopes up. But that's a good starting point I think.

---

### Post by phyrewall on 2009-03-08
> **ronaldrand said:**
> I upgraded to Jaunty (disastrous!) and had this same problem. Lefort's plugin is nowhere to be found in Evolution. But I had some success copying it from:

/usr/lib/evolution/2.24/plugins/liborg-jylefort-mail-notification.so
/usr/lib/evolution/2.24/plugins/org-jylefort-mail-notification.eplug

To the new evolution plugins folder. (I don't remember the version number at the moment.) It did not work as expected, so don't get your hopes up. But that's a good starting point I think.

Thanks, mate! This worked for me. :KS

---

### Post by ronaldrand on 2009-03-08
> **phyrewall said:**
> Thanks, mate! This worked for me. :KS

I'm so glad it worked for you! None of my programs seemed to work for me. It must be my laptop isn't supported yet.

I'll put these files online for a while in case anyone installs Jaunty without upgrading.

[http://dl.getdropbox.com/u/704812/LeFort%27s%20plugins/liborg-jylefort-mail-notification.so]("http://dl.getdropbox.com/u/704812/LeFort%27s%20plugins/liborg-jylefort-mail-notification.so")
[http://dl.getdropbox.com/u/704812/LeFort%27s%20plugins/org-jylefort-mail-notification.eplug]("http://dl.getdropbox.com/u/704812/LeFort%27s%20plugins/org-jylefort-mail-notification.eplug")

These are chmod 644 and owned and group owned by root.

---

### Post by nomediakings on 2009-04-30
Thanks ronaldrand -- I think the plugin people didn't update the file location from 2.24 to 2.26, so I just cut and pasted it and it works now.

---

### Post by bursucboghy on 2009-05-03
Hi, I have the same issue and I copied the plugin files from 2.24/plugins in to the new version of evolution 2.26/plugins and i found the mail-notification-evolution plugin listed in the Evolution plugins and activated but mail-notification still gives me that error about checking if the plugin is loaded.

---

### Post by habtool on 2009-05-04
> **bursucboghy said:**
> Hi, I have the same issue and I copied the plugin files from 2.24/plugins in to the new version of evolution 2.26/plugins and i found the mail-notification-evolution plugin listed in the Evolution plugins and activated but mail-notification still gives me that error about checking if the plugin is loaded.

I also copied them over and it did not work

---

### Post by gofishel on 2009-05-06
Worked for me too.

---

### Post by lucasgf on 2009-05-07
me too, don't work.

> **habtool said:**
> I also copied them over and it did not work

---

### Post by FokkerCharlie on 2009-05-09
Ace,

Copying the plugins worked for me, too.  Thanks very much for posting that solution.

One small gripe- when I hover my mouse over the new mail icon, I get the tooltip animated as per a normal window with Compiz.  Anyone found a way of getting rid of the effect?

Cheers
Charlie

EDIT:  Problem solved, add !(name=mail-notification) to the compiz animations thingie.

---

### Post by dadodadodado on 2009-05-10
i've solved only by editing the eplug file. in a terminal simply type
 ```
sudo gedit /usr/lib/evolution/2.26/plugins/org-jylefort-mail-notification.eplug
```
and find this line
```
location="/usr/lib/evolution/2.24/plugins/liborg-jylefort-mail-notification.so">
```
replace ```
2.24
``` with ```
2.26
```
save close and restart evolution. This is all you need!

---

### Post by lucasgf on 2009-05-11
dadodadodado, still not working.

THX for attetion.

---

### Post by bursucboghy on 2009-05-11
> **dadodadodado said:**
> i've solved only by editing the eplug file. in a terminal simply type
 ```
sudo gedit /usr/lib/evolution/2.26/plugins/org-jylefort-mail-notification.eplug
```and find this line
```
location="/usr/lib/evolution/2.24/plugins/liborg-jylefort-mail-notification.so">
```replace ```
2.24
``` with ```
2.26
```save close and restart evolution. This is all you need!
Worked for me!
Thanks!

---

### Post by relgames on 2009-05-12
> **ronaldrand said:**
> I upgraded to Jaunty (disastrous!) and had this same problem. Lefort's plugin is nowhere to be found in Evolution. But I had some success copying it from:

/usr/lib/evolution/2.24/plugins/liborg-jylefort-mail-notification.so
/usr/lib/evolution/2.24/plugins/org-jylefort-mail-notification.eplug

To the new evolution plugins folder. (I don't remember the version number at the moment.) It did not work as expected, so don't get your hopes up. But that's a good starting point I think.
Thanks a lot, it works!!

---

### Post by pandu.rs on 2009-05-15
I have upgraded to jaunty and got into the same issue. I got into the same problem as reported in this thread and fixed it now. But now my mail notification windows have a different appearance (It is now popping up like a dialog box with 5-6 buttons and steals the focus). It is quite annoying for me. Anybody facing the same issue? Any solutions?

---

### Post by mdgrech on 2009-05-17
Still having problems.  After copying:

/usr/lib/evolution/2.24/plugins/liborg-jylefort-mail-notification.so
/usr/lib/evolution/2.24/plugins/org-jylefort-mail-notification.eplug

to:

/usr/lib/evolution/2.26/plugins/liborg-jylefort-mail-notification.so
/usr/lib/evolution/2.26/plugins/org-jylefort-mail-notification.eplug

and changing location to read 2.26 in eplug as noted.  Now when I click on add a mailbox in the mail notifications properties window of mail notifer I see a bunch of folders, of which I select inbox.  Than I get a flashing error message in my tray that reads: 

inbox: unable to contact evolution

---

### Post by mdgrech on 2009-05-17
Alright got it, you still have to keep evolution open.  You can't dock evolution to the indicator applet like you can with pidgin which is silly (i'm sure there is a way but you can't do it easily).  second between keeping evolution open with alltray, running mail notification, and constantly running evolution along with all its other processes such as evolution alarm notify sucks up damn near 50mb or ram!  ridiculous.  Even outlook doesn't sux nearly this bad.

This in particular ticks me off b/c we have open source leaders like Richard Stallman openly bashing Gmail and the so called Javascript trap encouraging us to open-source alternatives like Evolution yet we have to go through all this trouble just to get our desktop email client to behave how most people would expect it to behave.

Stallman bashing Javascript technologies like Javascript [article on Tuxradar]("http://www.tuxradar.com/content/avoiding-javascript-trap")

**Edit:** Already in Brain storm, vote for it if you agree:
[http://brainstorm.ubuntu.com/idea/19454/](http://brainstorm.ubuntu.com/idea/19454/)

---

### Post by FokkerCharlie on 2009-05-17
Yes, I am seeing this, too.

I think that some sort of notification in the tray should be default behaviour, and not result in flashing, persistent warnings when Evolution is closed (how DARE we!!).

Unless there's something we've missed?

Charlie

---

### Post by enginuysal on 2009-05-24
Thanks ronaldrand. It worked for me as well.

---

### Post by filiatra on 2009-06-18
Hello! I've been trying to get the notification back in Jaunty for some time.
Thanx for the solution! I had to copy the files in the 2.26/plugins directory and then add mail-notification at system's startup programs.

Now the only thing is the blinking icon reporting "unable to contact evolution" when evolution is not running.. HOW did this just worked fine in 8.10 and is messed up now !!

EDIT: Solution found:
Run

gconf-editor /apps/mail-notification

and uncheck the "blink-on-errors" box.

---

### Post by wa98146 on 2009-06-25
Hi, How do you add the mail-notification to Startup Applications? I opened the Startup Applications then Add, but I do not know where the mail-notification is located. Any help appreciated. Thanks

---

### Post by jcarrete on 2010-02-15
> **pandu.rs said:**
> I have upgraded to jaunty and got into the same issue. I got into the same problem as reported in this thread and fixed it now. But now my mail notification windows have a different appearance (It is now popping up like a dialog box with 5-6 buttons and steals the focus). It is quite annoying for me. Anybody facing the same issue? Any solutions?

I had the same annoying problem. I managed to get ride of the message by

```
gconf-editor /apps/mail-notification
```

And then disabling popups.

Note that in Intrepid there was a nice-looking message near the notification area that would go away on its own in a few seconds unless you rolled the  mouse over it.  As noted above, in the current distribution (evolution version 2.28 under Karmic) I have resorted to eliminate notifications.

Cheers,

jcarrete

---

### Post by afridz on 2010-02-15
actually i came to the forum for the same prob.. any way i got the solution almost.. thanks all

---

### Post by 1jackjack on 2010-03-24
I can confirm that it still works to just copy those 2 plugin files from the 2.24 plugins directory into your version's plugin directory (I'm using evolution 2.28 on ubuntu 9.10), and update the path in the eplug file.

Now in my cluttered panel I have evolution running with alltray next to my mail-notification icon with the number of unread emails in my inbox. God I hate evolution, but it seems to be the best thing that supports MS Exchange, which I have to use at work :(

---

