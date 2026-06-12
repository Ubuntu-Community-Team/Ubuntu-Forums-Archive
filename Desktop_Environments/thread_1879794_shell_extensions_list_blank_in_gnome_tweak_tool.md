---
title: "shell extensions list blank in gnome tweak tool"
date: 2011-11-12
forum: Desktop Environments
---

### Post by pjbeahan on 2011-11-12
This seems to be a common issue with several fixes, none of which have worked for me (yet!?)

Running Ubuntu 11.10, and I've found some themes I'd like to try. I've downloaded the themes, and also got the gnome tweak tool to try to change the themes. I've tried to install the two gnome shell extensions recommended to change the theme, but the list for shell extensions in the gnome tweak tool. 

I have logged out and logged back in with gnome classic, no change. Where do I go from here?

---

### Post by johnnychimpo on 2011-11-12
Same problem.  No fix.  I dont think the tweak tool works with 11.10

---

### Post by cbowman57 on 2011-11-12
Are you certain you have the correct gnome-shell-extensions-user-theme?

[http://askubuntu.com/questions/75530/how-to-install-gnome-shell-extension](http://askubuntu.com/questions/75530/how-to-install-gnome-shell-extension)

---

### Post by BoreanDream on 2011-11-12
I have got the same problem even though I installed all packages (including the user theme) correctly. When I start the Shell extension (via Applications -> Other -> Advanced Settings) I can change everything related to Desktop, Font and even SHell, but when I click on Shell Extensions there's just a blank screen, as you can see on the screenshot:

[IMG]http://i.imgur.com/0zE7w.png

---

### Post by Cha0sBG on 2011-11-12
Same problem for me

---

### Post by Frogs Hair on 2011-11-12
The shell extensions are not visible or usable from Classic Gnome or Unity . The screen shot appears to be classic Gnome not the shell . You would not have an applications and places menu in the shell with out extensions . This how the shell appears when installed from the software center . Not the same theme of course . I don't know why the  user theme extension doesn't appear . It seems the Advanced Settings / Tweak Tool is all that is needed to Change themes in unity .

---

### Post by Frogs Hair on 2011-11-12
If you are using the shell get the extensions here . [http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html](http://www.webupd8.org/2011/10/official-gnome-shell-extensions.html)

---

### Post by BoreanDream on 2011-11-13
> **Frogs Hair said:**
> The shell extensions are not visible or usable from Classic Gnome or Unity . The screen shot appears to be classic Gnome not the shell . You would not have an applications and places menu in the shell with out extensions . This how the shell appears when installed from the software center . Not the same theme of course . I don't know why the  user theme extension doesn't appear . It seems the Advanced Settings / Tweak Tool is all that is needed to Change themes in unity .

Hey, thank you, under the new GNOME it works. :)

However, often when I try to install a Shell Theme, I get the message "Invalid Theme". Why is that?

---

### Post by Frogs Hair on 2011-11-13
Make sure they are GTK 3 themes that are up to date and compatible with Gnome 3.2 . There are still some 3.0 themes still around .  I would suggest this PPA  because the themes are updated via the update manager . [http://www.webupd8.org/2011/10/4-beautiful-gnome-32-compatible-gtk.html](http://www.webupd8.org/2011/10/4-beautiful-gnome-32-compatible-gtk.html)

Most of the themes at this link  work for me.  [http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=f988642a57fbbfce4129f7d544e00b28](http://gnome-look.org/index.php?xcontentmode=167&PHPSESSID=f988642a57fbbfce4129f7d544e00b28)

---

### Post by alain.roger on 2011-11-14
> **BoreanDream said:**
> I have got the same problem even though I installed all packages (including the user theme) correctly. When I start the Shell extension (via Applications -> Other -> Advanced Settings) I can change everything related to Desktop, Font and even SHell, but when I click on Shell Extensions there's just a blank screen, as you can see on the screenshot:

[IMG]http://i.imgur.com/0zE7w.png

+1 absolutely like that... it's now 4 days that i'm looking for a solution :-(

---

### Post by cbowman57 on 2011-11-14
The solution is, the extensions aren't going to show up in a Gnome classic session.

Gnome classic = applets
Gnome shell = extensions

---

### Post by alain.roger on 2011-11-14
> **cbowman57 said:**
> The solution is, the extensions aren't going to show up in a Gnome classic session.

Gnome classic = applets
Gnome shell = extensions

I tried all fourth:
Gnone
Gnome Classic
Gnome Classic (without effect)
Ubuntu

as far as i understood Gnome shell = Gnome in the log-in windows, isn't it ?

---

### Post by cbowman57 on 2011-11-14
The image you used as an example is Gnome classic so that behavior is to be expected.

If the same thing is happening under Gnome shell then there is a problem.

In Gnome shell hit **alt+f2** type **lg** hit **enter**, that gets you into looking glass, what is showing up under the Errors & Extensions tab?

A screenshot of looking glass might be helpful, you'll have to use the delay feature in Screenshot to capture it.

---

### Post by alain.roger on 2011-11-14
> **cbowman57 said:**
> The image you used as an example is Gnome classic so that behavior is to be expected.

If the same thing is happening under Gnome shell then there is a problem.

In Gnome shell hit **alt+f2** type **lg** hit **enter**, that gets you into looking glass, what is showing up under the Errors & Extensions tab?

A screenshot of looking glass might be helpful, you'll have to use the delay feature in Screenshot to capture it.

I would be glad to go to Gnome Shell but as you wrote before, it seems that for me when i click on Gnome (at the login window) i fell under Gnome classic... (even if at the login windo) i have Gnome classic as a choice.

so in this case if i hit **alt+F2** i just get the typical "run as program" window :-( and i never get the looking glass.

i'm getting crazy with this issue...
any idea what is my problem ?
i followed tutorials how to install gnome3 but i have the feeling that something didn't install well and it didn't notice me :-(

---

### Post by cbowman57 on 2011-11-14
Ok, it's defaulting to fallback mode, probably a problem with video.

What video card are you using & what drivers did you install for it?

---

### Post by alain.roger on 2011-11-14
> **cbowman57 said:**
> Ok, it's defaulting to fallback mode, probably a problem with video.

What video card are you using & what drivers did you install for it?

so my notebook is equiped with a nVidia GeForce GTX460M 1.5 GB GDDR5.
so i installed recommended drivers and suddenly everything works..... i'm really tired to forget such trivial thing.. thx again.
lookingGlass works, so lg, r, alt+F2...well everything :-)

---

### Post by cbowman57 on 2011-11-14
Alright, did you install the gallium experimental or nvidia proprietary drivers?

---

### Post by alain.roger on 2011-11-14
as i wrote after installation of video driver everything works correctly :-) i'm so stupid.

---

### Post by cecilpierce on 2011-11-14
> **cbowman57 said:**
> Alright, did you install the gallium experimental or nvidia proprietary drivers?

Hi Chuck,
Have you tried both ? Whats the difference ?

---

### Post by cbowman57 on 2011-11-14
Ok, didn't see the edit. :)

Always the simple things that get overlooked, glad you're up & running now.

With all these new DE's on the scene at the same time it gets confusing for everybody, including those of us that are trying to help.

---

### Post by cbowman57 on 2011-11-14
> **cecilpierce said:**
> Hi Chuck,
Have you tried both ? Whats the difference ?

Hi Cecil, yeah, I've tried both, they both work but I use the proprietary drivers for the most part.

---

### Post by cecilpierce on 2011-11-14
I just put in Mint 12, I think I liked 11 better :D

Sure would like to try that new Commodore 64 gizzmo but at my speed it would take forever, about 8 gigs total, looks like fun though  :P

---

### Post by cecilpierce on 2011-11-15
Hmmm! I have the same problem with Precise, the only one that works is 'gimmie'.
I guess its to early for precise stuff to work.

---

### Post by cbowman57 on 2011-11-15
I'm not having any problems with extensions on Precise.

You using any oddball ppa's?

---

### Post by cecilpierce on 2011-11-15
ricotz, think thats messing it up ?
Seems like I had them working b4, I got CRS.

---

### Post by cecilpierce on 2011-11-15
I just added some from murphy and they dont show or work????

---

### Post by cecilpierce on 2011-11-15
Just went to my other Precise that has ricotz and kokoto ppa's and all the extensions work but tweak still shows nuttin.
dock don't work?

---

### Post by cbowman57 on 2011-11-15
> **cecilpierce said:**
> ricotz, think thats messing it up ?
Seems like I had them working b4, I got CRS.

I'd try a different user-extensions-common or whatever it's called.

---

### Post by bmbaker on 2011-11-17
there has been a problem for awhile now with gnome-tweak, check out this thread it is very helpful
[http://ubuntuforums.org/showthread.php?t=1874010&highlight=gnome-tweak-tool](http://ubuntuforums.org/showthread.php?t=1874010&highlight=gnome-tweak-tool)

also there was an update today of gnome-tweak but you will still need to change (lines 48-61)
/usr/lib/python2.7/dist-packages/gtweak/gshellwrapper.py

this was posted by [phDaemon]("http://ubuntuforums.org/member.php?u=888489") :-)
I just checked it out on Oneric and Precise and it works just fine :-)

oh and just so you know i am also using ricotz/testing ppa :-)

---

### Post by bmbaker on 2011-11-17
seems that the only thing still not wking in gnome-tweak is the usr-theme extension!
i will play some more and see if i can get it wking :-)

---

### Post by cbowman57 on 2011-11-17
Funny, I never considered that the problem was with gnome-tweak-tool, that must have also come from ricotz/testing. :)

Rico warned us not to use them months ago.

---

### Post by bmbaker on 2011-11-18
> **cbowman57 said:**
> Funny, I never considered that the problem was with gnome-tweak-tool, that must have also come from ricotz/testing. :)

Rico warned us not to use them months ago.

well other than a few minor gliches everything so far has been very stable :-)

---

### Post by cbowman57 on 2011-11-18
> **bmbaker said:**
> well other than a few minor gliches everything so far has been very stable :-)

That's good.  I don't have a problem using a ppa, gNatty was dependent on  them, but you just have to be conscious of the fact that when dipping into testing & devel repos things might break.

Which is why I'm a big fan of Clonezilla. :)

---

### Post by bmbaker on 2011-11-18
> **cbowman57 said:**
> That's good.  I don't have a problem using a ppa, gNatty was dependent on  them, but you just have to be conscious of the fact that when dipping into testing & devel repos things might break.

Which is why I'm a big fan of Clonezilla. :)

I've been using remsterys latest build it wks great too :-)

---

### Post by cbowman57 on 2011-11-18
True, Remasterys has it's uses but it's not as quick & reliable as Clonezilla.

I'm a fan of both though.

---

