---
title: "Volume Icon Gone from Top Panel in Ubuntu 10.4"
date: 2010-03-22
forum: Desktop Environments
---

### Post by Xorlathor on 2010-03-22
I am using the fully updated version of Ubuntu 10.4. The volume icon is missing from the top panel and adding the "notification area" does not do anything - I can double-click the icon, or drag it over, and nothing appears in the panel. Adding the "Indicator Applet" also has the same result.

I do not know what applet to add, nor do I know why the volume icon is missing. 

The power icon, the network icon, the mail icon, and the rest of the applets are all there - only the volume icon is missing.

Also, when I press "fn + pg up or pg dn," it would usually change the volume and display a notification showing that the volume changed.

This does not happen anymore: no notification, no sound change.

I can still hear audio, but can not change the level. If you could help me with this, that'd be awesome!

---

### Post by Xorlathor on 2010-03-22
Anybody have a solution to this? And I'm a newbie here - is there anyway to go to a list of topics you've started (Besides subscribing it)? Because it's quite annoying to have to sift through a couple pages looking for a topic you've started.

---

### Post by stinkeye on 2010-03-22
It's in the indicator applet for me, on my lucid install.
You may have to restart for the volume to appear.
or
gnome-volume-control-applet will bring up the old karmic one in the notification area.

> **Xorlathor said:**
> And I'm a newbie here - is there anyway to go to a list of topics you've started (Besides subscribing it)? Because it's quite annoying to have to sift through a couple pages looking for a topic you've started.
Click on your user name at the top right and then click on statistics
and there are 2 links 
**Find all posts by Xorlathor**
**Find all threads started by Xorlathor**

---

### Post by Xorlathor on 2010-03-23
The strange thing is that the indicator applet is there - I see the battery and network icons; nothing weird with them. I tried adding the indicator applet again and it simply added just the battery and network icons (which I already have...) 

I don't know how to add the "gnome-volume-control-applet." It's not in the "Add to Panel" menu and I can't install it via "sudo apt-get install."

Sorry if it's something uber-obvious, I think I already mentioned I'm new to Ubuntu. But at least I learn quick and use right spelling and grammar. (And am not overtly stupid and ignorant, I hope...)

---

### Post by stinkeye on 2010-03-23
Your going to get a lot of bugs using lucid because it's still in alpha.

copy and paste 
```
gnome-volume-control-applet
```
in the terminal
and if it works add it to system > preferences > Startup Applications

---

### Post by Xorlathor on 2010-03-23
> **stinkeye said:**
> Your going to get a lot of bugs using lucid because it's still in alpha.

copy and paste 
```
gnome-volume-control-applet
```
in the terminal
and if it works add it to system > preferences > Startup Applications

Followed your instructions and it worked like a charm - thanks so much!

---

### Post by stinkeye on 2010-03-23
> **Xorlathor said:**
> Followed your instructions and it worked like a charm - thanks so much!
No problem.

---

### Post by edwardtilbury on 2010-04-02
Exact same problem here!

Will try to solution


x64 10.04 Beta

---

### Post by technoshaun on 2010-04-04
Thank You also I to lost the volume control. Your solution definitely worked. Can't figure out why it disappeared in first place though.

---

### Post by WxDan on 2010-04-13
> **edwardtilbury said:**
> Exact same problem here!

Will try to solution


x64 10.04 Beta

Same system, same issue. Fix also worked here. 

If you enter the below text in the terminal, it will start the applet until you reboot next time.

```
gnome-volume-control-applet &
```

---

### Post by davmax on 2010-04-13
Have the same problem in Ubuntu 9.1 but this fix does not work.

gnome-volume-control-applet is in startup applications but applet does not appear in upper panel.

New to Ubuntu and totally at a loss.

