---
title: "Set session startup order ?"
date: 2009-03-27
forum: General Help
---

### Post by RavanH on 2009-03-27
Hi,

I have been using first Wengophone now QuteCom a long time now but it as been a while now that QuteCom when started from Sessions (gnome-session-properties) does not show the tray icon. It does start and opens up the contact window but no tray icon.  

However, if I start the app from menu (or terminal) after login, the tray icon is there as it should. So I wonder if another command in the session startup list is interfering here and maybe changing the order in which the programs are started can help me getting around this... I would want to see if moving the qutecom command to run last helps in any way.

But then, I see no way to set/change/influence the order in which the commands in gnome-session-properties are run :(

Is this (or something similar) at all possible?? Thanks for any advice.

---

### Post by drs305 on 2009-03-27
One way to do this is write a small bash script. Replace the sessions startup command with the script file ( /path.to.script/scriptname.sh )  Make sure it is executable (chmod +x /path/scriptname.sh) 

Use the sleep command as the first command. As the second command input the command that is currently run in sessions startup.
> 
#! /bin/bash
sleep 20
/path/current.sessions.startup.command &   # Example:  /usr/bin/gimp 


---

### Post by RavanH on 2009-03-30
> **drs305 said:**
> One way to do this is write a small bash script. Replace the sessions startup command with the script file ( /path.to.script/scriptname.sh )  Make sure it is executable (chmod +x /path/scriptname.sh) 

Use the sleep command as the first command. As the second command input the command that is currently run in sessions startup.

Thanks ! That did the trick :)

I created a new file called qutecomdelayed with content ```
#! /bin/bash
sleep 20
/usr/bin/qutecom -b &
``` in my home folder, made it executable and replaced the normal session startup command with the full path to the new script and now QuteCom starts *with* a tray icon again :)

Would it be possible to include the sleep 20 command straight in the sessions startup list? Like ```
sleep 20 | /usr/bin/qutecom -b &
``` or something?

---

### Post by drs305 on 2009-03-30
> **RavanH said:**
> 
Would it be possible to include the sleep 20 command straight in the sessions startup list? Like ```
sleep 20 | /usr/bin/qutecom -b &
``` or something?

I don't think Sessions works that way, although you could try it. The command, when strung together, would be:
```
sleep 20 && /usr/bin/qutecom -b
```
It works on the command line but not in Sessions - at least not as entered as above.

Putting a "&" in a script allows two commands to be run concurrently. Putting a "&&" between the commands forces the first command to complete before running the second command. So in this case you would want the "&&".

---

### Post by RavanH on 2009-03-30
> **drs305 said:**
> I don't think Sessions works that way, although you could try it. The command, when strung together, would be:
```
sleep 20 && /usr/bin/qutecom -b
```
It works on the command line but not in Sessions - at least not as entered as above.

Putting a "&" in a script allows two commands to be run concurrently. Putting a "&&" between the commands forces the first command to complete before running the second command. So in this case you would want the "&&".

That did indeed not work... too bad. Strange though that it is not possible to change the startup order in Sessions. Am I the only one that has a need for that?

Anyway, the shell script solution works dandy. Thanks again :)

---

### Post by plamen_todoroff on 2009-04-02
No, you're not the only one :) I also would like to be able to sort the oder in which startup tasks start, and particularly those that came with the fresh install of the system (bluetooth manager, network manager, power manager, etc), as the other that I added manualy to the list are pretty easy to handle via a startup-script.sh with a sleep n && command.

The reason I want that is that I like my notification tray icons arranged in a certain order, and the only way to do this seems to be via gnome-session-properties dialog window. All the startup system applications I'm referring reside in /etc/xdg/autostart, but Ubuntu seems to start them all at the same time without any particular pattern or order, so they end up in the notification tray (no problem with that) but the order is different at each login.

The order option in the "current session" tab (in gnome-session-properties) seemed unable to be saved, it reverted back to the default 50 after logoff and login. But then I fixed the numbers of the applications to 55, 60, 65, etc and hit "save session", a file called .sessions appeared in /home/plamen_todoroff/.gnome2 and priorities were in it, easy to be changed. I did exactly that, rebooted, and... still a "mess" in the systray.

> I don't think Sessions works that way, although you could try it. The command, when strung together, would be:
Code:

