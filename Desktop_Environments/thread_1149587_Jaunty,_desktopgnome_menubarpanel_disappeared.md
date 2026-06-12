---
title: "Jaunty, desktop/gnome menubar/panel disappeared"
date: 2009-05-05
forum: Desktop Environments
---

### Post by rannday on 2009-05-05
After I started up my laptop running Juanty desktop edition, the menu bar which I had customized at the top of my screen disappeared. 

Apps still seem to be working through, was able to open up firefox via the terminal. 

I don't understand what happened though. Ne other cases of this? Any way to add a menubar w/ a command?

-rann
[email]rannday@bellsouth.net[/email]

---

### Post by fela on 2009-05-05
That's funny, the only explanation I can think of is that you accidentally deleted it (though that's quite unlikely!). But you can right click on the bottom panel and choose 'new panel' to create a new one.

---

### Post by rannday on 2009-05-05
I had no bottom panel, deleted it, leaving only the top. So that wasn't an option.

But I did some research, seems there are a few other cases of this. So tried running some terminal commands they recommend for the fix. But they weren't working.

I began thinking, maybe gnome-panel is no longer installed. . which was the case. reinstalled

```
sudo apt-get install gnome-panel
```

then ran gnome-panel

```
gnome-panel
```

and they came back, but I received this error message, asking me whether or not to delete it. still haven't decided.

> The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet". 

I didn't delete the panel. But last night, right before I went to bed, I partitioned by pen-drive and ran the USB Startup Disk Creator and installed Jaunty desktop edition on it. Don't know if thats pertinent, but its all I did b4 shutdown b4 I restarted it about an hour ago. 

Also, know its not the right forum for this, but my drive w/ jaunty on it doesn't seem to be "persistent"? It isn't saving my user data, such as customizing it and apps I install on it b4 shutdown.

---

### Post by rannday on 2009-05-05
So I decided not to delete that, but that caused gnome-panel to stop loading, so forced quit, and gnome-panel stopped working.

started again, deleted that "thing" this time, now received this error, and also gnome-panel stopped working.


> Unable to open desktop file evolution-mail.desktop for panel launcher

So I'm going to force-quit again, reinstalled evolution mail, and c if this fixes anything.

---

### Post by rannday on 2009-05-05
installed evolution mail and then ran gnome-panel again, here was the output

> /$ gnome-panel
** (gnome-panel:5567): DEBUG: Initialized Panel Applet Signaler.
** (gnome-panel:5567): DEBUG: Adding applet 0.
** (gnome-panel:5567): DEBUG: Adding applet 1.
** (gnome-panel:5567): DEBUG: Adding applet 2.
** (gnome-panel:5567): DEBUG: Adding applet 3.
** (gnome-panel:5567): DEBUG: Adding applet 4.
** (gnome-panel:5567): DEBUG: Adding applet 5.
** (gnome-panel:5567): DEBUG: Adding applet 6.
** (gnome-panel:5567): DEBUG: Adding applet 7.
** (gnome-panel:5567): DEBUG: Adding applet 8.
** (gnome-panel:5567): DEBUG: Adding applet 9.
** (gnome-panel:5567): DEBUG: Adding applet 10.
** (gnome-panel:5567): DEBUG: Adding applet 11.

(gnome-panel:5567): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:5567): DEBUG: Adding applet 12.

no clue what to do now. any help would be appreciated. 

-rann
[email]rannday@bellsouth.net[/email]

---

### Post by rannday on 2009-05-05
whatever the problem was, I've decided to just do a clean install, again.

but check out this script I wrote (jaunty.sh) for a Jaunty update after new install. 

Kinda new to Unix/Linux/Unbuntu, but I am lovin' it. Friend taught me how to write simple scripts, such as (jaunty.sh), enjoy!

---

### Post by fela on 2009-05-10
I shouldn't have taken that break from the computer!!! You didn't need to reinstall. I reckon you could have entered in the terminal:

```
sudo apt-get install ubuntu-desktop
```

That's a package that will automatically install all the packages that come with the Ubuntu desktop when installed.

I don't know what happened to your setup but it sounded like lots of packages had been removed.

Anyway, lesson learned hopefully! I would only reinstall if your system totally breaks (at the system level). And even then it is a last resort. Then again maybe it's cause I love fixing things!

Best of luck with the new 'Buntu installation.

---

### Post by wordsmyth on 2009-05-19
BOTH my desktop panels disappeared on Jaunty - TWICE! BOTH times I've had to re-install, for with no way to access the Terminal via Applications/Accessories on the missing top panel, I've had no other choice. But if it happens again, I'm going back to Windows. What IS going on here,  fellows?

---

### Post by dipaish on 2009-05-19
I too had the same problem. I solved it once by running in the safe mode. The second time i installed the ubuntu-desktop (sudo apt-get install ubuntu-desktop). Trust me whenever a new version of ubuntu comes there are always a lots of problem atleast for the first 3 months and then things start to get fine slowly. I too had many problems with ubuntu 8.10 . I had to install jaunty twice by now. For the first time i upgraded which made my pc very slow, my open office was hanging again and again, sound problem , if log out then it would hang,,,i would get a blank screen etc. I decided to re-install . Hope this is the final time and i dont have to reinstall again until the other version is launched (6 more months left:p)

---

### Post by bugritall on 2009-06-27
As part of my migration from XP, I disposed of Evolution Mail yesterday and installed Mozilla Thunderbird. I dragged in Thunderbird's Win-XP store and all seemed well until I booted my system this morning, only to discover that both my desktop panels have disappeared.

I'll follow your advice and report back.

