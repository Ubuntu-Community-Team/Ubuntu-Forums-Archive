---
title: "Did I just get hacked?!?"
date: 2006-01-07
forum: Desktop Environments
---

### Post by UltraSonicSite on 2006-01-07
Guys did I just get hacked? I was browsing along, minding my on buisnuss when a little screen pops up saying "hi"

Wtf?! I know I wasn't just seeing things either...

I changed my main and root passwords out of fear someones trying to fry my computer, any information I should know about this? Am I being paranoid??!

---

### Post by floyd27 on 2006-01-07
What kind of window did it open in?
kopete/gaim? or somethingelse?

---

### Post by UltraSonicSite on 2006-01-07
it was sort of like a box like this

-----------------------------------------------
hi
-----------------------------------------------

it stood there for about 3 seconds and disappeared

---

### Post by earobinson on 2006-01-07
chances are no, unless you know that some one was trying to hack you then maybe.... should have taken a screen shot.

could have been the website there is an html code for popup msgs, what sites where you at.

---

### Post by UltraSonicSite on 2006-01-07
lol THIS WEBSITE! And it popped up in front of the browser

as for the screenshot, it dissapeared before I could reach the button (print screen?)

---

### Post by earobinson on 2006-01-07
hum... and it was just a msg box?

are you runing any other custom programs... give us a ps -awx

NOTE: the chances of you getting randomly hacked are slim to none, maybe a worm or virus but chances are you have not been hacked, and even worm or virus is slim.

are u running dapper, or breezy? I know that sometimes when I have been debuging programs I have msgbox's like "hi" and "foo" and "x" as markers It could be that the programer of one of the programs that you are running forgot to take it out.

Also you get extra points for changing your password right off the bat

---

### Post by UltraSonicSite on 2006-01-07
Well I restarted my computer, so eh will it still work? Heres what it gives me:

