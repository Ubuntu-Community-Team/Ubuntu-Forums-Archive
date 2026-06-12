---
title: "Does Ububtu ' remember ' failed jobs and loop forever?"
date: 2007-09-25
forum: Desktop Environments
---

### Post by johnbl on 2007-09-25
I have a notebook that starts up in two stages, first as normal, user name, password then pink screen for 12 MINUTES!

I reported every thing I could see but - Gnome vfs mailing list xsession errors - didn't get any responses.

Could there be a ' job ' uncompleted that boot sequence simply returns too until some time out occurs. I noted in a log that it was attempting a write of a jpeg image now long gone as are the source directory. 

Would this be a ' cron ' job maybe and how can these things be flushed?

John

---

### Post by Wolki on 2007-09-25
> **johnbl said:**
> Would this be a ' cron ' job maybe and how can these things be flushed?

Unlikely. I assume this is a broken session. Do the following:

Press Ctrl-Alt-F1 while not logged in
Log in on the console
enter: "mv ~/gnome2/session ~/gnome2/session.backup"
logout ("exit")
Press Ctrl-Alt-F3
login at the Login screen

Does this fix your problem?

---

### Post by johnbl on 2007-09-26
Thank you thank you. 

Will check that out soon as I get back home. 
One point, " while not logged on '?

Do I do this at the normal log on screen, that's the way I'll try it, or ?

John

---

### Post by Wolki on 2007-09-26
> **johnbl said:**
> 
Do I do this at the normal log on screen, that's the way I'll try it, or ?


Exactly, that's what I meant.

---

### Post by johnbl on 2007-09-26
Tried that idea however;

" cannot stat /home/john/gnome2/session  no such file or directory "

ls doesn't show up a directory gnome or gnome2. " Find session"  refuses to do zip, but never have been able to make find work...

In powering down  I did note an error highlighted along the lines of zero length file in mail, mail system possibly broken.

Also noted wifi-radar, a package that I think might be at the original root of these problems, seems to still be resident if well hidden. Ostensibly it was removed but still getting a Guernsey !

But as there were at least two occasions when the system simply went into disk thrash and refused to accept any key board or power button hits, your suggestion of a busted session seems to be the very best bet.

Where now?

---

### Post by Wolki on 2007-09-26
> **johnbl said:**
> 
" cannot stat /home/john/gnome2/session  no such file or directory "

:oops: Sorry, I made a typo. It's "~/.gnome2/session", with a dot before the gnome2.

---

### Post by johnbl on 2007-09-27
Wolki,
Thanks for that. Still zip however.  Same error message as before in console.

Have searched the system and can find NO  "session" file, nor .gnome2 directory. Does this mean something has deleted some critical ' bit '?

John

---

### Post by Wolki on 2007-09-27
> **johnbl said:**
> Have searched the system and can find NO  "session" file, nor .gnome2 directory. Does this mean something has deleted some critical ' bit '?

You don't havce a .gnome2 directory? That's *very* odd, unless you haven't run gnome yet. A good number of gnome programs keep stuff in there.

A directory with a dot is hidden, and you need to enable "Show Hidden Files" (View menu) or use ls with the -a parameter to show them.