EDIT:
I managed to get to the system prompt (after a bit of dib0700 grief caused by my DVB-TV tuner) and I re-installed ubuntu-desktop. All is now well again, except that Evolution is back. However, since Thunderbird still appears to be my default mail client, I suppose I can live with having Evolution lurking around in the background.

I suppose it's a bit like having Internet Explorer lurking around when I'm using Firefox in Windoze.

EDIT 2:
I was wrong about Thunderbird being my default mail client because Evolution is. This is looking increasingly like a Windoze Update farrago. 

Anyway, chances are that the only time it might matter is when I respond to a HTML mailto but I still want to make Thunderbird my default mail client. How do I do that, please?

---

### Post by coolcat on 2009-06-27
@bugritall
To make Thunderbird your default email client go to System - Preferences - Preferred Applications
In the Internet tab you will see your default browser and email client.
Select Thunderbird from the drop down box. If it's not in the drop box then choose Custom and add this in the Command Box;
/usr/lib/thunderbird/thunderbird "%s"

I have found out in the past that attempting to uninstall Evolution will create serious problems with Gnome. Best to leave it alone and use the Preferred Apps panel to chose your default email client.

I have also recently read that Brasero may be the cause of disappearing desktop icons.
It was suggested to install nautilus-cd-burner which will uninstall 2 of the Brasero packages. That means that if you use Brasero it won't work anymore but the Desktop icons disappearing trick will be fixed.

I use k3b so getting rid of Brasero wasn't a hardship for me.

CCat

Check out Tazbuntu;
[http://tazbuntu.blogspot.com/](http://tazbuntu.blogspot.com/)

---

### Post by jfvb1225 on 2009-06-27
So far with Jaunty I've lost my panels on more than one machine and the only thing I've found so far that works (tried several of the common suggestions) is to abandon my current user on the machine and create a new one. The loss of panels seems to occur most often after installing updates or additional software.

---

### Post by bugritall on 2009-06-28
Many thanks, [B]CCat.

[/B]I have used Brasero a couple of times, so far without mishap, but I have had a look at the k3b site and I think I'll follow your lead. I like k3b's layout with its ever-ready file browser.

---

### Post by TSWMIN85 on 2009-07-06
I just realized the problem is that when you uninstall EVOLUTION or some other programs (i.e. ABIWORD) it also uninstalls GNOME and GNOME DESKTOP ENVIRONMENT. Which sucks, because I don't want or need these programs on my computer. Anyone know how to uninstall these programs without GNOME being effected?

---

### Post by sergius248 on 2009-07-12
My gnome-panels disappeared too after upgrading to jaunty on my set-up (AMD-64).
I could not find the causes. Using Alt-F2 I however managed to launch "RUN" with the command line "gnome-panel --replace". My gnomepanels returned and I installed using Ubuntu Tweak -> Autostarts a new command line "gnome-panel --replace"(I guess the same would be possible by manually editing "/home/*user*/.config/autostart")that restart the Gnome-Panels everytime the system start.
As a stopgap solution it seems to be working.

Serge

---

### Post by jfvb1225 on 2009-07-14
> **sergius248 said:**
> My gnome-panels disappeared too after upgrading to jaunty on my set-up (AMD-64).
I could not find the causes. Using Alt-F2 I however managed to launch "RUN" with the command line "gnome-panel --replace". My gnomepanels returned and I installed using Ubuntu Tweak -> Autostarts a new command line "gnome-panel --replace"(I guess the same would be possible by manually editing "/home/*user*/.config/autostart")that restart the Gnome-Panels everytime the system start.
As a stopgap solution it seems to be working.

Serge

Fantastic! That worked for me thanks!

---

### Post by ExcessionJaunty on 2009-07-19
I have this issue and none of the fixes in either of these threads works. I have tried all of them but a complete reinstall of gnome so far.

Desktop just looks like this:
[[IMG]http://img194.imageshack.us/img194/2696/screenshotgsv.th.png[/IMG]]("http://img194.imageshack.us/i/screenshotgsv.png/")

I am brand new to linux -help!

---

### Post by alexrb on 2009-08-09
I'm hitting Alt-F3 two or three times to make panels appear.
Annoying bug. Any solutions?

---

### Post by dreamsR4living on 2010-03-27
My Gnome-Panel disappeared for many times in different Ubuntu versions. To hit ALT-F2 and type gnome-panel --replace fixes the problem, but many times I wasn't even able to bring up ALT-F2.

The remedy is to right click the desktop and create a new application launcher. Name it Terminal and for command fill in gnome-terminal.

Open the new terminal launcher and type gnome-panel --replace.

If the gnome panel keeps disappearing you can also go to System > Preferences > Sessions and create a new session named Gnome Panel. The command should be gnome-panel. This makes gnome-panel start automatically after logging in.

Hope this helps.

---

### Post by 8086 on 2010-04-15
For me the top-panel disappeared after enabling auto-hide. It worked at first, but then disappeared on subsequent logins. It was showing as a running process, and by going into gconf-editor and finding the preferences for it, I disabled auto-hide and voila it popped up again!

---

### Post by chris.willis on 2010-04-16
Happened to me. I had a great system and the next time I logged in, no panel! Arrg! After reading forums and trying everything with complex commands and uninstalling stuff, I had an idea which worked ... and it's so simple!!

In Preferences - Startup Applications, Click Add. A box pops up. Enter the following:

Name: Panel
Command: gnome-panel

Click Save, then restart the system.

I've been using Ubuntu based distros for two years and I think this is the first time I've solved my own problem lol. Hope it helps somebody out there.

---

