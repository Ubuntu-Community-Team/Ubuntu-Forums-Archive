---
title: "Login In Sound"
date: 2012-01-30
forum: Desktop Environments
---

### Post by makitso on 2012-01-30
I know it's not keeping with the minimalistic nature of Lubuntu.  But, if I wanted to have the Ubuntu login sound, how might I go about this?  

I have 12.04 running in VB, installed canberra and have a startup file, along with the ubuntu sound files in /usr/share/sound.

This command will play the login sound but with a lot of static.  ogg123 -o alas:dev:hw:0   ./desktop-login.ogg

---

### Post by Rodney9 on 2012-01-30
It's curious how some of us are happy Lubuntu does not have a start-up sound and others wish it did.

Of course this is the beauty of Linux, you can make it whatever you want.

I will have a go at replicating your attempt and will report in a couple of hours.



For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by makitso on 2012-01-30
I have no problem with Lubuntu being lean and mean.  However, there should be an easy way to do things -- e.g. install this app, configure this script etc.  

As a test, 

xubuntu 12.04, using the file manager, clicked on a desktop.login.ogg file and Parole opened up and played it fine. 
 
lubuntu12.04  using the file manager, clicked on a desktop.login.ogg file and gnome-mplayer opened up and it stopped.  Installed Parole and it now plays the startup sound.  

But, need a command line to do a startup file.

---

### Post by Rodney9 on 2012-01-31
I have tried oggplay , aplay , play, scripts

I've put them in .config/autostart 
/home/rodney/.config/openbox/autostart.sh
/etc/xdg/lxsession/lxde/autostart

I failed to get any sound at start-up

Rodney

---

### Post by Rex Bouwense on 2012-01-31
Hey, I screwed around for a week to ten days when I first installed Ubuntu 11.04 trying lots of stuff until I discovered quite by accident that there was no sound in the Lubuntu start up.  Now I like it.

---

### Post by makitso on 2012-01-31
Yes, yes, I know, no one likes startup sound in lubuntu.  

The point is that is IF someone wants it how can one do it?  Right now, there is no way to make an .ogg file play via a command line utility.

---