sleep 20 && /usr/bin/qutecom -b

It works on the command line but not in Sessions - at least not as entered as above.

Putting a "&" in a script allows two commands to be run concurrently. Putting a "&&" between the commands forces the first command to complete before running the second command. So in this case you would want the "&&".

I tried that as a last resort, but the applications didn't even started at all after next login.

The later seems as the most elegant solution to fix the lack of sort ordering of startup applications in Gnome in general, not just my case, and I think that 

```
sleep 20 && /usr/bin/nm-applet --sm-disable
```

(that was one of my startup attempts in gnome-session properties btw), is not working only because of the SYNTAX of the command.

I'm not in any way a sleep command or a gnome-session properties guru, but I hope someone is and I'll wait for a reply. Thanks.

(Forgive my english.)

---

### Post by drs305 on 2009-04-02
> **plamen_todoroff said:**
> No, you're not the only one :) I also would like to be able to sort the oder in which startup tasks start, and particularly those that came with the fresh install of the system (bluetooth manager, network manager, power manager, etc), as the other that I added manualy to the list are pretty easy to handle via a startup-script.sh with a sleep n && command.


plamen_todoroff,

These system-wide programs are started during boot and the order is set by the S[COLOR="Red"]XX[/COLOR] designation at the start of the link name in /etc/init.d/rcX (rc2, rc3, etc). You might be able to change the number in these folders to get a particular process to start earlier or later than it currently does. This would be tweaking system startup files, so you don't want to be doing this without some knowledge. Do a search on "runlevels" to learn more about the process. 