Can you try to add another user (if you can't start gnome, use "sudo adduser test") and see whether everything starts up ok for that user?

---

### Post by johnbl on 2007-09-28
Wolki,

Thanks for your perseverance in helping me with this. Learning a lot at this end as to just how broken my system is and amazed it still works so well despite the obvious problem/s..

It will come as no surprise I sure to hear that you were right.. There IS a .gnome2 directory. " ls -a "  showed it up when having ' Show Hidden Files ' selected in File Browser didn't!

Had a peek into the directory and no session file there however!

Attempted to add a new user as you suggested, however interestingly enough the " Users and Groups " button is showing up with a red dot containing a "!" added and the window that opens is wholly white, empty, and refuses input, including closing.

Getting deeper into the mire here <g> any more ideas as to where next ... ?


John

---

### Post by Wolki on 2007-09-28
> **johnbl said:**
> Getting deeper into the mire here <g> any more ideas as to where next ... ?

Try adding the user from a terminal: "sudo adduser test" or some other username instead of test if you want.

There seems to be something completely wrong on your computer. We'll need to find out whether it's system-wide corruption or whether it only affects your user account.

If it's the last one, we might try to find the file making the problem, or migrate your data to the new account. If the whole system is damaged it probably could still be rescued, but a new install might be better unless we find the root of the problem.

Do you have an idea what might have caused this? Did you do anything unusual before this happened?

---

### Post by johnbl on 2007-09-29
Wolki,

Added the test user as suggested. 

* Seemed to work in that the user was accepted, password names numbers..

rebooted and tried using it, same hang post user name / password, but this time it never completed. I gave up after 10 minutes.

Rebooted in old name, same hang point, but 3minutes 40s. So no real change there.

System > Admin > Users and  Groups , till has small exclamation mark, opens as empty and refuses to close, no change there!

Only things different I have done, if different is the right word was;
install wi-fi radar - possibly ineptly as that never worked as advertised. Uninstalled that however vestiges seemed to remain. Then of course there was the disk thrashing episodes that I think might be either behind this or a early symptom where all input  was refused and system had to be killed by removal of the battery.

If you can't see anything in the logs I supplied in the other thread - - Gnome vfs mailing list xsession errors - could be a reinstall is the only way ' out '. But does seem like a shotgun approach to a air rifle sized problem.. Trick is the knowing of what to shoot though and that's proving very illusive to say the least!

Is there a way to do a repair install that replaces the core OS without trashing the system and all settings etal?

If so that might be the only way out of this

John

---

### Post by Wolki on 2007-09-29
> **johnbl said:**
> 
If you can't see anything in the logs I supplied in the other thread - - Gnome vfs mailing list xsession errors - could be a reinstall is the only way ' out '.

Ah, I didn't understand from your first post that you posted detailed logs already... I'm sorry.

They turned out to be quite intteresting. Four problems I noted:

- Nautilus cant thumbnail a file (which shouldn't be the cause of such a large problem, but if it persists we should probably try to get rid of it)
- Nautilus can't find some mimetypes (which would, since it's a system-wide problem, lead me to believe something has happened to your shared mime database, but these mimetypes aren't defined there...)
- gnome-settings-daemon crashes. This is generally very bad.
- This didn't hit me immediately, but only after I googled some of the errors: If the output of your ifconfig is complete, you don't have a loopback device! That's something that could lead to serious errors, and might have happened when installing that wifi-thing.

Let's see if that is the cause:
Open "/etc/network/interfaces" in your favorite text viewer/editor (if you need to edit, you will need superuser rights).
That file must contain two lines looking like:

```
auto lo
iface lo inet loopback
```

And these lines mustn't be commented out (ie, have a # in front of the text)

If you don't have them, add them back. Then restart and see whether it's faster now.

---

### Post by johnbl on 2007-09-30
Wolki,

Thanks for your perseverance with this. Much appreciated I assure you.

Interfaces did have the lines suggested, not commented out.

Did note that I couldn't initially GEDIT the file however permissions were set to owner only rw, chown to rwx r r .

Whilst that made it possible to open the file in GEDIT with sudo , made zip difference to the problem.

Did note a  ' new ' bug bear. Opening another window caused all the desktop controls to disappear and there was nothing for it but to use the power down button.


Noted that in ' Sessions ' Network Manager was not selected. Selected and restart. Message reports Network manager unable to find some resources. 
Opened up Synaptic Package manager and reinstalled all the Network apps.. Made no difference to message or the core slow start problem either!

Anything else suggested in the logs that I could check / alter?

John

---

### Post by Wolki on 2007-09-30
I'm sorry, my ideas are running out :-( It's probably a solvable problems (most things tend to be), but I don't know what could cause this.

---

### Post by johnbl on 2007-10-01
Wolki,

Thanks for your help. Really difficult diagnosing a problem one  removed from the system - and dealing with a dolt on the other end! <VBG>

You've helped walk me through some areas I didn't know and tightened the focus on the problem.

As luck would have it, I had a ' wonder ' this AM about the network being at the root of it all. Being a notebook on a switch that's itself downstream of a ADSL Modem Router there is no LAN until the switch is powered up. Left it off for the boot sequence and lo, system came straight up!

Haven't tried a reboot to confirm it was LAN absence but it sure tightens up the possible sources of the problem.

Are you aware of any process I could use to completely reload / install  all networking / network manager ' facilities ' by any chance?

Thanks for everything

John

---

### Post by Wolki on 2007-10-01
> **johnbl said:**
> 
As luck would have it, I had a ' wonder ' this AM about the network being at the root of it all. Being a notebook on a switch that's itself downstream of a ADSL Modem Router there is no LAN until the switch is powered up. Left it off for the boot sequence and lo, system came straight up!

Great! :) Good job finding that.


> Are you aware of any process I could use to completely reload / install  all networking / network manager ' facilities ' by any chance?


Not really. You can of course reinstall network-manager with synaptic, but I don't know that much about networking and how it's done automatically, just how to change some things manually.

But could you post the contents of your /etc/hosts file?

---

### Post by johnbl on 2007-10-02
Wolki,

Hosts file is ;
---------------------------------------------

127.0.0.1 localhost
127.0.1.1 interserve3

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

-----------------------------------------------
host.conf is;

-----------------------------------------------

# The "order" line is only used by old versions of the C library.
order hosts,bind
multi on

--------------------------------------------------
and  hostname is

---------------------------

interserve3

----------------------------
is that right?

John

---

### Post by Wolki on 2007-10-03
One thing you could try is commenting out the first two lines of /etc/hosts, and creating a new line to make it look like this:
```

#127.0.0.1 localhost
#127.0.1.1 interserve3
127.0.0.1 localhost interserve3
```

---

### Post by johnbl on 2007-10-03
Getting depressed here.
Thanks for the very good suggestion. Attempted to apply it but " Sudo gedit hosts"  refused to open the damb file. Cursor sits and blinks, forever.

Change permission to include execute. did, but gedit still didn't work. tried rename got a Perl error, or that's what's it's described as when I googled it. 

Now hosts is not visible using ls but the system wont let me create a hosts file...

So now there is no network connection from the box ..

A crack is appearing in my welded to Ubuntu joint I'm afraid .....

I'll give it another shot, but it's getting to either reinstall and try setting up every damb thing all over again - just when it does what is required it breaks isn't much of a feature I figure ..

OR

Find out how a ' recovery ' install can be done. Something MUST surely be available to repair a system that's going slowing mad.

---

### Post by johnbl on 2007-10-04
success of sorts, manged to recreate the hosts file form a clean reboot sans network.
So at least I'm back on air <VBG>

Looking into the networking forum to see what's there about reinstall of networks but most appears to be about wireless.

John
A much happier camper

John

---

