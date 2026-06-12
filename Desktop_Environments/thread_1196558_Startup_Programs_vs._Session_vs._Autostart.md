---
title: "Startup Programs vs. Session vs. Autostart"
date: 2009-06-25
forum: Desktop Environments
---

### Post by fgysin on 2009-06-25
Hey
Ok, so here is the basic problem I'm encountering: I want my Ubuntu to start some progs for me at startup after logging in.
This sounds quite basic, and as I have understood there actually are actually multiple ways of doing this, pity none works for me... :/

What I tried first:
Saving the currently opened progs in the Systen>Preferences>Session Menu. I tried this in all possible variations of opening programs, saving, or marking the checkmark at the 'automatically save running session' option...
But none of this programs is started after restart except for Pidgin. What dazzled me was that in the view of the current session, and also in the config file (~/.gnome2/session) the saved programs appeared - but they were never started. (Or maybe they were started - at least they were not visible and I could not found any processes in htop...)

What I tried after that was just entering these progs I want to have at startup to the 'startup programs list'. When dealing with this list I also saw that Pidgin was allready in it, so the Pidgin start after reboot was probably due to this fact rather than me saving a session with Pidgin open. At first this worked fine, I entered two gnome-ternimal calls with proper geometry, so they are displayed on my right screen. I also added a third terminal and some other apps, but sadly these were never started...

After some googling I read something about an 'autostart' option or file but was not really sure what it was and if it would help me with my problem. For the worst of it, after some more tinkering with session and startup programs none of my three terminals is started, instead I get Firefox - which is really strange as I am an Opera user who hardly ever uses the Fox and I for sure never entered it in any startup list...

Can it be that there are some conflicts between the different ways of starting progs after startup? (session, startup programs, autostart)



Here are the three terminal calls I entered into startup programs - the first two worked fine for a while, the third never did...
gnome-terminal --geometry=76x27+3200+26
gnome-terminal --geometry=76x27+3840+26
gnome-terminal --geometry=156x27+3200+509
(The problem cannot lie with the geometry setting. First I tried it without as well, second I read the values out of an existing screen session...)

Some information concerning my system:
Ubuntu: 8.04 Hardy
Gnome: 2.22.3
Kernel: 2.6.24-24-generic
CPU: Quadcore Intel(R) Xeon(R) CPU           E5405  @ 2.00GHz

I don't know if this is important but anyway:
I'm using a three-monitor setup. The three monitors are configured to have separate X screens that are linked by Xinerama. (Don't know if this really works like that, at least thats how I understood it.)
Please don't tell me to change anything at the monitor configuration, I had a lot of trouble until everything worked properly and the last two times I only made a small little change everything went bananas and I could start over again. :/


I'd be really grateful if someone could help me with my troubles - all I want is to be able to configure for some apps to start after reboot... I don't care if it is done with sessions or the startup programs list or autostart...

cheers,
Florian

PS: Excuse possible spelling mistakes, I'm not a native speaker.
PPS: I've only had that much experience with linux - I'm using Ubuntu for maybe half a year now.

---

### Post by Brandon Williams on 2009-06-25
First, you're actually only talking about two methods. autostart (or ~/.config/autostart) is the name of the directory where the config for 'startup programs' shows up.

Second, I've had great success with 'startup programs', but none with saving my session. I recommend that you stick with the 'startup programs' method.

Conidering what you're trying to do, start three instances of the same program at startup, I would probably write a script and use specify that script as my startup program. This might make debugging a bit easier, too.

Create a ~/bin directory (if it doesn't already exist) with 'mkdir ~/bin/'. Then use your favorite editor to create a file called '~/bin/startup_terminals'. Then content of the file will be:
```
#!/bin/sh
# uncomment the following two lines for debugging
#exec 2>> ~/bin/startup_terminals.log
#set -x
gnome-terminal --geometry=76x27+3200+26 &
gnome-terminal --geometry=76x27+3840+26 &
gnome-terminal --geometry=156x27+3200+509 &
wait
```
Now set the executable bit on the script with 'chmod u+x ~/bin/start_terminals', and then execute the script to verify that you get the three terminals you want, each in the correct location. The script will not exit until all three terminals are closed. If this doesn't work, then you might need to modify the commands in the script in order to make it work.

After the script starts working, create a single new 'startup application' that will run this script. Log out and back in to verify that the script is doing it's job. If it isn't, then uncomment the two lines used for debugging, log out and back in, and then check the contents of ~/bin/start_terminals.log to see if there is any useful output there.

---

### Post by fgysin on 2009-06-26
Thank you for your answer.
Just wrote the script and it worked just fine instantly, now I get all my three terminals... :)

I still dont quite get why the session thing is not working properly, it began to start all sort of programs at startup without beeing asked for it. (The checkmark to save sessions automatically was off...)
Anyway, I just deleted the session file in ~/.gnome2 and now it stopped now, so thats fine for me.

Very glad to have my nice terminals now... :) 

Thanks again,
Florian

[solved]

---