Here is an older link which discusses changing the boot order of various services:
[http://ubuntuforums.org/showthread.php?t=89491]("http://ubuntuforums.org/showthread.php?t=89491")

---

### Post by plamen_todoroff on 2009-04-02
> These system-wide programs are started during boot and the order is set by the SXX designation at the start of the link name in /etc/init.d/rcX (rc2, rc3, etc).

No, they aren't. They are user session specific and if you look at my previous post again you'll see that when I added the sleep 20 && command to start nm-applet, it didn't start at all, so it's not rcX connected.

Maybe I should attach a screenshot, just to clear things up. The applications that I would like to be able to start in a specific order are:

[LIST=1]
[*][COLOR="DarkOrange"]fusion-icon[/COLOR] (I want it to start first and be the first/right icon in notification area, so no "sleep" here.
[*][COLOR="DarkOrange"]nm-applet --sm-disable[/COLOR] a.k.a Network Manager in the list (sleep 2 && nm-applet --sm-disable).
[*][COLOR="DarkOrange"]gnome-power-manager[/COLOR] (see screenshot, with the highlited "sleep 3 &&" doesn't start at all, so I'm looking for different syntax, as I said none started with sleep prefixed either...
[*][COLOR="DarkOrange"]tracker-applet[/COLOR] (sleep 4 && tracker applet).
[*][COLOR="DarkOrange"]bluetooth-applet -singleton[/COLOR] a.k.a Bluetooth Manager in the list (sleep 5 && bluetooth-applet -singleton).
[/LIST]

Colored in orange are the original, untouched entries in the list, and in the brackets are the desired.

I hope finally someone understands, and explain why 
```
sleep 4 && tracker-applet
```
works in terminal and not in session-properties, so I could have my perfect desktop?

---

### Post by drs305 on 2009-04-02
plamen_todoroff,

My thought was that you could somehow bypass the user-specific settings and use the rc.X settings. 

It appears like there might be another way. Looking at the /etc/xdg/autostart ".deskop" configuration files, you might be able to place the delay there. If you look at /etc/xdg/autostart/evolution-alarm-notify.desktop there is a delay built in. This isn't included in most of the other ".desktop" configuration files but probably could be. Note it looks like you would not use "sleep XX &&" but "sleep XX;" into each of the other .desktop files you want to modify.
> 
[Desktop Entry]
Name=Evolution Alarm Notifier
Comment=Ensures that alarms set in Evolution go off at the appropriate time
Icon=stock_alarm
Exec=sh -c "sleep 30; exec /usr/lib/evolution/2.26/evolution-alarm-notify"
Terminal=false
Type=Application
OnlyShowIn=GNOME;
Categories=
X-Ubuntu-Gettext-Domain=evolution-2.26


Best of luck.

[COLOR="DarkRed"]
**ADDED**:[/COLOR]  I was called away on a business trip and away from my main computer for a few days. While I found the delay code embedded in one of the /etc/xdg/autostart files, the files to work with would most likely be the .desktop files in ~/.config/autostart. I provided the format above because it's the only place I found the delay code embedded in one of the .desktop files.  If I have time at the hotel I'll try to experiment. If I achieve anything I'll put it in a new post.

---

### Post by plamen_todoroff on 2009-04-02
drs305, you can't imagine what a discovery you've made with that evolution-alarm-notify!!!

I've been serching how to sort the order of starting *.desktop startup files in /etc/xdg/autostart for like a month. I remember that I've read about a 200 pages of gnome desktop specifications just to find about xdg (seems to be a new concept), and *.desktop files as a way of startup session entries.

I can't beleive I've missed that evolution-alarm-notify.desktop file, maybe it's because I've never used evolution :) I'm pretty sure I checked the others in /etc/xdg/autostart :)

Thank you! I can't wait to go to bed and start fiddling with the issue tomorrow morning, fresh headed, haven't slept for 48 hours, but I sense tommorow is going to be one fine day!

---

### Post by drs305 on 2009-04-02
I've done a bit of testing and can expand on what I added to my previous post.

In System, Preferences, Sessions (Startup Applications in Jaunty), add your desired apps. This will create a file in ~/.config/autostart called *.desktop. Open this file with a text editor. It will look something like this:
```



[Desktop Entry]
Type=Application
Name=gedit
Exec=gedit
Icon=system-run
Comment=

```

Edit the "Exec" line to add the desired delay.
Notes: 
1. gedit and gnome-terminal, the two apps I played with, did not require full path names, but it may not be a bad idea anyway.
2. The delay I set usually timed out about delay+20 from the time I hit ENTER on logon.
3. The blank first line was in all the original files.
Here is how I changed it and what worked for the 2 apps I tried:
```



[Desktop Entry]
Type=Application
Name=gedit
Exec=bash -c "sleep 20; /usr/bin/gedit"
Icon=system-run
Comment=

```

The apps opened in the order I set the delay. Tweaking of the delay times may be necessary to put them in the correct order, allowing for processing time of the app's opening.

***Please post your results here.*** I've seen this question posed before but not answered. If you can get it to work properly I would be glad to make a quick guide for the tutorials section. If you have problems I'd like to hear them as well. 

If anyone knows of a gui app that can set the start up order of the Sessions/Startup Applications list please post - then a guide wouldn't be necessary.

---

### Post by plamen_todoroff on 2009-04-03
```
Exec=sh -c "sleep 30; [COLOR="Red"]exec[/COLOR] /usr/lib/evolution/2.26/evolution-alarm-notify"
```

What is the role of the "exec" command here? I see that in your example with "gedit" the exec command is missing. I googled around and find that there is a difference whether we use

```
Exec=bash -c "sleep 20; /usr/bin/gedit"
```

or

```
Exec=bash -c "sleep 20; [COLOR="Red"]exec[/COLOR] /usr/bin/gedit"
```

Example, open terminal and try:

```
gedit
```

Then try:

```
exec gedit
```

You see how in the second example the terminal closes when you close gedit.

So which one should I use to modify *.desktop files in /home/name/.config/autostart?


[COLOR="Red"]ADDED:[/COLOR]
I think I understand what's happening: if I don't use the [COLOR="Red"]exec [/COLOR]command in the [COLOR="Red"]Exec=[/COLOR] line, my conky shows 5 more processes (*sh *ones) at startup (usually I have 236, after tweaking 5 *.desktop files I got 241). So I added the [COLOR="Red"]exec [/COLOR]command and now I have 236 again :) and they start the way I want them! Superb!

---

### Post by RavanH on 2009-04-03
@plamen_todoroff

Although I cannot imagine why you would want to be so particular (the word an@l springs to mind; sorry, I don't know you so that is inappropriate but still...) about the order in which tray icons show up I would like to thank you for hogging my thread ;) since it resulted in a working solution!

@drs305

You :guitar: dude! 

When I paste the command ```
bash -c "sleep 20; exec /usr/bin/qutecom -b"
``` straight at the Command line under Edit Session Startup Programs list (or whatever in English version), my QuteCom client starts delayed and works again! No need to edit the .desktop config file manually -- nor setting up some sh script. No fuss, this simply WORKS !!

Thanks!

---

### Post by plamen_todoroff on 2009-04-03
It passed through my mind that I should post a new thread, really, but your thread contained lots of useful information that I wanted to use to describe my "problem". I think that your initial problem and my issue are so connected that, in the interest of a free and open society, merging both was the only way to achieve some kind of a result that could be helpful to the community.

By the way, adding

```
bash -c "sleep 20; exec /usr/bin/qutecom -b"
```

in the command entry field under Edit Startup Program Sessions dialog, is doing exactly that - editing the corresponding *.desktop file in /home/login/.config/autostart. Just two different approaches with same result.

;)

PS: It's not the question why I need to sort my notification area icons, but could it be done, that is relevant here.

---

### Post by RavanH on 2009-04-03
> **plamen_todoroff said:**
> It passed through my mind that I should post a new thread, really, but your thread contained lots of useful information that I wanted to use to describe my "problem". I think that your initial problem and my issue are so connected that, in the purpose of a free and open society, merging both was the only way to achieve some kind of a result that could be helpful to the community.
No need to explain. I was not kidding when thanking you for joining.

> 
By the way, adding

```
bash -c "sleep 20; exec /usr/bin/qutecom -b"
```

in the command entry field under Edit Startup Program Sessions dialog, is doing exactly that - editing the corresponding *.desktop file in /home/login/.config/autostart. Just two different approaches with same result.
I know that. It just seems much less geeky to do it this way. Both the problem and the beauty of Linux OS'ses is (still) the geekiness of its possibilities. I mean, despite *huge* improvements in usability, some things still need manual tinkering. Not too difficult for users like I am, *with* the help of good tutorials and community support, but still... That is why I prefer to use Linux while I still would not recommend is to my mother (for instance), since she cannot be expected to browse forums like these and find some tutorial to fix some obscure thing like this. (sorry, off-topic)

> PS: It's not the question why I need to sort my notification area icons, but could it be done, that is relevant here.
Agreed. And I have to admit, you have an exiting Desktop going on ;) Is that Cairo Dock at the bottom or AWN ?

