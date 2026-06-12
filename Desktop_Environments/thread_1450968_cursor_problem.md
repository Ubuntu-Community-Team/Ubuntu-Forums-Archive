---
title: "cursor problem"
date: 2010-04-09
forum: Desktop Environments
---

### Post by lmseddik on 2010-04-09
right now am using ubuntu 10.04 when i apply a new cursor theme the main (arrow) cursor dosnt change unlike the other(resizing, hourglass,...) i got this problem before but now i want to set up my cursor manually does any one have an idea about this, thanks

---

### Post by copkiller on 2010-05-04
same problem only on 10.04.

---

### Post by BikeMike on 2010-05-05
I upgraded my GF's laptop from Xubuntu 9.1 i-386 to the new 10.04 and after the upgrade now the cursor works but only in the middle of the screen. It won't go to the far 20% of the left or right side of the screen but will go all the way to the top or bottom. :(

Any idea how to fix this?

---

### Post by gusman21 on 2010-05-09
Same issue. 2 fresh installs.
1 32bit desktop
1 64bit desktop
Cursor seems to change in applications and not on desktop or on panels.

---

### Post by dtach on 2010-05-09
Yeah, I ditto that. I'm guessing, by the sound of it, its just some minor bug that a lot of people are having issues with; I'm sure they'll fix it with the next update or so-- or at least I *hope* they will

---

### Post by Jay Car on 2010-05-09
I have the same problem in Lucid. Did some searching about it and found this: [bug# 459647]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/459647") 

It doesn't seem to be a high priority bug fix, they say it's merely cosmetic.  But the redglass cursor and the ability to enlarge it are important to me because my eyesight isn't the best anymore.  

Anyway, there are some suggested workarounds listed on that page, so maybe they will be helpful to you. I'm just sticking to Karmic for now. I'm pretty sure the cursor bug will be fixed soon.

---

### Post by BoogeyOfTheMan on 2010-06-11
I've had this same problem since 9.04 64. I assumed it was an upgrade issue since it was working in 8.10 64 and when I installed 9.04 32 on my wifes pc, the cursors worked fine. She's dicked around with it since then so I dunno if she changed cursors or what.

---

### Post by Topazgb on 2010-10-08
I have the same problem, the last bug report for the issue was 2007 for which there was a fix.  Have created a new bug report.

[https://bugs.launchpad.net/ubuntu/+bug/657152](https://bugs.launchpad.net/ubuntu/+bug/657152)

---

### Post by pedal2themedal on 2010-12-14
I realize this is a little old, but for those of you still needing a fix, I found an easy way to go about doing it. My Ubuntu setup is custom everything basically so this was the best option for me. I took one of the options that I found on the web and modified it so it is a little easier to do, and changeable relatively easy. Here you go:

[LIST=1]
[*]type the following in the terminal:
sudo update-alternatives --config x-cursor-theme
[*]You should get a box that looks     like this:
     Selection    Path                                         Priority   Status      
     ------------------------------------------------------------         
     * 0                /usr/share/icons/DMZ-White/cursor.theme   50        auto mode      
       1                /etc/X11/cursors/core.theme               30        manual mode      
       2                /etc/X11/cursors/handhelds.theme          20        manual mode      
       3                /etc/X11/cursors/redglass.theme           20        manual mode      
       4                /etc/X11/cursors/whiteglass.theme         20        manual mode      
       5                /usr/share/icons/DMZ-Black/cursor.theme   30        manual mode      
       6                /usr/share/icons/DMZ-White/cursor.theme   50        manual mode
[*]So then open the 0 option (or whichever one has the asterisk by it) with administrator privileges
[*]Once inside the folder, in my case,  it was DMZ-White, insert the cursors folder and index.theme of the cursor you are wanting to use.
[*]Then simply restart.
[/LIST]

---

### Post by Topazgb on 2010-12-14
@[pedal2themedal]("http://ubuntuforums.org/member.php?u=1189015")

That bug was fixed over a month ago.  Of course it works when you change the cursor for your desktop.

---

### Post by pedal2themedal on 2010-12-14
> **Topazgb said:**
> @[pedal2themedal]("http://ubuntuforums.org/member.php?u=1189015")

That bug was fixed over a month ago.  Of course it works when you change the cursor for your desktop.

Actually the latest update broke mine. I tried all of the fixes and none of them worked except this one.

---

### Post by M__L on 2011-04-12
Quick fix:
Go to /home/"yourname"/.icons 
Create "default" folder. In "default" folder create empty file and fill it with:

[Icon Theme]
Inherits=your desired cursor theme name (for example: Inherits=whiteglass)

Rename empty file to "index.theme". Now select your theme in "Appearance Preferences" and restart compiz.

(of course you can also edit "index.theme" in /usr/icons/default/ - if you like entering passwords:))

---