### Post by amjjawad on 2012-02-01
[https://www.facebook.com/groups/lubuntu.official/](https://www.facebook.com/groups/lubuntu.official/)

---

### Post by Rodney9 on 2012-02-01
> **amjjawad said:**
> [https://www.facebook.com/groups/lubuntu.official/](https://www.facebook.com/groups/lubuntu.official/)

```
You must log in to see this page.
Email:
Password:

Keep me logged in
or Sign up for Facebook
```

I do not want Facebook to know me.

What does [https://www.facebook.com/groups/lubuntu.official](https://www.facebook.com/groups/lubuntu.official) say ?

Rodney

---

### Post by amjjawad on 2012-02-01
> **Rodney9 said:**
> ```
You must log in to see this page.
Email:
Password:

Keep me logged in
or Sign up for Facebook
```I do not want Facebook to know me.

What does [https://www.facebook.com/groups/lubuntu.official](https://www.facebook.com/groups/lubuntu.official) say ?

Rodney

Well, you can create a fake account, I mean fake information. Anyway, it was a conversation between our Artwork Team Leader and one of the users. I need to copy-paste the whole thing or find a simple HOWTO for that :) 

Our weekly meeting will start soon and I must eat and take my pills so I can't do it right now, maybe later :)

Thanks!

---

### Post by makitso on 2012-02-02
[LEFT][COLOR=#333333][FONT=lucida grande][B][B][Facebook comments were:]("http://www.facebook.com/profile.php?id=100000028815932")

[Jan Marou&#353;ek]("http://www.facebook.com/profile.php?id=100000028815932")[/B]
[/B]

**can any1 tells me, where can I set-up the "welcome sound" when lubuntu started? tnx**

[COLOR=#999999][COLOR=#999999][January 29 at 10:47am]("https://www.facebook.com/groups/lubuntu.official/291353954254765/")[/COLOR][/COLOR]
[LIST]
[*]
[LIST]
[*][[IMG]https://fbcdn-profile-a.akamaihd.net/hprofile-ak-snc4/50010_100000028815932_1777048714_q.jpg[/IMG]]("http://www.facebook.com/profile.php?id=100000028815932")Mark as Spam

[Jan Marou&#353;ek]("http://www.facebook.com/profile.php?id=100000028815932") did, but there is not some sound choice :-))[COLOR=gray]January 29 at 4:44pm[/COLOR]
[*][[IMG]https://fbcdn-profile-a.akamaihd.net/hprofile-ak-snc4/186968_1407363799_2987344_q.jpg[/IMG]]("http://www.facebook.com/rafaellagunamendez")[&#31070;&#30290;&#30977;&#28246;]("http://www.facebook.com/rafaellagunamendez") Ha, ha, now's your turn. Just put a mp3 or ogg you like. I highly recommend something like SPARTAAA!!![COLOR=gray]Monday at 2:55pm[/COLOR]
[/LIST]
 
[/LIST]




Unfortunately, this answer does not work since ogg files do not play natively on lubuntu.  So,  amjjawad the question stands.  How would one configure lubunto to play a .ogg at startup?
Simple things like this should be easy to do on linux.  But, no one appears to take the question seriously.

[/FONT][/COLOR][/LEFT]

---

### Post by amjjawad on 2012-02-06
> **makitso said:**
> Simple things like this should be easy to do on linux.  But, no one appears to take the question seriously.
[LEFT][COLOR=#333333][FONT=lucida grande] 
[/FONT][/COLOR][/LEFT]


Before few weeks, my tasks became a lot more than before with Lubuntu. My involvements now have exceeded being just a forum guy, I have lots of stuff to do. You need to understand that Lubuntu is a small team that is doing their best to make this OS as good as possible. We are short in members, supported, contributors, etc. That's why everyone one of us is jumping here and there to help.

If your question on Ubuntu Forum isn't answered yet, there are many other channels you can try hopefully you'll get the answer. 
I wish I could help with the answer but I have no idea how to.

[https://wiki.ubuntu.com/Lubuntu/ContactUs](https://wiki.ubuntu.com/Lubuntu/ContactUs)
Same link on my signature. You can pop up on IRC OR subscribe to the mailing list and ask over there OR Search on Google OR wait until someone answer your question over here.

I'm really sorry for the late reply but I'll never ignore any question over here no matter what and I always take any question over here seriously, sometimes VERY serious :)
I've been so sick for the last 3 weeks, that is why my activities became less over here. My apology once more and I'll do my best to get the answer for you unless you want to keep digging yourself ;)

---

### Post by makitso on 2012-03-22
For those that are interested, I have login sound working on the latest lubuntu 12.04. 
 
For testing, I copied the ubuntu login .ogg file to ~/me/.config/autostart
Then I created a desktop file with the following:
[Desktop Entry]
Type=Application
Name=GNOME Login Sound
Comment=Plays a sound whenever you log in
Exec=/usr/bin/mplayer /home/me/.config/autostart/desktop-login.ogg

---

### Post by Rex Bouwense on 2012-03-22
Great (for those who want sound on log in).  I have bookmarked this to spread the word.  Out of curiosity, did you test it on any other version (11.10 0r 11.04)?  Probably doesn't make any difference because 12.04 will be released next month anyway.

---

### Post by amjjawad on 2012-03-22
> **makitso said:**
> For those that are interested, I have login sound working on the latest lubuntu 12.04. 
 
For testing, I copied the ubuntu login .ogg file to ~/me/.config/autostart
Then I created a desktop file with the following:
[Desktop Entry]
Type=Application
Name=GNOME Login Sound
Comment=Plays a sound whenever you log in
Exec=/usr/bin/mplayer /home/me/.config/autostart/desktop-login.ogg

That is great to know :)
I must test that myself too on my two test machines ;)

I just want to make sure how smooth that will be and how easy to do just for my information. I will not add that to the Wiki :P

---

### Post by amjjawad on 2012-03-22
Hello there :)

> **Rex Bouwense said:**
> Great (for those who want sound on log in). 
+1

> Out of curiosity, did you test it on any other version (11.10 0r 11.04)?  

Can someone confirm that?

> Probably doesn't make any difference because 12.04 will be released next month anyway.

Not everyone go for the newest version. Some believe in: if it is not broken, don't fix it :)

---

### Post by Guilden_NL on 2012-04-09
I like this because I run Lubuntu on some very fast/hot machines, and don't like to cripple everything just to be very lightweight.

Am running on a 2004 Toshiba Satellite with 1GB of RAM all the way to a 24 core desktop with 96GB RAM with a few duo/quad core laptops in the middle.

The start up sound helps me know where it is at in the start up process when I step away.  Of course, nice to disable it for the old HW too.

Thanks makitso!  (I too stay far away from Facebook, you wouldn't believe what those clowns capture and keep, even if you use a fake account.)  BTW, I made a custom AC/DC ogg, With the opening riff and then ending with "You've been Thunderstruck!"

---

### Post by Herpythebrony on 2012-04-09
I am now tempted to make the login sound play the south park theme.

---

### Post by amjjawad on 2012-04-11
> **Guilden_NL said:**
> Am running on a 2004 Toshiba Satellite with 1GB of RAM all the way to a **24 core desktop with 96GB RAM with a few duo/quad core laptops in the middle.**
What is that?

> (I too stay far away from Facebook, you wouldn't believe what those clowns capture and keep, even if you use a fake account.)

*OFF-Topic*
Not only facebook is able to store your data, keystroke, etc but many other sites do the same, google is one example ;)

---

### Post by amjjawad on 2012-04-11
> **makitso said:**
> For those that are interested, I have login sound working on the latest lubuntu 12.04. 
 
For testing, I copied the ubuntu login .ogg file to ~/me/.config/autostart
Then I created a desktop file with the following:
[Desktop Entry]
Type=Application
Name=GNOME Login Sound
Comment=Plays a sound whenever you log in
Exec=/usr/bin/mplayer /home/me/.config/autostart/desktop-login.ogg

Still don't have time to test that :(

Not sure how many users have tested it already and can confirm it works for them and never break anything else :)

---

### Post by Ajay Ramaseshan on 2012-11-15
Hello I have Lubuntu 12.10 on my 1 GH RAM laptop and am trying to get the old Windows 95 sound as a login sound (its one of the few things I like about Windows). So i downloaded the flie, converted into .ogg format, and placed it in the folder /home/ajayram/.config/autostart/ . next , I created a file on Desktop called GNOME Login sound and edited its contents as follows :

```

[Desktop Entry]
Type=Application
Name=GNOME Login Sound
Comment=Plays a sound whenever you log in
Exec=/usr/bin/mplayer /home/me/.config/autostart/Microsoft Windows 95 Startup Sound.ogg

```

Then I logged out and logged in again, but nothing happened, no sound was played, Could someone figure out what could have gone wrong ?

---

### Post by vasa1 on 2013-01-01
The sound issue seems to be a victim of a conspiracy of silence :(

---

### Post by orange9k on 2013-01-07
> **makitso said:**
> I know it's not keeping with the minimalistic nature of Lubuntu.  But, if I wanted to have the Ubuntu login sound, how might I go about this?  

I have 12.04 running in VB, installed canberra and have a startup file, along with the ubuntu sound files in /usr/share/sound.

This command will play the login sound but with a lot of static.  ogg123 -o alas:dev:hw:0   ./desktop-login.ogg


Hey there, 

I've been probing for the same for a while and finally figured it out;

_What I was looking for_: **how to play a sound at login prompt?**

[U]
How I did it[/U]: 

**1) apt-getted sox**

```
sudo apt-get install sox
```**2) edited rc.local** 
```
gksu leafpad /etc/rc.local
```and then 

**3) added this line** (before "exit 0"): 
```
play -v 1 /path/to/the/sound/the-startup-sound.ogg 
```(where "-v 1" refers to a volume multiplier value of x1).

And voila!

With these three simple steps your system should now play a sound upon sucessfully booting to the login prompt (LXDM).

**4) Optional**  If you've got and old and/or slow system and want to adjust the sound to play a little later (to match the appearance of LXDM), you can thus add a line prior to the play command stating "sleep X" (for where X is a delay in seconds).

Hope this helps.:popcorn:

-O9K

---