---

### Post by drs305 on 2009-04-03
RavanH,

Please permit me to add one more thing to your thread. 

It occurred to me that many users would probably have *nautilus* in their sessions. To place the sleep command with nautilus, the simple command sequence of just *[COLOR="DarkSlateBlue"]bash -c "/usr/bin/nautilus"[/COLOR]* did not work as many of the other commands will.

EDITED with further explanations:
If you specify a complete path, you can run the command:
```
bash -c "sleep *XX*; nautilus /path.you.want.opened"
``` 
Example: bash -c "sleep 15; nautilus /home"

If you do not specify a path, the browser may not open. *Nautilus* is not merely a file browser - it is a file *manager* which accomplishes many tasks. Including a path in the command line ensures the file browser is opened.

And as was discovered, placing that in a sessions command will automatically create the proper format in a new .desktop file in ~/.config/autostart

I used this in the .desktop file starting it with "Exec=" but it should work as plamen_todoroff mentioned as well.


Best wishes for your orderly lives  ;-)

---

### Post by RavanH on 2009-04-03
> **drs305 said:**
> ...Please permit me to add one more thing to your thread...
By all means! ;)

By the way, are you planning on putting this discovery of yours in a quick guide?

---

### Post by plamen_todoroff on 2009-04-04
It's AWN. I've never tried cairo-dock, seems to complicated :)

---

### Post by drs305 on 2009-04-04
> **RavanH said:**
> By all means! ;)

By the way, are you planning on putting this discovery of yours in a quick guide?

Yes I will unless it is already posted or you or plamen_todoroff  would like to do it.

---

### Post by drs305 on 2009-04-09
RavanH and plamen_todoroff,

I made a guide and it's posted on the Tutorials forum.
[_HOWTO: SET SESSIONS STARTUP ORDER_]("http://ubuntuforums.org/showthread.php?t=1119945&highlight=sessions")

1300 words to describe one simple command line input. I've got to learn to be more concise!

---