Also using the "Add to Panel" it is not listed and if I type in anything into " Find an item...." nothing happens.:(

---

### Post by stinkeye on 2010-04-14
Do you have the notification area applet in the panel?
If the volume control is in startups ,that's where it should appear.

---

### Post by booyakah on 2010-04-17
It seems that many people that use 10.4 has had issues with this.

I had basically the same problem before beta 2, but I could not get the volume indicator to show up. Like some before me have noted I also could not see the network, battery icon etc..

After I upgraded to beta 2 the problem was solved though.

---

### Post by Sepero on 2010-04-20
gnome-volume-control-applet &

I don't want or need the little "mail" icon, so I had unknowingly deleted both it and the volume. I can use the above and the volume is added to the "Notification Area" applet.

Add it to system > preferences > Startup Applications

Works for me on Lucid thanks.

---

### Post by infamous-online on 2010-04-20
I hope this isn't an issue doing the final release.

---

### Post by obieito on 2010-04-23
I'd say it is... I also upgraded yesterday, all I did was remove the chat-ubuntu-one-etc applet (why did they make that default? =/ I hate it!) and today I noticed I had no volume control...

---

### Post by obieito on 2010-04-23
Now I've found the correct solution here [http://ubuntuforums.org/showthread.php?t=1357005](http://ubuntuforums.org/showthread.php?t=1357005)

You have to add the "Indicator Applet" and the volume icon will come back.

---

### Post by soupowl on 2010-04-29
Both these applets seem to be linked, so you can't have the volume control without the envelope! Rats! I hate clutter - if I wanted clutter I'd use Microsoft.......

---

### Post by Mad-Halfling on 2010-04-29
It doesn't (seem to) display properly if you have the bar on the left or right side of the screen either - all you can see is the bluetooth icon - surely that must have come out in testing?

---

### Post by Xorlathor on 2010-04-29
I'm not sure what the big deal is - I've long since reinstalled Lucid (it's officially out today, go grab the torrent) and I've never had a problem since. 'Tis not that complicated, peoples.

---

### Post by polki@mac.com on 2010-05-01
Removing indicator-messages rid me of the horrible envelope. I don't know if I lost any functionality. I just like it this way. YMMV. I'm more happy without that not-working-with-thunderbird-thingy.

---

### Post by TheCheeze on 2010-05-01
> **polki@mac.com said:**
> Removing indicator-messages rid me of the horrible envelope. I don't know if I lost any functionality. I just like it this way. YMMV. I'm more happy without that not-working-with-thunderbird-thingy.
Thank you! Worked great and looks so much more streamlined than with the volume indicator applet.

---

### Post by wgarider on 2010-05-02
FWIW - I upgraded from 9.10 to 10.4 yesterday. My sound/volume icon disappeared in the process and none of the solutions I read here worked ***_except_*** to add it to the Startup Applications........
Thanks to everyone here for offering up a resolution!

---

### Post by zzirf on 2010-05-10
> **obieito said:**
> Now I've found the correct solution here [http://ubuntuforums.org/showthread.php?t=1357005](http://ubuntuforums.org/showthread.php?t=1357005)

You have to add the "Indicator Applet" and the volume icon will come back.

Thanks, it did come back (with the envelope).

---

### Post by vetetix on 2010-05-23
Just some info for those who might be interested : the sound control icon that fit in the indicator-applet in ubuntu lucid is provided by the indicator-sound package.

---

### Post by juanclunac on 2010-07-28
> **zzirf said:**
> Thanks, it did come back (with the envelope).

in fact, i like the fact i have sound control again, but i dont like the icon, i mean is not like the other ones, there is a way to put the theme icon on the sound control?

---

### Post by isbiyanto on 2010-08-08
> **stinkeye said:**
> Your going to get a lot of bugs using lucid because it's still in alpha.

copy and paste 
```
gnome-volume-control-applet
```in the terminal
and if it works add it to system > preferences > Startup Applications

thanks for all. i got audio applet again in my lucid

---

### Post by dineshrathod2216 on 2010-11-05
> **stinkeye said:**
> It's in the indicator applet for me, on my lucid install.
You may have to restart for the volume to appear.
or
gnome-volume-control-applet will bring up the old karmic one in the notification area.


Click on your user name at the top right and then click on statistics
and there are 2 links 
**Find all posts by Xorlathor**
**Find all threads started by Xorlathor**
gnome-volume-control-applet fixed my problem. Many thanks. :P

---

### Post by unplas7icated on 2010-11-20
> **vetetix said:**
> Just some info for those who might be interested : the sound control icon that fit in the indicator-applet in ubuntu lucid is provided by the indicator-sound package.

Thanks, that did it.

---

### Post by JohnnyVW on 2010-11-29
> **polki@mac.com said:**
> Removing indicator-messages rid me of the horrible envelope. I don't know if I lost any functionality. I just like it this way. YMMV. I'm more happy without that not-working-with-thunderbird-thingy.

Thank you!

I upgraded from 9.10 to 10.04 to 10.10 this weekend and the missing volume control/volume control AND message thing was bugging me.  This fixed it!

---

### Post by mx32 on 2011-01-30
> **stinkeye said:**
> Your going to get a lot of bugs using lucid because it's still in alpha.

copy and paste 
```
gnome-volume-control-applet
```
in the terminal
and if it works add it to system > preferences > Startup Applications


Hi, 
I had missing both, the volume and mail icons in ubuntu 10.04. I used the instructions above and worked great, although the volume icon looked slightly different and the mail icon was still missing. Finally I found the way to restore the original icons, this is how:

1. Right-click on the panel where you'd like the volume controller to appear and select "Add to panel"
2. Choose "Indicator Applet" from the list and click on "Add" and you're done. The volume and mail controls should be back.. 

Let me know if this worked for you.
):P

---

### Post by Singer on 2011-03-07
> **mx32 said:**
> Hi, 
I had missing both, the volume and mail icons in ubuntu 10.04. I used the instructions above and worked great, although the volume icon looked slightly different and the mail icon was still missing. Finally I found the way to restore the original icons, this is how:

1. Right-click on the panel where you'd like the volume controller to appear and select "Add to panel"
2. Choose "Indicator Applet" from the list and click on "Add" and you're done. The volume and mail controls should be back.. 

Let me know if this worked for you.
):P

worked like a magic 
thanks for the tip dear friend....

---

### Post by ingarion on 2011-08-25
When I type gnome-volume-control-applet into the terminal, this is what I get:

```
gnome-volume-control-applet: error while loading shared libraries: libpulse.so.0: cannot open shared object file: Permission denied
```Anyone know what's wrong? =\

---

### Post by lazyval on 2011-10-12
Thanks! Worked like a charm

---