[quote='ps -awx']Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
  PID TTY      STAT   TIME COMMAND
    1 ?        S      0:01 init [2]
    2 ?        SN     0:00 [ksoftirqd/0]
    3 ?        S<     0:00 [events/0]
    4 ?        S<     0:00 [khelper]
    5 ?        S<     0:00 [kthread]
    7 ?        S<     0:00 [kacpid]
   91 ?        S<     0:00 [kblockd/0]
  118 ?        S      0:00 [pdflush]
  119 ?        S      0:00 [pdflush]
  121 ?        S<     0:00 [aio/0]
  120 ?        S      0:00 [kswapd0]
  706 ?        S      0:00 [kseriod]
 2374 ?        S      0:00 [khubd]
 3943 ?        S      0:00 [kjournald]
 4073 ?        S<s    0:00 udevd --daemon
 6629 ?        S      0:00 [kgameportd]
 8112 ?        Ss     0:00 dhclient3 -pf /var/run/dhclient.eth0.pid -lf /var/run/dhclient.eth0.leases eth0
 8648 ?        Ss     0:00 /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acpid.socket
 8663 ?        Ss     0:00 /sbin/syslogd -u syslog
 8680 ?        Ss     0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 8682 ?        Ss     0:00 /sbin/klogd -P /var/run/klogd/kmsg
 8695 ?        Ss     0:00 /usr/bin/dbus-daemon --system
 8708 ?        Ss     0:00 /usr/sbin/hald
 8713 ?        S      0:00 hald-addon-acpi
 8722 ?        S      0:00 hald-addon-storage
 8724 ?        S      0:00 hald-addon-storage
 8769 ?        Ss     0:00 /usr/sbin/gdm
 8780 ?        S      0:00 /usr/sbin/gdm
 8822 ?        R      0:20 /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
 8839 ?        Ss     0:00 /usr/sbin/cupsd -F
 8869 ?        Ssl    0:00 /usr/sbin/hpiod
 8912 ?        S      0:00 python /usr/sbin/hpssd
 9098 ?        Ss     0:00 hcid: processing events
 9104 ?        Ss     0:00 /usr/sbin/sdpd
 9114 ?        S<     0:00 [krfcommd]
 9150 ?        Ss     0:00 /usr/sbin/atd
 9165 ?        Ss     0:00 /usr/sbin/cron
 9208 ?        S      0:00 /usr/bin/timidity -iA -B2,8 -Os1l -s 44100 -iAD
 9212 tty1     Ss+    0:00 /sbin/getty 38400 tty1
 9213 tty2     Ss+    0:00 /sbin/getty 38400 tty2
 9214 tty3     Ss+    0:00 /sbin/getty 38400 tty3
 9215 tty4     Ss+    0:00 /sbin/getty 38400 tty4
 9216 tty5     Ss+    0:00 /sbin/getty 38400 tty5
 9217 tty6     Ss+    0:00 /sbin/getty 38400 tty6
 9244 ?        Ss     0:00 x-session-manager
 9286 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session x-session-manager
 9289 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session x-session-manager
 9290 ?        Ss     0:00 dbus-daemon --fork --print-pid 8 --print-address 6 --session
 9292 ?        S      0:01 /usr/lib/gconf2/gconfd-2 5
 9322 ?        S      0:00 /usr/bin/gnome-keyring-daemon
 9324 ?        S      0:00 /usr/bin/esd -nobeeps
 9326 ?        Ss     0:00 /usr/lib/bonobo-activation/bonobo-activation-server --ac-activate --ior-output-fd=18
 9328 ?        S      0:00 /usr/lib/control-center/gnome-settings-daemon --oaf-activate-iid=OAFIID:GNOME_SettingsDaemon --oaf-ior-fd
 9331 ?        S      0:00 /usr/lib/gamin/gam_server
 9343 ?        S      0:00 xscreensaver -nosplash
 9358 ?        Rs     0:01 /usr/bin/metacity --sm-client-id=default0
 9372 ?        Ssl    0:01 gnome-panel --sm-client-id default1
 9374 ?        Ssl    0:01 nautilus --no-default-window --sm-client-id default2
 9376 ?        Ss     0:00 gnome-volume-manager --sm-client-id default4
 9380 ?        S      0:01 /usr/lib/gnome-panel/wnck-applet --oaf-activate-iid=OAFIID:GNOME_Wncklet_Factory --oaf-ior-fd=29
 9384 ?        Ss     0:00 update-notifier --sm-client-id default7
 9386 ?        Ssl    0:00 gnome-cups-icon --sm-client-id default3
 9388 ?        S      0:00 /usr/lib/notification-daemon/notification-daemon
 9391 ?        Sl     0:00 /usr/lib/gnome-vfs2/gnome-vfs-daemon --oaf-activate-iid=OAFIID:GNOME_VFS_Daemon_Factory --oaf-ior-fd=32
 9400 ?        Sl     0:00 /usr/lib/gnome-applets/trashapplet --oaf-activate-iid=OAFIID:GNOME_Panel_TrashApplet_Factory --oaf-ior-fd
 9404 ?        S      0:00 /usr/lib/nautilus-cd-burner/mapping-daemon
 9409 ?        S      0:00 /usr/lib/gnome-panel/notification-area-applet --oaf-activate-iid=OAFIID:GNOME_NotificationAreaApplet_Fact
 9411 ?        S      0:00 /usr/lib/gnome-applets/mixer_applet2 --oaf-activate-iid=OAFIID:GNOME_MixerApplet_Factory --oaf-ior-fd=40
 9413 ?        S      0:00 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=41
 9442 ?        Sl     1:09 /usr/lib/mozilla-firefox/firefox-bin -a firefox
 9461 ?        S      0:02 gedit
 9630 ?        Rl     0:00 gnome-terminal --working-directory=
 9631 ?        S      0:00 gnome-pty-helper
 9632 pts/0    Ss     0:00 bash
 9644 pts/0    R+     0:00 ps -awx
[/quote]

---

### Post by earobinson on 2006-01-07
well all ps awx (apparenty you dont need the dash but it works fine with it) just tells us whats running, I also edited the above post so if you want to look at it again.

breezy or dapper?

and of let us know if it happens again (same thread, i subscribe to all threads i post in)

---

### Post by UltraSonicSite on 2006-01-07
Alrighty then, just in case i'll post a pic I made that shows how it looked a'ight?

