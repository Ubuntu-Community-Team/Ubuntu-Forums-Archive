---
title: "Firefox Help needed!"
date: 2005-12-16
forum: General Help
---

### Post by Lofticus on 2005-12-16
Hi Guys (and girls of course),

Everytime I start firefox, my homepage will be [www.arizona.edu](www.arizona.edu) (but under preferences I set my Home to about:blank)

How can I change this? It buggs me to no end!

I'm using firefox 1.5

Plz help!

(grep -r arizona * in my .mozilla doesn't spit out anything, besides in my history.dat and in my Cache)

---

### Post by canadianwriterman on 2005-12-16
This might work...

Edit the ~/.mozilla-thunderbird/[profile_dir]/prefs.js file and add (or change) the following:

Code:
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");Your path to firefox may be diferent.

Then, in firefox, open the advanced section of the preferences and in "Tabbed Browsing - Open links from other applications in:", select "a new tab in the most recent window".

---

### Post by Lofticus on 2005-12-16
It didn't help )-:

---

### Post by earobinson on 2005-12-16
do you have any extentions installed that could be causing this?

---

### Post by Lofticus on 2005-12-16
I have a lot. Like Sessionsaver or tabbed browsing.

But it did work before, so I can't see why it should do this now.

(I have: DOM Inspector 1.8, Talkback, DownThemAll, Sessionsaver .2, Adblock, Tabbrowser Preferences, Fasterfox and StumbleUpon)

---

### Post by Lofticus on 2005-12-16
oh and it told me that I can't finish Chrome registration

---

### Post by pizzach on 2005-12-16
Worst case senerio:  just try starting fresh.  Make sure to bookmark where you got the extensions.  Maybe open them all in tabs and bookmark the group.  Then export your bookmarks to a file in bookmark manager.  Then go to your firefox profile and just delete it and start a new profile.  One way of that would be going to the terminal then nuking the whole mozilla directory with rm.  (rm -r .mozilla)

Then reimport your bookmarks throuh bookmark manager.  Then set up your preferences for about:blank.  NOW install the extensions.   (Though they shouldn't be causeing a problem now anyway.)

This would be a last option thing because it's a pain in the neck backing everything up and getting it all back.

---

### Post by Lofticus on 2005-12-16
I did... Still it doesn't work.

New profile also sets [www.arizona.edu](www.arizona.edu)...

that makes me wanna puke :P

Any1 has an other idea?

---

### Post by pizzach on 2005-12-16
Have you tried "sudo firefox"?  It sounds like there are some privilege issues by reading the install firefox thread.  I installed firefox from the mozilla.com website which is just a tar gziped file.

---

### Post by Lofticus on 2005-12-16
you mean that I start firefox with "sudo firefox"?

No, I didn't. 

I installed it per installerscript here in the forum

---

### Post by earobinson on 2005-12-16
try turning all your extentions off, im betting Sessionsaver has a bug

---

### Post by pizzach on 2005-12-16
It's the same chrome errer they are having on the installer script thread.  There is a fair chance that there is a connection.

---

### Post by Lofticus on 2005-12-16
[QUOTE=earobinson]try turning all your extentions off, im betting Sessionsaver has a bug[/QUOTE]

I deleted my extensions by making a new profile.

So Sessionsaver cannot be the fault.

---

### Post by earobinson on 2005-12-16
[QUOTE=Lofticus]I deleted my extensions by making a new profile.

So Sessionsaver cannot be the fault.[/QUOTE]
sorry I dident see that. my bad. Uninstall, Reinstall firefox?

---

### Post by Lofticus on 2005-12-16
that somehow doesn't work, if I make sudo apt-get remove mozilla-firefox and then install it again, it won't start.

Says another instance is already running and that I should close that window first.

Well, ps -e shows, that no instance of firefox is running. 

)-:

---

### Post by pizzach on 2005-12-16
Not, sudo apt-get.  We are not installing or removing anything right now.  I'm saying **run** firefox with sudo.  Therefore to run firefox 1.5, depending on how the package in installed would be
```
sudo firefox
```

The idea is if the preference is root access only, you should be able to edit it with root.  This is not a fix, it is a test.

---

### Post by earobinson on 2005-12-16
I think its a problem with your lock file [http://www.aims.ac.za/wiki/index.php/Linux_Frequently_Asked_Questions_(FAQ](http://www.aims.ac.za/wiki/index.php/Linux_Frequently_Asked_Questions_(FAQ))

---

### Post by Lofticus on 2005-12-16
[QUOTE=earobinson]I think its a problem with your lock file [http://www.aims.ac.za/wiki/index.php/Linux_Frequently_Asked_Questions_(FAQ](http://www.aims.ac.za/wiki/index.php/Linux_Frequently_Asked_Questions_(FAQ))[/QUOTE]

that link doesn't provide any text 

pizzach:

what after starting firefox with sudo?

---

### Post by pizzach on 2005-12-16
Edit your home page and see it if sticks.

---

### Post by Lofticus on 2005-12-16
Pizzach: you rock (-: thx man, after starting firefox with sudo, then starting without sudo, my homepage is google again

testing with about:blank, but I think it will work!

Thanks to all of you, you spared my Comp the death by a frustrated user hehe...

---

### Post by Lofticus on 2005-12-16
what the heck? I just found out what the error was

In my startet firefox was started with 'firefox %u'

So starting firefox in my starter makes arizona.edu appear, without, it disappears.

Strange!!

Thx anyways guys, it did help (: (I would never have looked into the starter)

---

### Post by pizzach on 2005-12-16
Rocky ride.  But at least you figured it out.  :)

---

### Post by Lofticus on 2005-12-16
Still wonder what the %u is for.. (:

---

### Post by Mr. Electric Wizard on 2005-12-16
I was starting to wonder if maybe you were connecting to the internet via a public WAP.
When I connect at say Panera Bread, I get re-directed to [www.panerabread.com](www.panerabread.com), instead of what my Firefox Home Page is ([www.google.com)](www.google.com)).

---

### Post by Lofticus on 2005-12-16
No, Its a normal LAN-Router-Internet connection

---

### Post by BrooksOfSheffield on 2005-12-16
Are you launching it via terminal or a launcher?  If via launcher, what's the actual command being passed?

[[edit]]
Nevermind.  You solved the issue already.

---

### Post by DarkAngel88 on 2005-12-16
Hey,

I was about to reply with a solution.  I use to have the same problem with my firefox.  I was starting firefox with the "%s" option.  My start page was [www.mcdonalds.com](www.mcdonalds.com) !!!  But after removing the %s option, everything went back to normal !

Glad you have found the problem by yourself !!

---

