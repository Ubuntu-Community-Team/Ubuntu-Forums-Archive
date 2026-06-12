---
title: "systray hw? classic"
date: 2012-05-20
forum: Desktop Environments
---

### Post by ottosykora on 2012-05-20
I have some apps, they really need to place an icon 'in the systray' when the run.

I have 4 installs, all similar, 12.04, classic(noeffects).
On one install this works somehow automatically, on other I have no clue how to set it up so it works.

Any help?

---

### Post by kansasnoob on 2012-05-20
Please have a look at this:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

See if any of the info there is helpful at all and then post back with more details.

---

### Post by ottosykora on 2012-05-20
hmm, yes this howto I have printed and did all the mods to the but this particular thing I do not see in it.

I have 4 installs, 3x 32bit and 1x x64

On one some programs can place an icon in the 'tray' and on the others no way.

So how to allow programs to place an icon?

I mean something like skype can do, place an icon as long as running.

I have for example one encrypted cloud service, called wuala (wuala.com)
And this needs to behave similar way as skype does. It has some main windows, but when I close this one, I need the icon as this is now the only acces to the running program and here it can be closed completely if needed.

On one computer, set up according your hwto, the icon does appear on the panel, infact it does shift the applet indicator little bit to left and sits there now.
Skype puts its icon on the left side of the applet indicator.


so any way to do it?

---

### Post by ottosykora on 2012-05-21
So here I have two examples.
Both are 12.04 installs, both almost identical.

In one case, when I use a program like wuala or even thunderbird, an icon is placed to the try.

Well the thunderbird icon is not the most important , as this is also in other cases hiding inside the envelope of the applet.

But with some other programs like this clod service or sky pe or similar, it is essential that one has an access to the icon, other wise there is only very complex way to stop the application via numerous kill etc.
And once it runs, it is often not possible to open it again, as it is still running in the background but has no other control to open it full again.

Now I remember, that I was doing some modification one time, advise given here in forum. I was using the gconf.

But this was longer time ago and I am not able find the thread any more.

I did read also about some settings for unity, entering some white-list for apps allowed to place icon in the try. But can not find any info how this can be done on classic.

As you can see from the picts, one install allows it, other not. I have no clue where is the difference, as both are upgrades done this weekend.

See the red W on one of the picts, this is the wuala cloud service icon. In this case also TB does not only 'hide' inside the envelope, but displays own icon as well.

Any idea how to allow the try icons?

---

### Post by kansasnoob on 2012-05-21
I'm guessing those apps are displayed within one of the indicator applets, so each should have it's own configuration process. Depending on the apps name give a thorough search through the entire menu. Sometimes the apps preferences show up in different places depending on the individual app.

---

### Post by ottosykora on 2012-05-22
well can be, but is not the case here.

I have also portable windows version of thunderbird, with the extension minimize to tray. Also this one when run in wine will place its icon visible in the top bar on one of my 4 installs.
I tried to search with gconf and dconf, but can not find any difference so far.

Skype will show its icon on all 4 installs for example.

Wuala is an java app in fact, it can be also downloaded just temporary instead of webservice for the cloud service. In such case also this one, not configured at all, will place its red icon to the tray.
In case of wuala it is absolutely essential as there is otherwise no control at all.

Next, there is also an icon which belongs to HP printing service. This icon attempts to appear in the tray during boot up, stays there for few seconds, then it is kicked out by the applet.
I have the hp service exactly the same running on all other installs, the icon does never show up there.

Under unity, there is some tweak with a white list of apps.

But this function must be somewhere in the system, as the behavior is clearly different on one install and probably I did some tweak there long time ago, when still 10.10 or 11.04 was on it. (I upgraded all installs from 11.04 in fact)

BTW: the icons are NOT displayed within one of the applets. When tehy are here, I can still move the applet or even remove it completely and the icons will still be here. It is rather that the in case of TB and Wuala, the applet is moved to left to make place for the icon and when the program is closed the applet moves itself back to the end.

---

### Post by ottosykora on 2012-05-22
in this pic, I have moved the applet somehow to the middle and you can see it will show some of the included icons. The 'crash' warner is n the applet, the HP service placed itselve between the caffeine and wx bug.

The thunderbird icon on the right is minimized portable thunderbird, which is a windows app running in wine. It does go to tray on this machine, but it does not on others.

The wuala (red W) is in this case the 'webservice' of wuala, namely their java applet running life, no instal of that, no config possible, it is selfcontained program using only javato run.

---

### Post by ottosykora on 2012-05-22
The only thing different between my installs is, that the one where the icons are shown is the oldest one, I assume it was upgraded the way back from 9.04 or so.

The other started with 10.04 or 10.10

---

### Post by ottosykora on 2012-05-22
OK I have it!

See the picture, the indicator applet, complete or not, will apparently display only specific programs or tasks which it was made for or the programs are made to be compatible with it.

If we need any programs giving us systray icon, thewe have to install the indicator field (sorry my computer talks german, do not know how is it called in english version) -> see pic.

One can first remove the applet, then put the indicator field onto the panel, then the icons will be on complete right end and the applett will shift and make space depending on how many icons want to be displayed.
If you place the indicator field after the applet was placed then it will look like on my pic.


@Kansasnoob !!!!

Please take it into your hwto script, name it how it is really named in english and perhaps include CLI command to do it from terminal. It is valuable, I have seen number of unanswered threads on that subject, so it is not only me who needs it. 
Have admit, it was driving me nuts, but now I am kind of relaxed.

Thanks



--------
not sure, but can t be the thing is called com.canonical.notify-osd ?

---