-----
[[IMG]http://img494.imageshack.us/img494/5007/whatitlooklike9sz.jpg[/IMG]](http://imageshack.us)

it popped up and showed for a few seconds

(note it didnt happen on your purticular post, i'm just showing as if it were a webpage)

I think I have breezy.

---

### Post by earobinson on 2006-01-07
go for it, noting looks really funny in your ps awx to me. but it is really weird

---

### Post by UltraSonicSite on 2006-01-07
Ya I was creeped out, my first instinct when something odd happens is to turn of my computer immidiately. In this case I restarted and logged into the terminal and changed the 2 passwords.

---

### Post by earobinson on 2006-01-07
you can find out if its dapper or breezy by doing a "cat /etc/apt/sources.list"

also what browser do you use? ... nm u use firefox (checked your ps awx)

---

### Post by Ptero-4 on 2006-01-07
Hi. Can you check your forum user cp. Since you said you were in this site, I think that the popup can be the PM notification popup. I have mine disabled, but maybe you enabled your and forgot it.

---

### Post by earobinson on 2006-01-07
question... when you hover your mouse over something is the text that comes up on a gray backround (I noticed you had a strange theme)

> Hi. Can you check your forum user cp. Since you said you were in this site, I think that the popup can be the PM notification popup. I have mine disabled, but maybe you enabled your and forgot it.

are you talking about the email notifacation (because that is a center screen megbox)? if not where is that listed

---

### Post by ardchoille on 2006-01-07
If you click on "New posts" and then hover your mouse over one of the posts for a few seconds, you'll see that exact kind of message (but with different text). I am thinking that your browser was just a bit slow and you saw one of those messages. I have seen those in my browser a few times. If that is what it was, there's nothing to be worried about.

---

### Post by earobinson on 2006-01-07
[QUOTE=ardchoille]If you click on "New posts" and then hover your mouse over one of the posts for a few seconds, you'll see that exact kind of message (but with different text). I am thinking that your browser was just a bit slow and you saw one of those messages. I have seen those in my browser a few times. If that is what it was, there's nothing to be worried about.[/QUOTE]
ya thats what I thought it might be hence asking what color it was when he hoverd over things

---

### Post by UltraSonicSite on 2006-01-07
haha well if I guess your right, only one problem with your therioe(sp?), the box that popped up was no where NEAR a button or link or even text for that matter. As for the pm thing, lemme check into that

Ya I used firefox, and the box didnt have an outline like when I go over the quote button or reply button.

btw, where does a link on the forums pop up a message that says hi? =P

---

### Post by ardchoille on 2006-01-07
[QUOTE=UltraSonicSite]haha well if I guess your right, only one problem with your therioe(sp?), the box that popped up was no where NEAR a button or link or even text for that matter. As for the pm thing, lemme check into that

Ya I used firefox, and the box didnt have an outline like when I go over the quote button or reply button.

btw, where does a link on the forums pop up a message that says hi? =P[/QUOTE]
That little "Hi" message usually pops up wherever my mouse cursor is at the time, but I have noticed a little bit of lag sometimes.

---

### Post by UltraSonicSite on 2006-01-07
Hey, ya know what, I'll take that as a temporary answer to what happened. If all goes well well just blame it on my "damn slow browser", Firefox. =)

Still very odd though, cuase it didn't have a border, that's what is wierd about it. and it was longer than it needed to be:

--------------------------------
hi
--------------------------------

if it was a button or link it would be

 ---
|hi |
 ---

---

### Post by cwaldbieser on 2006-01-07
[QUOTE=UltraSonicSite]Hey, ya know what, I'll take that as a temporary answer to what happened. If all goes well well just blame it on my "damn slow browser", Firefox. =)

Still very odd though, cuase it didn't have a border, that's what is wierd about it. and it was longer than it needed to be:

--------------------------------
hi
--------------------------------

if it was a button or link it would be

 ---
|hi |
 ---[/QUOTE]

Whenever you hover over the link to any thread or post on the forums, a tooltip with the first line of the post pops up.  It is so you can get a quick summary without having to follow the link, because lots of times the subject doesn't really explain the thread too well.  However, since most people are relatively polite, the start out with something like "Hi!", "Hello", "Greetings,", or "Help!" on a line by itself.  This unfortunately doesn't give much help in figuring out what the thread is about.  It would probably be better if it stripped out newlines and showed a fair chunk of text.

---

### Post by dcraven on 2006-01-07
These guys are correct. It was just the post preview of a forum post whose first line was the single word "hi". I've seen this happen before, and it's not rare that posts begin like this. It's nothing to worry about.

HTH,
~djc

---

### Post by UltraSonicSite on 2006-01-07
Alright guys. Thanks for trying.

(although the popup came up while looking at a post through the middle of the page. I understand this though, in windows when you were in internet explorer sometimes a lil message like that pops up and stays even when you move the mouse away.)


The reason i'm thinking so much about it is because in windows I tested out this hacking program on myself, and I sent my computer a message that said hello or some crap, then a window would show up for a few seconds before leaving. And if the message worked then I could litterally do anything I wanted on my own computer, like delete files and crap.

The same as if I was doing it on someone else. (Don't worry though, my attempts at getting the damn thing to work against someone else's computer failed miserably) =P

(I do realize this is linux, not windows, but hey - heh its just what I think)

---

### Post by earobinson on 2006-01-11
I was looking into your bug a bit more, Im on windows right now (at work) but I was able to make firefox do what you said happened. Steps to make this happen:
1. Go to [New Posts]("http://www.ubuntuforums.org/search.php?do=getnew&exclude=121")
2. Click a link (make sure after clicking the link you dont move the mouse)
Now when the new page loads whatever the popup of the link you click was will appear for some seconds

[Screen Shot]("http://earobinson.blogspot.com/2006/01/re-did-i-just-get-hacked.html")

Hope this helps, you try it tell us if its the same thing. This is infact a firefox bug.

---

### Post by UltraSonicSite on 2006-01-29
Okay thanks alot =)

---

